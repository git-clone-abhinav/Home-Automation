# Device Registry Service

## Usage

All responses will have the form

```json
{
    "data": "Mixed type holding the contect of the response",
    "message": "Description of what happened"
}
```

### List all the Devices

**Definition**

`GET /devices`

**Resources**

- `200 OK` on Success

```json
[
    {
    "identifier": "floor-lamp",
    "name": "Floor Lamp",
    "device_type": "switch",
    "controller_gateway": "192.168.1.24"
    },
    {
    "identifier": "samsung-tv",
    "name": "Living Room TV",
    "device_type": "tv",
    "controller_gateway": "192.168.1.24"
    }
]
```

### Registering a new device

**Definition**

`POST /devices`

**Arguments**
- `"identifier":string` a globally unique identifier for this device
- `"name":string` a friendly name to the device
- `"device_type":string` the type of the device as understood by the client
- `"controller_gateway":string` the IP address of the device's controller

If a device with the given identifier already exists, the existing device will be overwritten.

**Response**

- `201 Created` on success

```json
{
    "identifier": "floor-lamp",
    "name": "Floor Lamp",
    "device_type": "switch",
    "controller_gateway": "192.168.1.24"
}
```

## Lookup device details

`Get /device/<identifier>`

**Response**

- `404 Not Foud` if the device does not exist
- `200 OK` on success

## Delete a device

**Response**

-`404 Not Found` if the devices does not exist
-`203 No Content` on success