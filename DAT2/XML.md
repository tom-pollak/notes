# XML
> Extensible Markup Language
> - Markup: encoding information between tags

- When working between two different applications, we use XML as a communicator
	- e.g. client server applications

- [[Semi-structured data]]

## Uses

- Store and arrange data
- Describe data
- Maintain a text based [[Relational Databases | DB]]
- Transport data from one application to another
- Simplify creation of HTML for large websitess

## Attributes

- Specifies a single property of an element
	- \<car make = "bmw">
	
## References

| Disallowed char | Replacement |
| --------------- | ----------- |
| >               | \&gt;        |
| <               | \&lt;        |
| &               | \&amp;       |
| '               | \&apos;      |
| "               | \&quot;            |

## Document Type Definition

> Defines structure of XML document
>  \<!ELEMENT element-name (Content-Model)>


\<!ELEMENT student (id,name,age)>
\<!ELEMENT id (#PCDATA)>

**PCDATA:** an element may only contain Parsed Character Data
- Must not contain any child elements

### Types

#### Internal

> DTD resides within the XML elements, and must be wrapped in \<!DOCTYPE> definition

\<!DOCTYPE root Element [DTD rules]>
XML Elements

#### External
> DTD rules written in separate document with .DTD extension

Two types:
- Private
- Public