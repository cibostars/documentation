# Products - Delete one

Delete one product

### Request
`DELETE internal_api/products/:internal_id.json`

`internal_id` - Identifier of a product.

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
`DELETE internal_api/products/a1ewd2f.json`

##### Response
```json
{
  "processing_object": {
    "id": 10,
    "status": "succeeded",
    "info": "Deleted: 1"
  }
}
```