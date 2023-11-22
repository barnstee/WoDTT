# DTDLv3 and W3C WoT Thing Description 1.1 Comparision

This document gives a detailed comparison between [DTDL](https://azure.github.io/opendigitaltwins-dtdl/DTDL/v3/DTDL.v3.html) and [W3C WoT Thing Description/Thing Model](https://www.w3.org/TR/wot-thing-description11/).

Hint: JSON-LD keywords like @id, @context, @type etc. are ignored.

## Example Of Conversion

### _Digital Twin Description Language v3_

```json
{
  "@context": "dtmi:dtdl:context;3",
  "@id": "dtmi:thing:model:test;1",
  "@type": "Interface",
  "displayName": {
    "en": "Thing Model Test",
    "it": "Modello di Test",
    "fr": "Modèle de test",
    "de": "Testmodel"
  },
  "description": {
    "en": "Thing Model used for testing",
    "it": "Modello utilizzato a fini di test",
    "fr": "Modèle utilisé à des fins d'essai'",
    "de": "Zu Testzwecken verwendetes Modell"
  },
  "comment": "http://localhost:3000",
  "contents": [
    {
      "@type": "Property",
      "writable": false,
      "schema": {
        "fields": [
          {
            "@type": "Field",
            "name": "status"
          }
        ],
        "@type": "Object",
        "displayName": "availablePower"
      },
      "name": "power",
      "displayName": "availablePower",
      "description": "Property obtained from 'Thing Model Test' Thing Model",
      "comment": "1 form: 1 - href: power"
    },
    {
      "@type": "Property",
      "writable": false,
      "schema": "string",
      "name": "content",
      "displayName": {
        "en": "availableContent",
        "it": "contenutoDisponibile",
        "fr": "contenuDisponible",
        "de": "verfügbarerInhalt"
      },
      "description": "Content of the Test Model",
      "comment": "1 form: 1 - href: content"
    },
    {
      "@type": "Property",
      "writable": false,
      "schema": "integer",
      "name": "temperature",
      "displayName": "availableTemperature",
      "description": "Property obtained from 'Thing Model Test' Thing Model",
      "comment": "1 form: 1 - href: temp"
    },
    {
      "@type": "Property",
      "writable": false,
      "schema": {
        "valueSchema": "string",
        "enumValues": [
          {
            "@type": "EnumValue",
            "displayName": "readyToCharge",
            "name": "readyToCharge",
            "enumValue": "readyToCharge"
          },
          {
            "@type": "EnumValue",
            "displayName": "charging",
            "name": "charging",
            "enumValue": "charging"
          },
          {
            "@type": "EnumValue",
            "displayName": "stopCharging",
            "name": "stopCharging",
            "enumValue": "stopCharging"
          }
        ],
        "@type": "Enum",
        "description": "Current car status (readyToCharge, charging, stopCharging)"
      },
      "name": "status",
      "displayName": "status",
      "description": "Current car status (readyToCharge, charging, stopCharging)",
      "comment": "1 form: 1 - href: /ecar/properties/status"
    },
    {
      "@type": "Property",
      "writable": false,
      "schema": {
        "elementSchema": "double",
        "@type": "Array",
        "displayName": "RGB color value"
      },
      "name": "rgb",
      "displayName": "RGB color value",
      "description": "Property obtained from 'Thing Model Test' Thing Model"
    },
    {
      "@type": "Command",
      "name": "toggle",
      "displayName": "togglePowerStatus",
      "description": "Command obtained from 'Thing Model Test' Thing Model",
      "comment": "1 form: 1 - href: toggle"
    },
    {
      "@type": "Command",
      "name": "setVolume",
      "displayName": "setVolume",
      "description": "Command obtained from 'Thing Model Test' Thing Model",
      "comment": "1 form: 1 - href: setvolume"
    },
    {
      "@type": "Command",
      "Request": {
        "@type": "CommandRequest",
        "name": "rebootRequest",
        "displayName": "Reboot Time",
        "description": "Requested time to reboot the device.",
        "schema": "dateTime"
      },
      "Response": {
        "@type": "CommandResponse",
        "name": "rebootResponse",
        "displayName": "Scheduled Time",
        "description": "Scheduled shutdown time",
        "schema": "dateTime"
      },
      "name": "reboot",
      "displayName": "SystemReboot",
      "description": "Reboots the system at the specified time"
    },
    {
      "@type": "Command",
      "Request": {
        "@type": "CommandRequest",
        "name": "playVideoRequest",
        "displayName": "playVideo Request",
        "description": "playVideo action request",
        "schema": {
          "fields": [
            {
              "@type": "Field",
              "displayName": "VideoIdentifier",
              "name": "identifier",
              "description": "The unique identifier of a Video",
              "schema": "string"
            },
            {
              "@type": "Field",
              "displayName": "VideoName",
              "name": "name",
              "description": "The name of a Video file",
              "schema": "string"
            },
            {
              "@type": "Field",
              "displayName": "Timestamp",
              "name": "timestamp",
              "description": "Request Timestamp",
              "schema": "dateTime"
            },
            {
              "@type": "Field",
              "displayName": "VideoUrl",
              "name": "url",
              "description": "The Video Url",
              "schema": "string"
            }
          ],
          "@type": "Object",
          "displayName": "playVideoRequest",
          "description": "playVideo action request"
        }
      },
      "Response": {
        "@type": "CommandResponse",
        "name": "playVideoResponse",
        "displayName": "playVideo Response",
        "schema": {
          "fields": [
            {
              "@type": "Field",
              "name": "stream",
              "schema": "string"
            },
            {
              "@type": "Field",
              "name": "timestamp",
              "schema": "dateTime"
            }
          ],
          "@type": "Object"
        }
      },
      "name": "playVideo",
      "displayName": "playVideo",
      "description": "Command obtained from 'Thing Model Test' Thing Model",
      "comment": "1 form: 1 - href: playvideo"
    },
    {
      "type": "Telemetry",
      "name": "alert",
      "displayName": "alert",
      "description": "Telemetry obtained from 'Thing Model Test' Thing Model",
      "comment": "2 forms: 1 - href: alrt / 2 - href: ws://localhost:8888/alert / "
    }
  ]
}
```

### _Thing Model 1.1_

```json
{
  "@context": "https://www.w3.org/2019/wot/td/v1",
  "id": "urn:testModel",
  "@type": "tm:ThingModel",
  "title": "Thing Model Test",
  "description": "Thing Model used for testing",
  "descriptions": {
    "en": "Thing Model used for testing",
    "it": "Modello utilizzato a fini di test",
    "fr": "Modèle utilisé à des fins d'essai'",
    "de": "Zu Testzwecken verwendetes Modell"
  },
  "securityDefinitions": {
    "nosec_sc": {
      "scheme": "nosec"
    }
  },
  "security": "nosec_sc",
  "base": "http://localhost:3000",
  "titles": {
    "en": "Thing Model Test",
    "it": "Modello di Test",
    "fr": "Modèle de test",
    "de": "Testmodel"
  },
  "properties": {
    "power": {
      "title": "availablePower",
      "type": "object",
      "properties": {
        "status": {}
      },
      "forms": [
        {
          "op": "readproperty",
          "contentType": "application/json;charset=utf-8",
          "href": "power"
        }
      ]
    },
    "content": {
      "title": "availableContent",
      "titles": {
        "en": "availableContent",
        "it": "contenutoDisponibile",
        "fr": "contenuDisponible",
        "de": "verfügbarerInhalt"
      },
      "description": "Content of the Test Model",
      "type": "string",
      "forms": [
        {
          "op": "readproperty",
          "contentType": "application/json;charset=utf-8",
          "href": "content"
        }
      ]
    },
    "temperature": {
      "title": "availableTemperature",
      "type": "integer",
      "forms": [
        {
          "op": "readproperty",
          "contentType": "application/json;charset=utf-8",
          "href": "temp"
        }
      ]
    },
    "status": {
      "type": "string",
      "description": "Current car status (readyToCharge, charging, stopCharging)",
      "readOnly": true,
      "enum": ["readyToCharge", "charging", "stopCharging"],
      "forms": [
        {
          "href": "/ecar/properties/status",
          "contentType": "application/json",
          "op": ["readproperty"]
        }
      ]
    },
    "rgb": {
      "title": "RGB color value",
      "type": "array",
      "items": {
        "type": "number",
        "minimum": 0,
        "maximum": 255
      },
      "minItems": 3,
      "maxItems": 3
    }
  },
  "actions": {
    "toggle": {
      "safe": true,
      "idempotent": false,
      "title": "togglePowerStatus",
      "forms": [
        {
          "op": "invokeaction",
          "contentType": "application/json;charset=utf-8",
          "href": "toggle"
        }
      ]
    },
    "setVolume": {
      "safe": true,
      "idempotent": false,
      "title": "setVolume",
      "forms": [
        {
          "op": "invokeaction",
          "contentType": "application/json;charset=utf-8",
          "href": "setvolume"
        }
      ]
    },
    "reboot": {
      "title": "SystemReboot",
      "description": "Reboots the system at the specified time",
      "input": {
        "type": "string",
        "format": "date-time",
        "title": "Reboot Time",
        "description": "Requested time to reboot the device."
      },
      "output": {
        "type": "string",
        "format": "date-time",
        "title": "Scheduled Time",
        "description": "Scheduled shutdown time"
      }
    },
    "playVideo": {
      "safe": true,
      "idempotent": false,
      "title": "playVideo",
      "forms": [
        {
          "op": "invokeaction",
          "contentType": "application/json;charset=utf-8",
          "href": "playvideo"
        }
      ],
      "input": {
        "type": "object",
        "description": "playVideo action request",
        "title": "playVideo Request",
        "properties": {
          "identifier": {
            "type": "string",
            "title": "Video Identifier",
            "description": "The unique identifier of a Video"
          },
          "name": {
            "type": "string",
            "title": "Video Name",
            "description": "The name of a Video file"
          },
          "timestamp": {
            "type": "string",
            "format": "date-time",
            "title": "Timestamp",
            "description": "Request Timestamp"
          },
          "url": {
            "type": "string",
            "title": "Video Url",
            "description": "The Video Url"
          }
        }
      },
      "output": {
        "type": "object",
        "properties": {
          "stream": {
            "type": "string"
          },
          "timestamp": {
            "type": "string",
            "format": "date-time"
          }
        }
      }
    }
  },
  "events": {
    "alert": {
      "title": "alert",
      "data": { "type": "object" },
      "forms": [
        {
          "op": "subscribeevent",
          "contentType": "application/json;charset=utf-8",
          "subprotocol": "longpoll",
          "href": "alrt"
        },
        {
          "op": "subscribeevent",
          "contentType": "application/json;charset=utf-8",
          "href": "ws://localhost:8888/alert"
        }
      ]
    }
  }
}
```

## Root / Thing Level

| DTDL Term / Concept      | DTDL Description                                                                       | WoT TD Term             | WoT TD Description                                                                                                    | Comments                                                                                                        |
| ------------------------ | -------------------------------------------------------------------------------------- | ----------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **displayName**          | A localizable name for display.                                                        | **title**               | Provides a human-readable title (e.g., display a text for UI representation) based on a default language.             | Derived from JSON schema. Proposal is to use the WoT definition.                                                |
|                          | Comment: displayName allows JSON-LD language map for multi-language support            | **titles**              | Provides multi-language human-readable titles (e.g., display a text for UI representation in different languages).    | Proposal is to keep WoT definition.                                                                             |
| **description**          | A localizable description for display.                                                 | **description**         | (human-readable) information based on a default language.                                                             | Derived from JSON schema. Proposal is to use the WoT definition.                                                |
|                          | Comment: description allows JSON-LD language map for multi-language support            | **descriptions**        | Can be used to support (human-readable) information in different languages.                                           | Proposal is to keep WoT definition.                                                                             |
| **comment**              | A comment for model authors.                                                           |                         |                                                                                                                       | Proposal is to keep the DTDL definition.                                                                        |
|                          |                                                                                        | **version**             | Provides version information.                                                                                         | Proposal is to keep WoT definition.                                                                             |
|                          |                                                                                        | **created**             | Provides information when the TD instance was created.                                                                | Proposal is to keep WoT definition.                                                                             |
|                          |                                                                                        | **modified**            | Provides information when the TD instance was last modified.                                                          | Proposal is to keep WoT definition.                                                                             |
|                          |                                                                                        | **support**             | Provides information about the TD maintainer as URI scheme (e.g., mailto [RFC6068], tel [RFC3966], https [RFC9112]).  | Proposal is to keep WoT definition.                                                                             |
| **content**              | A set of elements that define the contents of this Interface.                          |                         | Comment: Kind of interactions specified directly in properties, actions, and events container.                        | Proposal is to split this up into 3 separate fields, i.e. WoT "properties", "actions" and "events" (see below). |
| **schemas**              | A set of complex schema objects that are reusable within this Interface.               | **schemaDefinitions**   | Set of named data schemas. To be used in a schema name-value pair inside an AdditionalExpectedResponse object.        | Proposal is to keep WoT definition.                                                                             |
| **extends**              | A set of DTMIs that refer to Interfaces from which this Interface inherits contents... | **links**               | A Thing Model can extend an existing Thing Model by using the tm:extends mechanism announced in the links definition. | WoT uses [RFC8288] web linking for inheritance. Proposal is to use that.                                        |
|                          |                                                                                        |                         | Links provide Web links to arbitrary resources that relate to the specified Thing Description.                        |                                                                                                                 |
|                          |                                                                                        | **forms**               | Set of form hypermedia controls that describe how an operation can be performed.                                      | Used for WoT protocol bindings. Proposal is to use the WoT definition.                                          |
|                          |                                                                                        | **security**            | Set of security definition names, chosen from those defined in securityDefinitions.                                   | Proposal is to use the WoT definition.                                                                          |
|                          |                                                                                        | **securityDefinitions** | Set of named security configurations (definitions only).                                                              | Proposal is to use the WoT definition.                                                                          |
|                          |                                                                                        | **profile**             | Indicates mandatory fields defined in the profile. New in version 1.1. Not used yet.                                  | Proposal is to use the WoT definition.                                                                          |
|                          |                                                                                        | **uriVariables**        | Define URI template variables according to [RFC6570] as collection based on DataSchema declarations.                  | Proposal is to use the WoT definition.                                                                          |
| **"@type": "Property"**  | A Property describes the read-only and read/write state of any digital twin.           | **properties**          | All Property-based Interaction Affordances of the Thing.                                                              | Proposal is to use the WoT definition.                                                                          |
| **"@type": "Command"**   | A Command describes a function or operation that can be performed on any digital twin. | **actions**             | All Action-based Interaction Affordances of the Thing.                                                                | Proposal is to use the WoT definition.                                                                          |
| **"@type": "Telemetry"** | Telemetry describes the data emitted by any digital twin, whether the data is ...      | **events**              | All Event-based Interaction Affordances of the Thing.                                                                 | Proposal is to use the WoT definition.                                                                          |

### Examples

#### _DTDL v3_

```json
{
  "@context": "dtmi:dtdl:context;3",
  "@id": "dtmi:test:model;1",
  "@type": "Interface",
  "displayName": "Test Model",
  "description": "Thing Model Test",
  "comment": "http://localhost:3000",
  "contents": []
}
```

#### _Thing Model 1.1_

```json

{
  "@context": "https://www.w3.org/2019/wot/td/v1",
  "id": "urn:testModel",
  "@type": "tm:ThingModel",
  "description" : "Thing Model Test",
  "securityDefinitions": {
    "nosec_sc": {
      "scheme": "nosec"
    }
  },
  "security": "nosec_sc",
  "base": "http://localhost:3000",
  "title": "Test Model",
  "properties": []

}
```

## Interface schemas

| DTDL Term / Concept | DTDL Description                                  | WoT TD Term     | WoT TD Description                                                                                        | Comments |
|---------------------|---------------------------------------------------|-----------------|-----------------------------------------------------------------------------------------------------------|----------|
| **@type**           | This must be "Array", "Enum", "Map", or "Object". | ...             | ...                                                                                                       |          |
| **@id**             | An identifer for the complex schema.              | ...             | ...                                                                                                       |          |
| **comment**         | A comment for model authors.                      | ...             | ...                                                                                                       |          |
| **description**     | A localizable description for display.            | **description** | (human-readable) information based on a default language.                                                 |          |
| **displayName**     | A localizable name for display.                   | **title**       | Provides a human-readable title (e.g., display a text for UI representation) based on a default language. |          |

## Property/Telemetry Level

| DTDL Term / Concept | DTDL Description                                                        | WoT TD Term        | WoT TD Description                                                                                                     | Comments                                                            |
| ------------------- | ----------------------------------------------------------------------- | ------------------ | ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **displayName**     | A localizable name for display.                                         | **title**          | Provides a human-readable title (e.g., display a text for UI representation) based on a default language.              | Derived from JSON schema. Proposal is to use the WoT definition.    |
| **description**     | A localizable description for display.                                  | **description**    | (human-readable) information based on a default language.                                                              | Derived from JSON schema. Proposal is to use the WoT definition.    |
| **comment**         | A comment for model authors.                                            |                    |                                                                                                                        | Proposal is to keep the DTDL definition.                            |
| **name**            | The programming name of the element.                                    | **{property key}** | Comment: Programming name is assigned as key name of the property                                                      | Proposal is to keep the DTDL definition but convert to JSON-LD 1.1. |
| **schema**          | The data type of the Property, which is an instance of Schema.          | **type**           | Assignment of JSON-based data types compatible with JSON Schema                                                        | Proposal is to keep WoT definition.                                 |
| **writable**        | A boolean value that indicates whether the Property is writable or not. | **writeOnly**      | Boolean value that is a hint to indicate whether a property interaction / value is write only (=true) or not (=false). | Proposal is to use the WoT definition.                              |
|                     |                                                                         | **readOnly**       | Boolean value that is a hint to indicate whether a property interaction / value is read only (=true) or not (=false).  | Proposal is to use the WoT definition.                              |
|                     |                                                                         | **observable**     | Boolean value that is a hint to indicate whether a property interaction / value is observable (=true) or not (=false). | Proposal is to use the WoT definition.                              |
|                     |                                                                         | **forms**          | Set of form hypermedia controls that describe how an operation can be performed (used for protocol bindings).          | Proposal is to use the WoT definition.                              |
|                     |                                                                         | **uriVariables**   | Define URI template variables according to [RFC6570] as collection based on DataSchema declarations.                   | Proposal is to use the WoT definition.                              |
|                     |                                                                         | **{DataSchema}**   | Comment: At property level there can be the terms from data schema                                                     | Proposal is to use the WoT definition.                              |

### Examples

#### _DTDL v3_

```json

{
  "@type": "Property",
  "writable": false,
  "schema": "string",
  "name": "content",
  "displayName": "availableContent",
  "description": "Content of the Test Model",
  "comment": "1 form: 1- Thing Model form href: content"
},

```

#### _Thing Model 1.1_

```json
"properties" :{
  "content": {
    "title": "availableContent",
    "type": "string",
    "description": "Content of the Test Model",
    "forms": [
      {
        "op": "readproperty",
        "contentType": "application/json;charset=utf-8",
        "href": "content"
      }
    ]
  }
}

```

## Commands Level

| DTDL Term / Concept | DTDL Description                                                     | WoT TD Term       | WoT TD Description                                                | Comments                                                            |
| ------------------- | -------------------------------------------------------------------- | ----------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| **@type**           | If provided, must be "Command"                                       | **action**        |                                                                   | Proposal: Use JSON-LD 1.1 style for better JSON processing          |
| **@id**             | Identifier for the commnand. Assigned automatically if not provided. |                   | Same concept from JSON-LD                                         |                                                                     |
| **comment**         | A comment for model authors                                          |                   |                                                                   |                                                                     |
| **description**     | Comment for model authors                                            | **description**   | (human-readable) information based on a default language.         |                                                                     |
| **displayName**     | A localizable name for display.                                      | **title**         | Human-readable title based on a default language.                 |                                                                     |
| **name**            | The programming name of the element.                                 | **{command-key}** | Comment: Programming name is assigned as key name of the property | Proposal is to keep the DTDL definition but convert to JSON-LD 1.1. |
| **request**         | A description of the input to the Command.                           | **input**         | The input data schema of the Action {DataSchema format}           |                                                                     |
| **response**        | A description of the output of the Command.                          | **output**        | The output data schema of the Action {DataSchema format}          |                                                                     |

### Examples

_DTDL v3_

```json
{
  "@type": "Command",
  "Request": {
    "@type": "CommandRequest",
    "name": "rebootRequest",
    "displayName": "Reboot Time",
    "description": "Requested time to reboot the device.",
    "schema": "dateTime"
  },
  "Response": {
    "@type": "CommandResponse",
    "name": "rebootResponse",
    "displayName": "Scheduled Time",
    "description": "Scheduled shutdown time",
    "schema": "dateTime"
  },
  "name": "reboot",
  "displayName": "SystemReboot",
  "description": "Reboots the system at the specified time"
}
```

_Thing Model 1.1_

```json

"actions":{
 "reboot": {
   "title": "SystemReboot",
   "description": "Reboots the system at the specified time",
   "input": {
     "type": "string",
     "format": "date-time",
     "title": "Reboot Time",
     "description": "Requested time to reboot the device."
   },
   "output": {
     "type": "string",
     "format": "date-time",
     "title": "Scheduled Time",
     "description": "Scheduled shutdown time"
   }
 }
}
```

## Primitive schema

| DTDL Term / Concept | DTDL Description                                                                                                          | WoT TD Term                         | WoT TD Description | Comments                                                                       |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- | ------------------ | ------------------------------------------------------------------------------ |
| **boolean**         | a boolean value                                                                                                           | type: **boolean**                   | ...                |                                                                                |
| **date**            | a date in ISO 8601 format, per [RFC 3339](https://tools.ietf.org/html/rfc3339)                                            | type: **string + format=date-time** | ...                |                                                                                |
| **dateTime**        | a date and time in ISO 8601 format per [RFC 3339](https://tools.ietf.org/html/rfc3339)                                    | type: **string + format=date-time** | ...                |                                                                                |
| **double**          | a finite numeric value that is expressible in IEEE 754 double-precision floating point format, conformant with xsd:double | type: **number**                    | ...                |                                                                                |
| **duration**        | a duration in ISO 8601 format                                                                                             | type: **string + format=duration**  | ...                |                                                                                |
| **float**           | a finite numeric value that is expressible in IEEE 754 single-precision floating point format, conformant with xsd:float  | type: **number**                    |                    | for conversion purposes, number will be always mapped as a double (TM to DTDL) |
| **integer**         | a signed integral numeric value that is expressible in 4 bytes                                                            | type: **integer**                   | ...                |                                                                                |
| **long**            | a signed integral numeric value that is expressible in 8 bytes                                                            | type: **number**                    |                    | for conversion purposes, number will be always mapped as a double (TM to DTDL) |
| **string**          | a UTF8 string                                                                                                             | **string**                          | ...                |                                                                                |
| **time**            | a time in ISO 8601 format, per [RFC 3339](https://tools.ietf.org/html/rfc3339)                                            | type: **string + format=time**      | ...                |                                                                                |

## Array

An Array describes an indexable data type where each element is of the same schema.
The schema for an Array's element can itself be a primitive or complex schema.

The chart below lists the properties that an Array may have.

| DTDL Term / Concept | DTDL Description                                                                       | WoT TD Term     | WoT TD Description                                            | Comments |
| ------------------- | -------------------------------------------------------------------------------------- | --------------- | ------------------------------------------------------------- | -------- |
| **@type**           | This must be "Array".                                                                  | ...             | ...                                                           |          |
| **@id**             | An identifer for the Array. If no @id is provided, one will be assigned automatically. | ...             | ...                                                           |          |
| **comment**         | A comment for model authors.                                                           | ...             | ...                                                           |          |
| **description**     | A localizable description for display.                                                 | **description** | (human-readable) information based on a default language.     |          |
| **displayName**     | A localizable name for display.                                                        | **title**       | (human-readable) title based on a default language.           |          |
| **elementSchema**   | The data type of each element in the Array, which is an instance of Schema.            | **items.type**  | The definition of the array type is based on DataSchema Types |          |

### Examples

#### _DTDL v3_

```json

"schema": {
  "elementSchema": "double",
  "displayName": "RGB color value",
  "@type": "Array"
}

```

#### _Thing Model 1.1_

```json
{
 "title": "RGB color value",
 "type": "array",
 "items": {
   "type": "number",
   "minimum": 0,
   "maximum": 255
 },
 "minItems": 3,
 "maxItems": 3
}

```

## Enum

| DTDL Term / Concept | DTDL Description                                                                      | WoT TD Term     | WoT TD Description                                        | Comments |
| ------------------- | ------------------------------------------------------------------------------------- | --------------- | --------------------------------------------------------- | -------- |
| **@type**           | This must be "Enum".                                                                  | ...             | ...                                                       |          |
| **@id**             | An identifer for the Enum. If no @id is provided, one will be assigned automatically. | ...             | ...                                                       |          |
| **comment**         | A comment for model authors.                                                          | ...             | ...                                                       |          |
| **description**     | A localizable description for display.                                                | **description** | (human-readable) information based on a default language. |          |
| **displayName**     | A localizable name for display.                                                       | **title**       | (human-readable) title based on a default language.       |          |
| **enumValues**      | A set of name/value mappings for the Enum.                                            | **enum**        | A list of strings representing the possible enum values   |          |
| **valueSchema**     | The data type for the enumValues; all values must be of the same type.                | **type**        | ...                                                       |          |

### EnumValue

| DTDL Term / Concept | DTDL Description                                                                              | WoT TD Term  | WoT TD Description                             | Comments |
| ------------------- | --------------------------------------------------------------------------------------------- | ------------ | ---------------------------------------------- | -------- |
| **@type**           | If provided, must be "EnumValue".                                                             | ...          | ...                                            |          |
| **@id**             | An identifer for the EnumValue. Assigned automatically if not provided                        | ...          | ...                                            |          |
| **comment**         | A comment for model authors.                                                                  | ...          | ...                                            |          |
| **description**     | A localizable description for display.                                                        |              |                                                |
| **displayName**     | A localizable name for display.                                                               | **enum.key** | In TMs, the displayName is the name of the enum itself |          |
| **enumValue**       | The on-the-wire value that maps to the EnumValue, which may be either an integer or a string. | **enum.key** | In TMs, the value is the name of the enum itself       |          |
| **name**            | The programming name of the element.                                                          | **enum.key** | In TMs, the name is the name of the enum itself        |          |

### Examples

#### _DTDL v3_

```json
"schema": {
  "valueSchema": "string",
  "description": "Current car status (readyToCharge, charging, stopCharging)",
  "enumValues": [
    {
      "@type": "EnumValue",
      "displayName": "readyToCharge",
      "name": "readyToCharge",
      "enumValue": "readyToCharge"
    },
    {
      "@type": "EnumValue",
      "displayName": "charging",
      "name": "charging",
      "enumValue": "charging"
    },
    {
      "@type": "EnumValue",
      "displayName": "stopCharging",
      "name": "stopCharging",
      "enumValue": "stopCharging"
    }
  ],
  "@type": "Enum"
}
```

#### _Thing Model 1.1_

```json


 "status": {
   "type": "string",
   "description": "Current car status (readyToCharge, charging, stopCharging)",
   "enum": [
     "readyToCharge",
     "charging",
     "stopCharging"
   ],
   "forms": []
 }


```

## Object

| DTDL Term / Concept | DTDL Description                                                                        | WoT TD Term     | WoT TD Description                                                          | Comments |
| ------------------- | --------------------------------------------------------------------------------------- | --------------- | --------------------------------------------------------------------------- | -------- |
| **@type**           | This must be "Object".                                                                  | ...             | ...                                                                         |          |
| **@id**             | An identifer for the Object. If no @id is provided, one will be assigned automatically. | ...             | ...                                                                         |          |
| **comment**         | A comment for model authors.                                                            | ...             | ...                                                                         |          |
| **description**     | A localizable description for display.                                                  | **description** | (human-readable) information based on a default language.                   |
| **displayName**     | A localizable name for display.                                                         | **title**       | (human-readable) title based on a default language.                         |          |
| **fields**          | A set of field descriptions, one for each field in the Object.                          | **properties**  | A dictionary of object properties which follow the DataSchema specification |          |

### Field

A Field describes a field in an Object.

The chart below lists the properties that a Field may have.

| DTDL Term / Concept | DTDL Description                                                                       | WoT TD Term        | WoT TD Description                                        | Comments |
| ------------------- | -------------------------------------------------------------------------------------- | ------------------ | --------------------------------------------------------- | -------- |
| **@type**           | If provided, must be "Field".                                                          | ...                | ...                                                       |          |
| **@id**             | An identifer for the Field. If no @id is provided, one will be assigned automatically. | ...                | ...                                                       |          |
| **comment**         | A comment for model authors.                                                           | ...                | ...                                                       |          |
| **description**     | A localizable description for display.                                                 | **description**    | (human-readable) information based on a default language. |
| **displayName**     | A localizable name for display.                                                        | **title**          | (human-readable) title based on a default language.       |          |
| **name**            | The programming name of the element.                                                   | **properties.key** | the name is the key of a property field                   |          |
| **schema**          | The data type of the element, which is an instance of Schema.                          | **type**           | Type follows the DataSchema specification                 |          |

### Examples

#### _DTDL v3_

```json

"schema": {
  "displayName": "playVideoRequest",
  "description": "playVideo action request",
  "fields": [
    {
      "@type": "Field",
      "displayName": "VideoIdentifier",
      "name": "identifier",
      "description": "The unique identifier of a Video",
      "schema": "string"
    },
    {
      "@type": "Field",
      "displayName": "VideoName",
      "name": "name",
      "description": "The name of a Video file",
      "schema": "string"
    },
    {
      "@type": "Field",
      "displayName": "Timestamp",
      "name": "timestamp",
      "description": "Request Timestamp",
      "schema": "dateTime"
    },
    {
      "@type": "Field",
      "displayName": "VideoUrl",
      "name": "url",
      "description": "The Video Url",
      "schema": "string"
    }
  ],
  "@type": "Object"
}

```

#### _Thing Model 1.1_

```json

{
 "type": "object",
 "description": "playVideo action request",
 "title": "playVideo Request",
 "properties": {
   "identifier": {
     "type": "string",
     "title": "Video Identifier",
     "description": "The unique identifier of a Video"
   },
   "name": {
     "type": "string",
     "title": "Video Name",
     "description": "The name of a Video file"
   },
   "timestamp": {
     "type": "string",
     "format": "date-time",
     "title": "Timestamp",
     "description": "Request Timestamp"
   },
   "url": {
     "type": "string",
     "title": "Video Url",
     "description": "The Video Url"
   }
}

```

## Geospatial Schemas

DTDL provides a set of geospatial schemas, based on [GeoJSON](https://geojson.org/), for modeling a variety of geographic data structures.

| DTDL Term / Concept | DTDL Description                                                            | WoT TD Term | WoT TD Description | Comments |
| ------------------- | --------------------------------------------------------------------------- | ----------- | ------------------ | -------- |
| **lineString**      | GeoJSON LineString - dtmi:standard:schema:geospatial:lineString;3           | ...         | ...                | Proposal is to use the Geojson RFC |
| **multiLineString** | GeoJSON MultiLineString - dtmi:standard:schema:geospatial:multiLineString;3 | ...         | ...                |          |
| **multiPoint**      | GeoJSON MultiPoint - dtmi:standard:schema:geospatial:multiPoint;3           | ...         | ...                |          |
| **multiPolygon**    | GeoJSON MultiPolygon - dtmi:standard:schema:geospatial:multiPolygon;3       | ...         | ...                |          |
| **point**           | GeoJSON Point - dtmi:standard:schema:geospatial:point;3                     | ...         | ...                |          |
| **polygon**         | GeoJSON Polygon - dtmi:standard:schema:geospatial:polygon;3                 | ...         | ...                |          |

### Examples

#### _DTDL v3_

This example shows modeling the location of a device as Telemetry using the geospatial schema `point`.

```json

{
  "@type": "Telemetry",
  "name": "location",
  "schema": "point"
}

```

A Telemetry message sent by a particular device reporting its location would have the following structure in JSON (and equivalent structure in other serializations).

```json

{
  "location": {
    "type": "Point",
    "coordinates": [ 47.643742, -122.128014 ]
  }
}

```

# Unsolved Mappings

## Map

| DTDL Term / Concept | DTDL Description                                                                     | WoT TD Term | WoT TD Description | Comments |
| ------------------- | ------------------------------------------------------------------------------------ | ----------- | ------------------ | -------- |
| **@type**           | This must be "Map". `                           `                                    | ...         | ...                |          |
| **@id**             | An identifer for the Map. If no @id is provided, one will be assigned automatically. | ...         | ...                |          |
| **comment**         | A comment for model authors.                                                         | ...         | ...                |          |
| **description**     | A localizable description for display.                                               | ...         | ...                |          |
| **displayName**     | A localizable name for display.                                                      | ...         | ...                |          |
| **mapKey**          | A description of the keys in the Map.                                                | ...         | ...                |          |
| **mapValue**        | A description of the values in the Map.                                              | ...         | ...                |          |

### MapKey

| DTDL Term / Concept | DTDL Description                                                                        | WoT TD Term | WoT TD Description | Comments |
| ------------------- | --------------------------------------------------------------------------------------- | ----------- | ------------------ | -------- |
| **@type**           | If provided, must be "MapKey".                                                          | ...         | ...                |          |
| **@id**             | An identifer for the MapKey. If no @id is provided, one will be assigned automatically. | ...         | ...                |          |
| **comment**         | A comment for model authors.                                                            | ...         | ...                |          |
| **description**     | A localizable description for display.                                                  | ...         | ...                |          |
| **displayName**     | A localizable name for display.                                                         | ...         | ...                |          |
| **name**            | The programming name of the element.                                                    | ...         | ...                |          |
| **schema**          | The data type of the Map's key, which must be string.                                   | ...         | ...                |          |

### MapValue

| DTDL Term / Concept | DTDL Description                                                        | WoT TD Term | WoT TD Description | Comments |
| ------------------- | ----------------------------------------------------------------------- | ----------- | ------------------ | -------- |
| **@type**           | If provided, must be "MapValue".                                        | ...         | ...                |          |
| **@id**             | An identifer for the MapValue. Assigned automatically if none provided. | ...         | ...                |          |
| **comment**         | A comment for model authors.                                            | ...         | ...                |          |
| **description**     | A localizable description for display.                                  | ...         | ...                |          |
| **displayName**     | A localizable name for display.                                         | ...         | ...                |          |
| **name**            | The programming name of the element.                                    | ...         | ...                |          |
| **schema**          | The data type of the element, which is an instance of Schema.           | ...         | ...                |          |

## Relationship Level

| DTDL Term / Concept | DTDL Description                                                                                           | WoT Term                 | WoT Description                                          | Comments                      |
|---------------------|------------------------------------------------------------------------------------------------------------|--------------------------|----------------------------------------------------------|-------------------------------|
| **@type**           | If provided, must be "Relationship"                                                                        | ***"@type":"hctl:link"** |                                                          | Implicit, can add dtmi type   |
| **@id**             | Identifier for the Relationship. Assigned automatically if not provided.                                   | **"@id"**                |                                                          |                               |
| **comment**         | A comment for model authors                                                                                | -                        |                                                          |                               |
| **description**     | Comment for model authors                                                                                  | -                        |                                                          | "td:description"              |
| **displayName**     | A localizable name for display.                                                                            | -                        |                                                          | "td:title"                    |
| **maxMultiplicity** | The max multiplicity for the realtionship target; defaults to the max allowable value                      | -                        |                                                          | Propose to W3C                |
| **minMultiplicity** | The min multiplicity for the realtionship target; defaults to the max allowable value                      | -                        |                                                          | Propose to W3C                |
| **name**            | The programming name of the element.                                                                       | **"rel"**                | A link relation type identifies the semantics of a link. | Is it used in DTDL?           |
| **properties**      | A set of Properties that define Relationship-specific state.                                               | -                        |                                                          |                               |
| **target**          | An Interface identifier. If no target is specified, each instance target is permitted to be any Interface. | **"href"**               | Target IRI of a link or submission target of a form.     |                               |
| **writable**        | A boolean value that indicates whether the Relationship is writable or not.                                | -                        |                                                          | What does writable mean here? |

From `Ontologies/ISA95/CommonObjectModels/Part2/OperationsSchedule/OperationsSchedule.json`
```json
        {
            "@type": "Relationship",
            "name": "isMadeUpOf",
            "displayName": "Is made up of",
            "description": "The operations requests that make up the operations schedule.",
            "target": "dtmi:digitaltwins:isa95:OperationsRequest;1"
        },
```

```json
        {
            "@type": "dtmi:Relationship",
            "rel": "isMadeUpOf",
            "title": "Is made up of",
            "description": "The operations requests that make up the operations schedule.",
            "href": "dtmi:digitaltwins:isa95:OperationsRequest;1"
        },
```


## Component Level

| DTDL Term / Concept | DTDL Description                                                               | WoT TD Term       | WoT TD Description         | Comments |
|---------------------|--------------------------------------------------------------------------------|-------------------|----------------------------|----------|
| **@type**           | This must be "Component".                                                      | **@type**         | This must be "tm:submodel" |          |
| **@id**             | An identifer for the Component. If no @id is provided, assigned automatically. | **@id**           | Same as DTDL               |          |
| **comment**         | A comment for model authors.                                                   | -                 |                            |          |
| **description**     | A localizable description for display.                                         | -                 |                            |          |
| **displayName**     | A localizable name for display.                                                | -                 |                            |          |
| **name**            | The programming name of the element.                                           | -                 |                            |          |
| **schema**          | The data type of the Component, which is an instance of Interface.             | **href**/**type** | IRI of TM                  |          |
