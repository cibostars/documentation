# Products - Bulk Insert

Create or update many products.

### Request
`POST /internal_api/products/bulk_insert.json`
```json
{
  "products": [
    {
      "internal_id": "string",
      "title": "string",
      "weight": "string",
      "price": "string",
      "deleted": "boolean"
    }
  ]
}
```
> All keys must be specified in a request even if their values are empty.

### Response
Bulk insert is an asynchronous operation. If you want to get actual information about request - use [processing_status](processing_status.md)
API endpoint with `id` parameter from that response.

```json
{
  "processing_object": {
    "id": "integer",
    "status": "string",
    "errors": "string, presented only if status is failed"
  }
}
```

Possible statuses:

| Status       | Description                                                  |
|--------------|--------------------------------------------------------------|
| preprocessed | Json data was validated. Waiting for async processing        |
| failed       | Error at preprocessing stage. Data from request wasn't saved |


### Example:
##### Request
`POST internal_api/products/bulk_insert.json`
```json
{
  "products": [
    {
      "internal_id": "kd1fe2f3ke",
      "title": "Калифорния",
      "weight": "300 г",
      "price": "1000.00",
      "deleted": false
    },
    {
      "internal_id": "uio123jnds",
      "title": "Пепперони 30см",
      "weight": "659",
      "price": "2400.00",
      "deleted": true
    }
  ]
}
```
##### Response
```json
{
  "processing_object": {
    "id": 10,
    "status": "preprocessed"
  }
}
```
