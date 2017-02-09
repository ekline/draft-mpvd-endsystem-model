Multiple Provisioning Domain (MPVD) End System Model

# Requirements

1. PvD-aware End Systems MUST be able to identify PvDs, and be able to aggregate PvD information into respective PvDs.

  PvDs may be *implicit*, meaning the End System itself creates PvDs based on criteria known only to itself.
  For example, an implementation might:
    * have a "loopback" PvD for all local communications
    * define a "null" PvD in which no networking configuration information is ever stored
    * define that each interface is its own PvD

  PvDs may be *explicit*, meaning the End System learned from the network of a PvD and information that should be associated with it.
  This mechanism is outside the scope of this document.

2. A PvD-aware End System MUST be able to restrict operations that make any use of network configuration information (IP addresses, routes, ...) to use only the information within a specified PvD.

  Fallback/fallthrough/... can be implemented by the End System by iterating (serially or in parallel) operations over a set of PvDs.

  Examples: RFC 6724 section 4:
  >It is RECOMMENDED that the candidate source addresses be the set of
   unicast addresses assigned to the interface that will be used to send
   to the destination (the "outgoing" interface).

3. A PvD-aware End System SHOULD provide an Application Programming Interface for applications to use.

# Implementation Guidance

How to learn/isolate PvD info
    * Use URPF
    * Baker-Linkova multihoming (learn data on a per next-hop basis)
    * Templin's RIOs in Redirects ??

  Implicit per-interface PvDs means behaving very much like a Strong End System Model.

Implementing support for an API will have several implications...
