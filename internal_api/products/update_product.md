# Products - Create one

Update one product

### Request
`PUT internal_api/products/:internal_id.json`

`internal_id` - Identifier of a product.

```json
{
  "product": {
    "title": "string",
    "weight": "string",
    "price": "string"
  }
}
```

### Response
Update product is a synchronous operation. You will get final status of an operation.
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
`PUT internal_api/products/a1ewd2f.json`
```json
{
  "product": {
    "price": "2500.00"
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