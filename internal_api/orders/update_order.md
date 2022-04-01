# Order - Update one

Update one order.

### Request
`PUT internal_api/orders/:id.json`

`id` - Identifier of an order.

```json
{
  "order": {
    "status": "string"
  }
}
```

### Response
Update order is a synchronous operation. You will get final status of an operation.
```json
{
  "processing_object": {
    "id": "integer",
    "status": "string",
    "info": "string, presented only if status is succeeded",
    "errors": "string, presented only if status is failed"
  }
}
```

Possible statuses:

| Status    | Description                               |
|-----------|-------------------------------------------|
| succeeded | Data was successfully processed and saved |
| failed    | Error. Data from request wasn't saved     |

### Example:
##### Request
`PUT internal_api/orders/cdb3d536-92d6-4eb9-8840-1b2ad164b4ce.json`
```json
{
  "order": {
    "status": "confirmed"
  }
}
```

##### Response
```json
{
  "processing_object": {
    "id": 10,
    "status": "succeeded",
    "info": "Updated: 1"
  }
}
```