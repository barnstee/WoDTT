# DTDLv3 and W3C WoT Thing Description 1.1 Comparision

This document gives a detailed comparison between [DTDL](https://azure.github.io/opendigitaltwins-dtdl/DTDL/v3/DTDL.v3.html) and [W3C WoT Thing Description/Thing Model](https://www.w3.org/TR/wot-thing-description11/).

Hint: JSON-LD keywords like @id, @context, @type etc. are ignored. 

## Root / Thing Level

| DTDL Term / Concept     | DTDL Description                                                                        | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **displayName**         | A localizable name for display.                                                        | **title**                 | Provides a human-readable title (e.g., display a text for UI representation) based on a default language.             | Derived from JSON schema. Proposal is to use the WoT definition.		|
|                         | Comment: displayName allows JSON-LD language map for multi-language support            | **titles**                | Provides multi-language human-readable titles (e.g., display a text for UI representation in different languages).    | Proposal is to keep WoT definition.									|
| **description**         | A localizable description for display.                                                 | **description**           | (human-readable) information based on a default language.                                                             | Derived from JSON schema. Proposal is to use the WoT definition.		|									
|                         | Comment: description allows JSON-LD language map for multi-language support            | **descriptions**          | Can be used to support (human-readable) information in different languages.                                           | Proposal is to keep WoT definition.									|									
| **comment**             | A comment for model authors.                                                           |                           |                                                                                                                       | Proposal is to keep the DTDL definition.								|	
|                         |                                                                                        | **version**               | Provides version information.                                                                                         | Proposal is to keep WoT definition.									|
|                         |                                                                                        | **created**               | Provides information when the TD instance was created.                                                                | Proposal is to keep WoT definition.									|
|                         |                                                                                        | **modified**              | Provides information when the TD instance was last modified.                                                          | Proposal is to keep WoT definition.									|
|                         |                                                                                        | **support**               | Provides information about the TD maintainer as URI scheme (e.g., mailto [RFC6068], tel [RFC3966], https [RFC9112]).  | Proposal is to keep WoT definition.									|
| **content**             | A set of elements that define the contents of this Interface.                          |                           | Comment: Kind of interactions specified directly in properties, actions, and events container.                        | Proposal is to split this up into 3 separate fields, i.e. WoT "properties", "actions" and "events" (see below). |
| **schemas**             | A set of complex schema objects that are reusable within this Interface.               | **schemaDefinitions**     | Set of named data schemas. To be used in a schema name-value pair inside an AdditionalExpectedResponse object.        | Proposal is to keep WoT definition.									|
| **extends**             | A set of DTMIs that refer to Interfaces from which this Interface inherits contents... | **links**                 | A Thing Model can extend an existing Thing Model by using the tm:extends mechanism announced in the links definition. | WoT uses [RFC8288] web linking for inheritance. Proposal is to use that. |
|                         |                                                                                        |						   | Links provide Web links to arbitrary resources that relate to the specified Thing Description.                        |																		|
|                         |                                                                                        | **forms**                 | Set of form hypermedia controls that describe how an operation can be performed.                                      | Used for WoT protocol bindings. Proposal is to use the WoT definition. |
|                         |                                                                                        | **security**              | Set of security definition names, chosen from those defined in securityDefinitions.                                   | Proposal is to use the WoT definition.									|
|                         |                                                                                        | **securityDefinitions**   | Set of named security configurations (definitions only).                                                              | Proposal is to use the WoT definition.									|
|                         |                                                                                        | **profile**               | Indicates mandatory fields defined in the profile. New in version 1.1. Not used yet.								   | Proposal is to use the WoT definition.									|
|                         |                                                                                        | **uriVariables**          | Define URI template variables according to [RFC6570] as collection based on DataSchema declarations.                  | Proposal is to use the WoT definition.									|
| **"@type": "Property"** | A Property describes the read-only and read/write state of any digital twin.           | **properties**            | All Property-based Interaction Affordances of the Thing.                                                              | Proposal is to use the WoT definition.									|
| **"@type": "Command"**  | A Command describes a function or operation that can be performed on any digital twin. | **actions**               | All Action-based Interaction Affordances of the Thing.                                                                | Proposal is to use the WoT definition.									|
| **"@type": "Telemetry"**| Telemetry describes the data emitted by any digital twin, whether the data is ...      | **events**                | All Event-based Interaction Affordances of the Thing.                                                                 | Proposal is to use the WoT definition.									|

## Property Level

| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description																									   | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------| 
| **displayName**         | A localizable name for display.                                                        | **title**                 | Provides a human-readable title (e.g., display a text for UI representation) based on a default language.			   | Derived from JSON schema. Proposal is to use the WoT definition.		|
| **description**         | A localizable description for display.                                                 | **description**           | (human-readable) information based on a default language.															   | Derived from JSON schema. Proposal is to use the WoT definition.		|
| **comment**             | A comment for model authors.                                                           |                           |																													   | Proposal is to keep the DTDL definition.								|
| **name**                | The programming name of the element.                                                   |                           | Comment: Programming name is assigned as key name of the property												       | Proposal is to keep the DTDL definition but convert to JSON-LD 1.1.	|
| **schema**              | The data type of the Property, which is an instance of Schema.                         | **type**                  | Assignment of JSON-based data types compatible with JSON Schema													   | Proposal is to keep WoT definition.		  							|
| **writable**            | A boolean value that indicates whether the Property is writable or not.                | **writeOnly**             | Boolean value that is a hint to indicate whether a property interaction / value is write only (=true) or not (=false).| Proposal is to use the WoT definition.									|
|                         |                                                                                        | **readOnly**              | Boolean value that is a hint to indicate whether a property interaction / value is read only (=true) or not (=false). | Proposal is to use the WoT definition.									|
|                         |                                                                                        | **observable**            | Boolean value that is a hint to indicate whether a property interaction / value is observable (=true) or not (=false).| Proposal is to use the WoT definition.									|
|                         |                                                                                        | **forms**                 | Set of form hypermedia controls that describe how an operation can be performed (used for protocol bindings).		   | Proposal is to use the WoT definition.									|
|                         |                                                                                        | **uriVariables**          | Define URI template variables according to [RFC6570] as collection based on DataSchema declarations.				   | Proposal is to use the WoT definition.									|
|                         |                                                                                        | **{DataSchema}**          | Comment: At property level there can be the terms from data schema													   | Proposal is to use the WoT definition.									|

## Commands Level

| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **@type**               |If provided, must be "Command"                                                          | ...					   | ...																												   |																		|
| **@id**                 |Identifier for the commnand.  Assigned automatically if not provided.                   | ...					   | ...																						                    	   |																		|
| **comment**             |A comment for model authors                                                             | ...					   | ...																												   |																		|
| **description**         |Comment for model authors                                                               | ...					   | ...																												   |																		|
| **displayName**         |A localizable name for display.                                                         | ...					   | ...																												   |																		|
| **name**                |The programming name of the element.                                                    | ...					   | ...																												   |																		|
| **request**             |A description of the input to the Command.                                              | ...					   | ...																												   |																		|
| **response**            |	A description of the output of the Command.                                            | ...					   | ...																												   |																		|

## Relationship Level 

| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **"@type": "Command"**  |If provided, must be "Relationship"                                                     | ...					   | ...																												   |																		|
| **@id**                 |Identifier for the Relationship.  Assigned automatically if not provided.               | ...					   | ...																						                    	   |																		|
| **comment**             |A comment for model authors                                                             | ...					   | ...																												   |																		|
| **description**         |Comment for model authors                                                               | ...					   | ...																												   |																		|
| **displayName**         |A localizable name for display.                                                         | ...					   | ...																												   |																		|
| **maxMultiplicity**     |The max multiplicity for the realtionship target; defaults to the max allowable value   | ...					   | ...																												   |																		|
| **minMultiplicity**     |The min multiplicity for the realtionship target; defaults to the max allowable value   | ...					   | ...																												   |																		|
| **name**                |The programming name of the element.                                                    | ...					   | ...																												   |																		|
| **properties**          |A set of Properties that define Relationship-specific state.                            | ...					   | ...																												   |																		|
| **target**              |An Interface identifier. If no target is specified, each instance target is permitted to be any Interface. | ...					   | ...																												   |																		|
| **writable**            |	A boolean value that indicates whether the Relationship is writable or not.            | ...					   | ...																												   |																		|


## Component Level

| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **@type**               | This must be "Component".                                                              | ...					   | ...																												   |																		|
| **@id**                 | An identifer for the Component. If no @id is provided, assigned automatically.         | ...					   | ...																												   |																		|
| **comment**             | A comment for model authors.                                                           | ...					   | ...																												   |																		|
| **description**         | A localizable description for display.                                                 | ...					   | ...																												   |																		|
| **displayName**         | A localizable name for display.                                                        | ...					   | ...																												   |																		|
| **name**                | The programming name of the element.                                                   | ...					   | ...																												   |																		|
| **schema**              | The data type of the Component, which is an instance of Interface.                     | ...					   | ...																												   |																		|


## Primitive schema


| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **boolean**             | a boolean value                                                                        | ...					   | ...																												   |																		|
| **date**                | a date in ISO 8601 format, per [RFC 3339](https://tools.ietf.org/html/rfc3339)         | ...					   | ...																												   |																		|
| **dateTime**            | a date and time in ISO 8601 format per [RFC 3339](https://tools.ietf.org/html/rfc3339) | ...					   | ...																												   |																		|
| **double**              | a finite numeric value that is expressible in IEEE 754 double-precision floating point format, conformant with xsd:double | ...					   | ...																												   |																		|
| **duration**            | a duration in ISO 8601 format                                                          | ...					   | ...																												   |																		|
| **float**               | a finite numeric value that is expressible in IEEE 754 single-precision floating point format, conformant with xsd:float | ...					   | ...																												   |																		|
| **integer**             | a signed integral numeric value that is expressible in 4 bytes                         | ...					   | ...																												   |																		|
| **long**                | a signed integral numeric value that is expressible in 8 bytes                         | ...					   | ...																												   |																		|
| **string**              | a UTF8 string                                                                          | ...					   | ...																												   |																		|
| **time**                | a time in ISO 8601 format, per [RFC 3339](https://tools.ietf.org/html/rfc3339)         | ...					   | ...																												   |																		|

## Array

An Array describes an indexable data type where each element is of the same schema.
The schema for an Array's element can itself be a primitive or complex schema.

The chart below lists the properties that an Array may have.

| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **@type**               | This must be "Array".                                                                  | ...					   | ...																												   |																		|
| **@id**                 | An identifer for the Array. If no @id is provided, one will be assigned automatically. | ...					   | ...																												   |																		|
| **comment**             | A comment for model authors.                                                           | ...					   | ...																												   |																		|
| **description**         | A localizable description for display.                                                 | ...					   | ...																												   |																		|
| **displayName**         | A localizable name for display.                                                        | ...					   | ...																												   |																		|
| **elementSchema**       | The data type of each element in the Array, which is an instance of Schema.            | ...					   | ...																												   |																		|


## Enum

| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **@type**               |This must be "Enum".                                                                    | ...					   | ...																												   |																		|
| **@id**                 |An identifer for the Enum. If no @id is provided, one will be assigned automatically.   | ...					   | ...																												   |																		|
| **comment**             |A comment for model authors.                                                            | ...					   | ...																												   |																		|
| **description**         | A localizable description for display.                                                 | ...					   | ...																												   |																		|
| **displayName**         | A localizable name for display.                                                        | ...					   | ...																												   |																		|
| **enumValues**          | A set of name/value mappings for the Enum.                                             | ...					   | ...																												   |																		|
| **valueSchema**         | The data type for the enumValues; all values must be of the same type.                 | ...					   | ...																												   |																		|



### EnumValue

| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **@type**               | If provided, must be "EnumValue".                                                      | ...					   | ...																												   |																		|
| **@id**                 | An identifer for the EnumValue. Assigned automatically if not provided                 | ...					   | ...																												   |																		|
| **comment**             | A comment for model authors.                                                           | ...					   | ...																												   |																		|
| **description**         | A localizable description for display.                                                 | ...					   | ...																												   |																		|
| **displayName**         | A localizable name for display.                                                        | ...					   | ...																												   |																		|
| **enumValue**           | The on-the-wire value that maps to the EnumValue, which may be either an integer or a string. | ...					   | ...																												   |																		|
| **name**                | The programming name of the element.                                                   | ...					   | ...																												   |																		|

## Map



| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **@type** | required | [IRI](#internationalized-resource-identifier) |  | This must be "Map". |
| **@id** | optional | [DTMI](#digital-twin-model-identifier) | max 2048 characters | An identifer for the Map. If no @id is provided, one will be assigned automatically. |
| **comment** | optional | *string* | max 512 characters | A comment for model authors. |
| **description** | optional | localizable *string* | max 512 characters | A localizable description for display. |
| **displayName** | optional | localizable *string* | max 512 characters | A localizable name for display. |
| **mapKey** | required | [MapKey](#mapkey) |  | A description of the keys in the Map. |
| **mapValue** | required | [MapValue](#mapvalue) |  | A description of the values in the Map. |


### MapKey

| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| --- | --- | --- | --- | --- |
| **@type** | optional | [IRI](#internationalized-resource-identifier) |  | If provided, must be "MapKey". |
| **@id** | optional | [DTMI](#digital-twin-model-identifier) | max 2048 characters | An identifer for the MapKey. If no @id is provided, one will be assigned automatically. |
| **comment** | optional | *string* | max 512 characters | A comment for model authors. |
| **description** | optional | localizable *string* | max 512 characters | A localizable description for display. |
| **displayName** | optional | localizable *string* | max 512 characters | A localizable name for display. |
| **name** | required | *string* | max 512 characters; contains only alphanumerics and underscore, starting with a letter, ending with alphanumeric | The programming name of the element. |
| **schema** | required | [String](#string) | must be *string* | The data type of the Map's key, which must be string. |

### MapValue


| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| --- | --- | --- | --- | --- |
| **@type** | optional | [IRI](#internationalized-resource-identifier) |  | If provided, must be "MapValue". |
| **@id** | optional | [DTMI](#digital-twin-model-identifier) | max 2048 characters | An identifer for the MapValue. If no @id is provided, one will be assigned automatically. |
| **comment** | optional | *string* | max 512 characters | A comment for model authors. |
| **description** | optional | localizable *string* | max 512 characters | A localizable description for display. |
| **displayName** | optional | localizable *string* | max 512 characters | A localizable name for display. |
| **name** | required | *string* | max 512 characters; contains only alphanumerics and underscore, starting with a letter, ending with alphanumeric | The programming name of the element. |
| **schema** | required | [Schema](#schema) | max depth of 5 levels when MapValue is the value of Map **mapValue** | The data type of the element, which is an instance of Schema. |

## Object


| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| --- | --- | --- | --- | --- |
| **@type** | required | [IRI](#internationalized-resource-identifier) |  | This must be "Object". |
| **@id** | optional | [DTMI](#digital-twin-model-identifier) | max 2048 characters | An identifer for the Object. If no @id is provided, one will be assigned automatically. |
| **comment** | optional | *string* | max 512 characters | A comment for model authors. |
| **description** | optional | localizable *string* | max 512 characters | A localizable description for display. |
| **displayName** | optional | localizable *string* | max 512 characters | A localizable name for display. |
| **fields** | optional | set of [Fields](#field) |  | A set of field descriptions, one for each field in the Object. |



### Field

A Field describes a field in an Object.

The chart below lists the properties that a Field may have.

| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| --- | --- | --- | --- | --- |
| **@type** | optional | [IRI](#internationalized-resource-identifier) |  | If provided, must be "Field". |
| **@id** | optional | [DTMI](#digital-twin-model-identifier) | max 2048 characters | An identifer for the Field. If no @id is provided, one will be assigned automatically. |
| **comment** | optional | *string* | max 512 characters | A comment for model authors. |
| **description** | optional | localizable *string* | max 512 characters | A localizable description for display. |
| **displayName** | optional | localizable *string* | max 512 characters | A localizable name for display. |
| **name** | required | *string* | max 512 characters; contains only alphanumerics and underscore, starting with a letter, ending with alphanumeric; must be unique for all fields in Object | The programming name of the element. |
| **schema** | required | [Schema](#schema) | max depth of 5 levels when Field is the value of Object **fields** | The data type of the element, which is an instance of Schema. |

## Geospatial Schemas

DTDL provides a set of geospatial schemas, based on [GeoJSON](https://geojson.org/), for modeling a variety of geographic data structures.

| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|| --- | --- | --- |
| **lineString** | GeoJSON LineString | dtmi:standard:schema:geospatial:lineString;3 |
| **multiLineString** | GeoJSON MultiLineString | dtmi:standard:schema:geospatial:multiLineString;3 |
| **multiPoint** | GeoJSON MultiPoint | dtmi:standard:schema:geospatial:multiPoint;3 |
| **multiPolygon** | GeoJSON MultiPolygon | dtmi:standard:schema:geospatial:multiPolygon;3 |
| **point** | GeoJSON Point | dtmi:standard:schema:geospatial:point;3 |
| **polygon** | GeoJSON Polygon | dtmi:standard:schema:geospatial:polygon;3 |

### Geospatial schema examples

This example shows modeling the location of a device as Telemetry using the geospatial schema **point**.

******json
{
  "@type": "Telemetry",
  "name": "location",
  "schema": "point"
}
******

A Telemetry message sent by a particular device reporting its location would have the following structure in JSON (and equivalent structure in other serializations).

******json
{
  "location": {
    "type": "Point",
    "coordinates": [ 47.643742, -122.128014 ]
  }
}
******

## Interface schemas

Within an Interface definition, complex schemas may be defined for reusability across Telemetry, Properties, and Commands.
This is designed to promote readability and improved maintenance because schemas that are reused can be defined once (per Interface).
Interface schemas are defined in the **schemas** property of an Interface.

Note that an inheriting Interface cannot reuse schemas defined in the Interface it **extends**, nor can an Interface in a Component reuse schemas defined in the Interface that holds the Component.

The chart below lists the properties that Interface schemas may have.

| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|| --- | --- | --- | --- | --- |
| **@type** | required | [IRI](#internationalized-resource-identifier) |  | This must be "Array", "Enum", "Map", or "Object". |
| **@id** | required | [DTMI](#digital-twin-model-identifier) | max 2048 characters | An identifer for the complex schema. |
| **comment** | optional | *string* | max 512 characters | A comment for model authors. |
| **description** | optional | localizable *string* | max 512 characters | A localizable description for display. |
| **displayName** | optional | localizable *string* | max 512 characters | A localizable name for display. |

### Interface schema examples

******json
{
  "@context": "dtmi:dtdl:context;3",
  "@id": "dtmi:com:example:ReusableTypeExample;1",
  "@type": "Interface",
  "contents": [
    {
      "@type": "Telemetry",
      "name": "accelerometer1",
      "schema": "dtmi:com:example:acceleration;1"
    },
    {
      "@type": "Telemetry",
      "name": "accelerometer2",
      "schema": "dtmi:com:example:acceleration;1"
    }
  ],
  "schemas": [
    {
      "@id": "dtmi:com:example:acceleration;1",
      "@type": "Object",
      "fields": [
        {
          "name": "x",
          "schema": "double"
        },
        {
          "name": "y",
          "schema": "double"
        },
        {
          "name": "z",
          "schema": "double"
        }
      ]
    }
  ]
}
******

## Model Versioning

In DTDL, Interfaces are versioned by an optional one- or two-part version number in the last segment of their identifier.
The first part of a two-part version is the major version number, and the second part is the minor version number.
The use of the version number is up to the model author; however, it is recommended that when only the minor version is increased, the changes to the model are strictly additive.

In some cases, when the model author is working closely with the code that implements and/or consumes the model, any number of changes from version to version may be acceptable.
In other cases, when the model author is publishing an Interface to be implemented by multiple devices or digital twins or consumed by multiple consumers, compatible changes may be appropriate.

## Additional concerns

### Conformance with JSON and JSON-LD

Unless stated otherwise in this document, the Digital Twins Definition Language conforms with the JSON and JSON-LD 1.1 specifications.
This conformance includes things such as keywords, case sensitivity, terminology, etc.
In particular, the JSON-LD spec states that all keys, keywords, and values in JSON-LD are case-sensitive.

### Digital Twin Model Identifier

All elements in digital twin models must have an identifier that is a **digital twin model identifier (DTMI)**.
This includes Interfaces, Properties, Telemetries, Commands, Relationships, Components, complex schema objects, etc.
This does not require that every model element have an explicit identifier, but any identifier assigned to a model element by a digital twin processor must follow this identifier format.

A DTMI has three components: scheme, path, and version.
Scheme and path are separated by a colon (*:*), while path and version are separated by a semicolon (*;*).
The format looks like this: **<scheme> : <path> ; <version>**.

The scheme is the string literal "dtmi" in lowercase.
The path is a sequence of one or more segments, separated by colons.
The version is a numeric value.

Each path segment is a non-empty string containing only letters, digits, and underscores.
The first character may not be a digit, and the last character may not be an underscore.
Segments are thus representable as identifiers in all common programming languages.

Segments are partitioned into user segments and system segments.
If a segment begins with an underscore, it is a system segment; if it begins with a letter, it is a user segment.
If a DTMI contains at least one system segment, it is a system DTMI; otherwise, it is a user DTMI.
System DTMIs are not permitted in DTDL model documents; only user DTMIs are permitted.

The version (and the preceding semicolon) may be omitted entirely.
If present, the version is either a one-part (integer) value or a two-part (major.minor) value.
The length of a one-part version or the major part of a two-part version is limited to nine digits, because the number 999,999,999 fits in a 32-bit signed integer value.
The length of the minor part of a two-part version is limited to six digits, because the number 999,999,999.999,999 fits in a double-precision floating-point value.
The first digit of a version or any part thereof may not be zero, so there is no ambiguity regarding whether version 1 matches version 01 since the latter is invalid.
The minor part of a two-part version may not be zero, so there is no ambiguity regarding whether version 1 matches version 1.0 since the latter is invalid.

Here is an example of a valid DTMI: **dtmi:foo_bar:_16:baz33:qux;12**.

The path contains four segments: *foo_bar*, *_16*, *baz33*, and *qux*.
One of the segments (*_16*) is a system segment, and therefore the identifier is a system DTMI.
The version is 12.

Equivalence of DTMIs is case-sensitive.

The maximum length of a DTMI is 4096 characters.
The maximum length of a user DTMI is 2048 characters.
The maximum length of a DTMI for an Interface is 128 characters.

Developers are encouraged to take reasonable precautions against identifier collisions.
At a minimum, this means not using DTMIs with very short lengths or only common terms, such as **dtmi:myDevice;1**.

Such identifiers are perfectly acceptable in sample documents but should never be used in definitions that are deployed in any fashion.

For any definition that is the property of an organization with a registered domain name, a suggested approach to generating identifiers is to use the reversed order of domain segments as initial path segments, followed by further segments that are expected to be collectively unique among definitions within the domain.
For example, **dtmi:com:fabrikam:industrialProducts:airQualitySensor;1**.

It is also suggested that any identifers within an Interface (e.g. identifers for reusable schemas) should use a prefix from the identifier of the Interface.
For example, an identifier for an Array of double values defined within **dtmi:com:fabrikam:industrialProducts:airQualitySensor;1** might be **dtmi:com:fabrikam:industrialProducts:airQualitySensor:doubleArray;1**.

This practice will not eliminate the possibility of collisions, but it will limit accidental collisions to developers who are organizationally proximate.
It will also simplify the process of identifying malicious definitions when there is a clear mismatch between the identifier and the account that uploaded the definition.

Identifiers with the following prefixes are reserved by the DTDL language:

* **dtmi:dtdl:**
* **dtmi:standard:**

For a full definition of DTMI, please see the [DTMI spec](../../DTMI/README.md).

### Automatic Identifier Assignment

Every element in a DTDL model is identified by a DTMI.
If a DTMI is not indicated directly in the model via an "@id" property, an identifier is assigned automatically.
For reference in the subseqent description, consider the following model:

******json
{
  "@context": "dtmi:dtdl:context;3",
  "@id": "dtmi:com:example:anInterface;1",
  "@type": "Interface",
  "contents": [
    {
      "@id": "dtmi:com:example:aTelemetry;1",
      "@type": "Telemetry",
      "name": "currentDistance",
      "schema": {
        "@id": "dtmi:com:example:doubleArray;1",
        "@type": "Array",
        "elementSchema": "double"
      }
    }
  ]
}
******

The algorithm for determining ID values is as follows:

* If a model element has an "@id" property, this value is the ID of the element. For example, the ID of the Telemetry is "dtmi:com:example:aTelemetry;1", and the ID of the Array is "dtmi:com:example:doubleArray;1".
* If a model element does not have an "@id" property, its ID is generated from (a) its parent's ID, (b) the property connecting it to its parent, and optionally (c) its name.
* For properties that are singular, the algorithm takes the parent's DTMI and adds one segment before the version number (or at the end if there is no version) which is the name of the property preceded by an underscore. So, if the Array above did not have the "@id" property, its ID would be "dtmi:com:example:aTelemetry:_schema;1".
* For properties that are plural, the algorithm takes the parent's DTMI and adds two segments before the version number (or at the end if there is no version). The first added segment is the name of the property preceded by an underscore; the second added segment is the value of the "name" property preceded by two underscores. So, if the Telemetry above did not have the "@id" property, its ID would be "dtmi:com:example:anInterface:_contents:__currentDistance;1".
* These rules apply recursively, so if neither the Telemetry nor the Array had an "@id" property, the ID of the Array would be "dtmi:com:example:anInterface:_contents:__currentDistance:_schema;1"

### Internationalized Resource Identifier

DTDL uses Internationalized Resource Identifiers (IRIs) to refer to DTDL language elements (such as type names) as well as model-defined elements (such as schemas).
IRIs in DTDL are [JSON-LD IRIs](https://w3c.github.io/json-ld-syntax/#iris) and may be relative or absolute.

### Display string localization

Some string properties in models are meant for display and, therefore, support localization.
Digital twin models use JSON-LD's string internationalization support for localization.
Each localizable property (e.g. **displayName** and **description**) is defined to be a JSON-LD language map (**"@container": "@language"**).
The keys of the language map must be language tag strings (see [BCP 47](https://tools.ietf.org/html/bcp47)).
[ISO 639](https://www.loc.gov/standards/iso639-2/php/code_list.php) provides a list of language tags.
The default language for DTDL documents is English.

#### Localization examples

In the following example, no language code is used for the localizable **displayName** property, so the default language English is used.

******json
{
  "@context": "dtmi:dtdl:context;3",
  "@id": "dtmi:com:example:Thermostat;1",
  "@type": "Interface",
  "displayName": "Thermostat"
}
******

In the following example, the localizable **displayName** property is localized into multiple languages.

******json
{
  "@context": "dtmi:dtdl:context;3",
  "@id": "dtmi:com:example:Thermostat;1",
  "@type": "Interface",
  "displayName": {
    "en": "Thermostat",
    "it": "Termostato"
  }
}
******

### Context

When writing a digital twin definition, it is necessary to specify the version of DTDL being used.
Because DTDL is based on JSON-LD, you use the JSON-LD context (the **@context** statement) to specify the version of DTDL being used.

For this version of DTDL, the context is exactly *dtmi:dtdl:context;3*.

Additional context specifiers may also be included, in particular to import definitions for [language extensions](#language-extensions) into the model.
However, the DTDL context must always be first in the ordered list of context specifiers, with any other contexts listed subsequently.

## Language extensions

DTDL also supports a selection of [language extensions](./DTDL.Extensions.md), which offer additional functionality beyond what is provided by the core DTDL language.
The chart below lists the language extensions that are currently available for use with DTDL version 3.

| Extension | Category | Description |
| --- | --- | --- |
| [QuantitativeTypes v1](./DTDL.quantitativeTypes.v1.md) | feature | A set of standard semantic types, unit types, and units. |
| [Historization v1](./DTDL.historization.v1.md) | feature | Record the historical sequence of values of a Property or Telemetry and the times at which values change. |
| [Annotation v1](./DTDL.annotation.v1.md) | feature | Add custom metadata to a Property or a Telemetry. |
| [Overriding v1](./DTDL.overriding.v1.md) | feature | Override a model property with an instance value. |