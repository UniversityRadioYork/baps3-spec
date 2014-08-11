# Inter-Service Communications

Unless BAPS3 is implemented as a single monolithic entity, its services need to
communicate with each other to fulfil the tasks of a playout suite.  We specify
two interfaces for inter-service communication:

* The _internal API_, which is a lightweight, line-orientated textual API used
  for communication between server-side services;
* The _external API_, which is a HTTP-based JSON API used for communication
  specifically between the platform and client services.

## The BAPS2 API

We consciously chose not to use the existing BAPS2 API, for the following
reasons:

* The BAPS2 API is based on a binary protocol that is difficult to debug, and
  provides a lack of transparency that outweighs the performance advantages of
  using the binary protocol;
* The HTTP-based external API allows Web-based implementations of the client
  service, amongst other flexibility benefits;
* The change from BAPS2 to BAPS3 allowed us to correct some oddities and
  counter-intuitive design decisions in the BAPS2 API.

## Chapter Structure

We define both APIs in turn, starting with the internal API and following with
the external API.  For each API, the protocols underlying the API are first
described, followed by a detailed reference of
the requests and responses used in that API.

For the internal API, requests and responses are grouped by _feature flags_,
which are used by the API to describe the feature set of an internal API server.