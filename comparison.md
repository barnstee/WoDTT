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
| **@type**               | This must be "Map".                         `                           `              | ...					   | ...																												   |																		|
| **@id**                 |  An identifer for the Map. If no @id is provided, one will be assigned automatically.  | ...					   | ...																												   |																		|
| **comment**             |  A comment for model authors.                                                          | ...					   | ...																												   |																		|
| **description**         |  A localizable description for display.                                                | ...					   | ...																												   |																		|
| **displayName**         |  A localizable name for display.                                                       | ...					   | ...																												   |																		|
| **mapKey**              | A description of the keys in the Map.                                                  | ...					   | ...																												   |																		|
| **mapValue**            | A description of the values in the Map.                                                | ...					   | ...																												   |																		|


### MapKey

| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **@type**               | If provided, must be "MapKey".                                                         | ...					   | ...																												   |																		|
| **@id**                 | An identifer for the MapKey. If no @id is provided, one will be assigned automatically.| ...					   | ...																												   |																		|
| **comment**             | A comment for model authors.                                                           | ...					   | ...																												   |																		|
| **description**         | A localizable description for display.                                                 | ...					   | ...																												   |																		|
| **displayName**         | A localizable name for display.                                                        | ...					   | ...																												   |																		|
| **name**                | The programming name of the element.                                                   | ...					   | ...																												   |																		|
| **schema**              | The data type of the Map's key, which must be string.                                  | ...					   | ...																												   |																		|

### MapValue


| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **@type**               | If provided, must be "MapValue".                                                       | ...					   | ...																												   |																		|
| **@id**                 | An identifer for the MapValue. Assigned automatically if none provided.                | ...					   | ...																												   |																		|
| **comment**             | A comment for model authors.                                                           | ...					   | ...																												   |																		|
| **description**         | A localizable description for display.                                                 | ...					   | ...																												   |																		|
| **displayName**         | A localizable name for display.                                                        | ...					   | ...																												   |																		|
| **name**                | The programming name of the element.                                                   | ...					   | ...																												   |																		|
| **schema**              | The data type of the element, which is an instance of Schema.                          | ...					   | ...																												   |																		|
## Object


| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **@type**               | This must be "Object".                                                                 | ...					   | ...																												   |																		|
| **@id**                 | An identifer for the Object. If no @id is provided, one will be assigned automatically.| ...					   | ...																												   |																		|
| **comment**             | A comment for model authors.                                                           | ...					   | ...																												   |																		|
| **description**         | A localizable description for display.                                                 | ...					   | ...																												   |																		|
| **displayName**         | A localizable name for display.                                                        | ...					   | ...																												   |																		|
| **fields**              |  A set of field descriptions, one for each field in the Object.                        | ...					   | ...																												   |																		|



### Field

A Field describes a field in an Object.

The chart below lists the properties that a Field may have.

| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **@type**               | If provided, must be "Field".                                                          | ...					   | ...																												   |																		|
| **@id**                 | An identifer for the Field. If no @id is provided, one will be assigned automatically. | ...					   | ...																												   |																		|
| **comment**             | A comment for model authors.                                                           | ...					   | ...																												   |																		|
| **description**         | A localizable description for display.                                                 | ...					   | ...																												   |																		|
| **displayName**         | A localizable name for display.                                                        | ...					   | ...																												   |																		|
| **name**                | The programming name of the element.                                                   | ...					   | ...																												   |																		|
| **schema**              | The data type of the element, which is an instance of Schema.                          | ...					   | ...																												   |																		|

## Geospatial Schemas 

DTDL provides a set of geospatial schemas, based on [GeoJSON](https://geojson.org/), for modeling a variety of geographic data structures.

| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments																|
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------| 
| **lineString**          | GeoJSON LineString - dtmi:standard:schema:geospatial:lineString;3                      | ...					   | ...																												   |																		|
| **multiLineString**     | GeoJSON MultiLineString - dtmi:standard:schema:geospatial:multiLineString;3            | ...					   | ...																												   |																		|
| **multiPoint**          | GeoJSON MultiPoint - dtmi:standard:schema:geospatial:multiPoint;3                      | ...					   | ...																												   |																		|
| **multiPolygon**        | GeoJSON MultiPolygon - dtmi:standard:schema:geospatial:multiPolygon;3                  | ...					   | ...																												   |																		|
| **point**               | GeoJSON Point - dtmi:standard:schema:geospatial:point;3                                | ...					   | ...																												   |																		|
| **polygon**             | GeoJSON Polygon - dtmi:standard:schema:geospatial:polygon;3                            | ...					   | ...																												   |																		|




## Interface schemas


| DTDL Term / Concept     | DTDL Description                                                                       | WoT TD Term               | WoT TD Description                                                                                                    | Comments						                                        |
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------| 
| **@type**               | This must be "Array", "Enum", "Map", or "Object".                                      | ...					   | ...																												   |																		|
| **@id**                 | An identifer for the complex schema.                                                   | ...					   | ...																												   |																		|
| **comment**             | A comment for model authors.                                                           | ...					   | ...																												   |																		|
| **description**         | A localizable description for display.                                                 | ...					   | ...																												   |																		|
| **displayName**         | A localizable name for display.                                                        | ...					   | ...																												   |																		|

