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

### Formatting Rules

1. A Record Separator RS (U+001E) is used between each record in the file including the header.
1. A Unit Separator US (U+001F) is used between each field in a record.
1. A CCSV MUST begin with a header.  The header consists of the names of the columns separated with US (U+001F) entities.
1. The header is terminated with the RS (U+001E) entity if the document contains any records.
1. The header and each record MUST contain the same number of US (U+001F) entities i.e., the header and each record MUST have the same number of fields.
1. Each record in the body is delimited with a RS (U+001E) entity.  Note that carriage returns and line feeds are not part of the delimiter and are valid characters in the body of a field.
1. Each field within a record is delimited with the US (U+001F) entity.
1. The US (U+001F) entity and the RS (U+001E) separator MUST NOT appear in the body of a field.


The ABNF grammar {{!STD68}} appears as follows:

~~~~
file = header RS *(record RS) [record]
header = name *( US name )
record = field *( US field )
name = field
field = *VCHAR
VCHAR = %x00-1D / %x20-D7FF / %xE000-10FFFF ; all characters except the designated delimiters and surrogates
RS = %x1E ; record separator
US = %x1F ; unit separator
~~~~

# Encoding Considerations
CCSV files MUST be encoded using UTF-8 {{!RFC3629}}.

Implementations MUST NOT add a byte order mark (U+FEFF) to the beginning of the file or networked-transmitted text.

# Security Considerations

CCSV files alone are considered relatively harmless as there is no additional prescribed processing. However, the file may be parsed and further processed by the recipient. To the extent that a receiving application executes arbitrary system level commands from strings contained in a CCSV file, they may be at risk.

# Interoperability Considerations

Adherance to the Formatting Rules {{formatting-rules}} and the Encoding Considerations {{encoding-considerations}} ensures a high level of interoperability.

# IANA Considerations

This section provides the media-type registration application (as per {{!RFC6838}}).

Type name: text

Subtype name: ccsv

Required parameters: N/A

Optional parameters: N/A

Encoding considerations: See {{encoding-considerations}}

Security considerations: See {{security-considerations}}

Interoperability considerations: See {{interoperability-considerations}}

Published specification: TBD

Applications that use this media type:
  
	Databases, spreadsheets, statistical programs, and data conversion utilities

Fragment identifier considerations: N/A

Additional information:

	Deprecated alias names for this type: N/A
	Magic number(s): N/A
	File extension(s): CCSV
	Macintosh file type code(s): TEXT

Person & email address to contact for further information:

  Mike Rankin
	ICF
	1902 Reston Metro Plaza
	Reston, VA  20190
	USA

	mrankin@icf.com

Intended usage: COMMON

Restrictions on usage: N/A

Author/Change controller: Mike Rankin

Provisional registration?


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
