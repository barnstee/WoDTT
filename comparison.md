# DTDLv3 and W3C WoT Thing Description 1.1 Comparision

This document gives a detailed comparison between [DTDL](https://azure.github.io/opendigitaltwins-dtdl/DTDL/v3/DTDL.v3.html) and [W3C WoT Thing Description/Thing Model](https://www.w3.org/TR/wot-thing-description11/).

Hint: JSON-LD keywords like @id, @context, @type etc. are ignored. 

## Root / Thing Level

| DTDL Term / Concept     | DTDL Description                                                                       | TD Term                   | TD Description                                                                                                        |
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|
| **displayName**         | A localizable name for display.                                                        | **title**                 | Provides a human-readable title (e.g., display a text for UI representation) based on a default language.             | 
|                         |                                                                                        | **titles**                | Provides multi-language human-readable titles (e.g., display a text for UI representation in different languages).    |
| **description**         | A localizable description for display.                                                 | **description**           | (human-readable) information based on a default language.                                                             |
|                         |                                                                                        | **descriptions**          | Can be used to support (human-readable) information in different languages.                                           |
| **comment**             | A comment for model authors.                                                           |                           |                                                                                                                       |
|                         |                                                                                        | **version**               | Provides version information.                                                                                         |
|                         |                                                                                        | **modified**              | Provides information when the TD instance was last modified.                                                          |
|                         |                                                                                        | **support**               | Provides information about the TD maintainer as URI scheme (e.g., mailto [RFC6068], tel [RFC3966], https [RFC9112]).  |
| **content**             | A set of elements that define the contents of this Interface.                          |                           | Comment: Kind of interactions specified directly in properties, actions, and events container.                        |
| **schemas**             | A set of complex schema objects that are reusable within this Interface.               | **schemaDefinitions**     | Set of named data schemas. To be used in a schema name-value pair inside an AdditionalExpectedResponse object.        |
| **extends**             | A set of DTMIs that refer to Interfaces from which this Interface inherits contents... |                           | A Thing Model can extend an existing Thing Model by using the tm:extends mechanism announced in the links definition. |
|                         |                                                                                        | **links**                 | Provides Web links to arbitrary resources that relate to the specified Thing Description.                             |
|                         |                                                                                        | **forms**                 | Set of form hypermedia controls that describe how an operation can be performed.                                      |
|                         |                                                                                        | **security**              | Set of security definition names, chosen from those defined in securityDefinitions.                                   |
|                         |                                                                                        | **securityDefinitions**   | Set of named security configurations (definitions only).                                                              |
|                         |                                                                                        | **profile**               | Indicates the WoT Profile mechanisms followed by this Thing Description and the corresponding Thing implementation.   |
|                         |                                                                                        | **uriVariables**          | Define URI template variables according to [RFC6570] as collection based on DataSchema declarations.                  |
| **"@type": "Property"** | A Property describes the read-only and read/write state of any digital twin.           | **properties**            | All Property-based Interaction Affordances of the Thing.                                                              |
| **"@type": "Command"**  | A Command describes a function or operation that can be performed on any digital twin. | **actions**               | All Action-based Interaction Affordances of the Thing.                                                                |
| **"@type": "Telemetry"**| Telemetry describes the data emitted by any digital twin, whether the data is ...      | **events**                | All Event-based Interaction Affordances of the Thing.                                                                 |


## Property Level


| DTDL Term / Concept     | DTDL Description                                                                       | TD Term                   | TD Description                                                                                                 |
|-------------------------|----------------------------------------------------------------------------------------|---------------------------|----------------------------------------------------------------------------------------------------------------|
| **displayName**         | A localizable name for display.                                                        | **title**                 | Provides a human-readable title (e.g., display a text for UI representation) based on a default language.      | 
| **description**         | A localizable description for display.                                                 | **description**           | (human-readable) information based on a default language.                                                      |
| **comment**             | A comment for model authors.                                                           |                           |                                                                                                                |
| **name**                | The programming name of the element.                                                   |                           | Comment: Programming name is assigned as key name of the property                                              |
| ...               | ...                                                |     ...                      | ...                                          |
