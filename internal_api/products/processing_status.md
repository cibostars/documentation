# Products - Processing status

Get status about async operation (see [bulk_insert](bulk_import.md)).

### Request
`GET /internal_api/processing_status/:id.json`

`id` - Identifier of a processing object. You can get it from API responses (i.e [bulk_insert](bulk_import.md)).

### Response
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

All possible statuses:

| Status       | Description                                                                |
|--------------|----------------------------------------------------------------------------|
| created      | Initial status when request is received                                    |
| preprocessed | Json data was validated. Waiting for async processing                      |
| processing   | Async processing                                                           |
| succeeded    | Data was successfully processed and saved                                  |
| failed       | Error at preprocessing or processing stage. Data from request wasn't saved |

### Example:
##### Request
`GET /internal_api/processing_status/11.json`

##### Response
```json
{
  "processing_object": {
    "id": 11,
    "status": "succeeded",
    "info": "Processed: 10; Created: 1; Updated: 2; Deleted: 3; Restored: 1"
  }
}

```
| Info      | Description                                                   |
|-----------|---------------------------------------------------------------|
| Processed | Number of all products that has been processed during request |
| Created   | Number of new products that has been created                  |
| Updated   | Number of products that has been updated                      |
| Deleted   | Number of products that has been deleted                      |
| Restored  | Number of products that has been restored from deleted state  |


