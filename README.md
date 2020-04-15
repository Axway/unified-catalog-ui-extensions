# Custom UI extensions for Unified Catalog

In April 2020, Amplify Central Unified Catalog added support for CUSTOM catalog items types that can provide consumers 
access to unstructured data types. 
At the same time, support was added to attach additional data to any of the existing supported catalog item types.

The unstructured data can be attached by the provider in Base64 encoding, but it can be retrieved back by the consumer
decoded using information attached to the Catalog Item by the provider.

Example of providing metadata on the attached data:
```json
{
    "fileName": "service-details.json",
    "label": "Microservice Canvas",
    "type": "service-details",
    "contentType": "application/json"
}
```
The _fileName_ and _contentType_ fields are used by the Unified Catalog download functionality and default rendering.
Currently Unified Catalog will automatically render text/plain and text/markdown.

The  _type_ field is user defined, it can be any string.

All the custom extensions in this repository will be rendered based on the _type_ value.

The data linked to the provided metadata can have any structure. In the above example, the metadata indicates that the
data is provided as JSON.
An example could be:
```json
{
    "description": "The service provides APIs for creating, updating and cancelling orders",
    "api": {
        "commands": [
            {
                "name": "Create order",
                "type": "sync"
            }
        ],
        "queries": [
            {
                "name": "getAll",
                "description": "Retrieve all orders"
            }
        ],
        "events": [
            "Order created",
            "Order Cancelled"
        ]
    },
    "nonFunctionalRequirements": [
        "99% availability",
        "1000 orders/second"
    ],
    "observability": {
        "metrics": "orders_created"
    },
    "dependencies": [
        "inventory",
        "payment"
    ]
}
```

Using the UI extensions, this data can be rendered similar to the table provided example from:
https://chrisrichardson.net/post/microservices/general/2019/02/27/microservice-canvas.html

# UI Extension examples

Axway will be offering an _axway:demo_ type with the supported UI components that can be used to render custom 
unstructured types and additional unstructured data that can be attached to already supported Unified Catalog types.
