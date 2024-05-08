
An iterable is an [[Classes and objects#Objects|object]] capable of returning values one at a time.

```mermaid
---
title: Iterables
---
flowchart LR
I(Iterables) --> S(Sequences)
	S --> Strings
	S --> Lists
	S --> Tuples
	S --> Range
	S --> Bytes
I(Iterables) --> C(Collections)
	C --> Dictionary
	C --> Sets

```

