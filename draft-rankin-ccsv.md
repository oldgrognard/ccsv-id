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
    organization: "ICF International, Inc."
    email: "mrankin@oldgrognard.pub"

normative:

informative:


--- abstract

This document documents the format used for Control-Character-Separated Values (CCSV) files and registers the associated MIME type "text/ccsv".


--- middle

# Introduction

A CCSV (Control-Character-Separated Values file) is a file format that enables moving data between spreadsheets, statistical analysis programs, databases, and any other program that works with rectangular data. It is very similar to (CSV) Comma-Separated Values files {{!RFC4180}}, (TSV) Tab-Separated Values files, and their derivatives. Unlike those file types, the CCSV minimizes usage ambiguity by having non-printable characters as delimiters. The two delimiter characters may not appear in the document's text, making the practice of escaping certain characters or adding additional delimiters for certain strings unnecessary. This document seeks to define the format of Control Character Separated Values (CCSV) files and formally register the "text/ccsv" Media Type for CCSV in accordance with {{!RFC6838}}.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

## Definition of the CCSV format

In order for a file to be a CCSV, it MUST adhere to the following formatting rules:

1. A Record Separator (RS - ASCII entity %x1F) is used between each record in the file including the header.
1. A Unit Separator (US - ASCII entity %x1E) is used between each field in a record.
1. A CCSV MUST begin with a header.  The header consists of the names of the columns separated with (US) entities.
1. The header is terminated with the (RS) entity if the document contains any records.
1. The header and each record MUST contain the same number of (US) entities i.e., the header and each record MUST have the same number of fields.
1. Each record in the body is delimited with a (RS) entity.  Note that carriage returns and line feeds are not part of the delimiter and are valid characters in the body of a field.
1. Each field within a record is delimited with the (US) entity.
1. The (US) entity and the (RS) separator MUST NOT appear in the body of a field.


The ABNF grammar {{!STD68}} appears as follows:

~~~
file = header RS *(record RS) [record]
header = name *( US name )
record = field *( US field )
name = field
field = *VCHAR
VCHAR = %x21-7E ; visible characters
RS = %x1E ; record separator
US = %x1F ; unit separator

~~~

# Security Considerations

TODO Security


# IANA Considerations

This section provides the media-type registration application (as per {{!RFC6838}}).

Type name: text

Subtype name: ccsv

Required parameters: n/a

Optional parameters: 
  charset:

Encoding considerations:

Security considerations:

Interoperability considerations:

Published specification:

Applications that use this media type:

Fragment identifier considerations:

Additional information:

  Deprecated alias names for this type:
  Magic number(s):
  File extension(s):
  Macintosh file type code(s):

Person & email address to contact for further information:

Intended usage: COMMON

Restrictions on usage:

Author: Mike Rankin

Change controller:

Provisional registration?


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
