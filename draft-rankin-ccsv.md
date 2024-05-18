---
title: "Common Format and Media Type for Control-Character-Separated Values (CCSV) Files"
abbrev: "CCSV"
category: info

docname: draft-rankin-ccsv-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
# area: AREA
# workgroup: WG Working Group
keyword:
 - next generation
 - unicorn
 - sparkling distributed ledger
venue:
#  group: WG
#  type: Working Group
#  mail: WG@example.com
#  arch: https://example.com/WG
  github: "oldgrognard/ccsv-id"
  latest: "https://oldgrognard.github.io/ccsv-id/draft-rankin-ccsv.html"

author:
 -
    fullname: "Mike Rankin"
    organization: "Individual Contributor"
    email: "mrankin@oldgrognard.pub"

normative:

informative:


--- abstract

This document documents the format used for Control-Character-Separated Values (CCSV) files and registers the associated MIME type "text/ccsv".


--- middle

# Introduction

TODO Introduction


# Conventions and Definitions

{::boilerplate bcp14-tagged}

## Definition of the CCSV format

The ABNF grammar {{!STD68}} appears as follows:

file = [header RS] record *(US record) [RS]
header = name *(US name)
record = field *(US field)
name = field
field = *VCHAR
VCHAR = %x21-7E
RS = %x1E
US = %x1F


# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.