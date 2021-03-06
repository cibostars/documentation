# Products - Upsert one

Create or update one product.

### Request
`POST internal_api/products/upsert.json`

```json
{
  "product": {
    "internal_id": "string",
    "title": "string",
    "weight": "string",
    "price": "string",
    "deleted": "boolean"
  }
}
```

### Response
Create product is a synchronous operation. You will get final status of an operation.
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
`POST internal_api/products/upsert.json`
```json
{
  "product": {
    "internal_id": "a1ewd2f",
    "title": "Маргарита",
    "weight": "200 г",
    "price": "2000.00",
    "deleted": false
  }
}
```

##### Response
```json
{
  "processing_object": {
    "id": 10,
    "status": "succeeded",
    "info": "Created: 1"
  }
}
```