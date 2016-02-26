---
NEP: 2
Author: Kyle Fuller
Status: Draft
Created: 2015-12-19
Last Modified: 2015-12-19
---

# NEP 2: Streamable Bodies

## Table of Contents

- [Abstract](#abstract)
- [Motivation](#motivation)
- [Rationale](#rationale)
- [Backwards Compatibility](#backwards-compatibility)
- [Reference Implementation](#reference-implementation)

## Abstract

This NEP details a new mechanism for request and response bodies to be
streamable bytes instead of Strings.

## Motivation

In the current version of Nest, request and response bodies are String types.
String's in Swift are constructed of Unicode grapheme clusters which doesn't
allow Nest applications to receive and send non Unicode HTTP bodies. Nest
applications cannot send or receive raw binary payloads which ultimately means
Nest applications can't deal with any content other than Unicode strings.

The Nest application callback currently expects the whole body to be read
from the client upfront, along with the whole response body to be inside the
response type. These may have both memory and performance concerns.

Applications will achieve the best throughput by buffering request and
response bodies. This avoids loading the whole body into memory at once.

## Rationale

This NEP proposes adding a `PayloadType` protocol which contains a
mutating method called `next` which returns an optional `UInt8`.

```swift
/// Represents a HTTP request or response body<F24><F25>
protocol PayloadType {
  /// Returns the next byte in the payload
  mutating func next() -> UInt8?
}
```

This type SHOULD be returned from the `ResponseType`s `body` property.
A Nest application may continuously call `next` on the body type until it
returns `nil` which represents the end of the body.

```swift
public protocol RequestType {
  var method: String { get }
  var path: String { get }
  var headers: [Header] { get }
  var body: PayloadType { get }
}
```

Similarly, the response body would also become a `PayloadType`.
Nest applications MAY return a body on a response. A Nest server will
continuously call `next` on the body streaming the body to the client until
`nil` is returned from `next` which represents the end of the body.

```swift
public protocol ResponseType {
  var statusLine: String { get }
  var headers: [Header] { get }
  var body: PayloadType? { get }
}
```

Tooling and libraries around Nest (such as Inquiline) may include
convenience mechanisms to allow Nest applications to easily use Strings
bodies while retaining the ability to stream raw bytes.

## Backwards Compatibility

These proposed changes are not backwards compatibility, however since Nest is
in it's early stages and hasn't reached 1.0 I don't believe this is a problem.

## Reference Implementation

Pull request [Nest#17](https://github.com/nestproject/Nest/pull/17),
[Inquiline#4](https://github.com/nestproject/Inquiline/pull/4) implements
the suggested changes in this NEP.
