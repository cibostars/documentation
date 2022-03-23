# Orders - Get list

Get list of orders within specified date range

### Request
`GET /internal_api/orders.json`

Params:
- `start_date` - ISO 8601 datetime format
- `end_date`- ISO 8601 datetime format

### Response
```json
{
  "orders": [
    {
      "id": "integer",
      "created_at": "string, ISO 8601 datetime format",
      "status": "string",
      "payment_status": "string",
      "payment_method": "string",
      "source_type": "string",
      "comment": "string",
      "change": "string",
      "products": [
        {
          "internal_id": "string",
          "quantity": "integer",
          "price": {
            "base_for_one": "string, price for one product without discounts",
            "base_total": "string, total price for product (+ quantity and additions) without discounts"
          },
          "additions": [
            {
              "internal_id": "string"
            }
          ]
        }
      ],
      "customer": {
        "id": "integer",
        "name": "string",
        "mobile_phone": "string"
      },
      "delivery": {
        "address": "string",
        "datetime": "string",
        "price": {
          "base_total": "string, total price for delivery without discounts"
        }
      },
      "price": {
        "delivery_base": "string, total price for delivery without discounts",
        "products_base": "string, total price for products without discounts",
        "order_base_total": "string, total price for order without discounts"
      }
    }
  ]
}
```
Statuses:

| Status    | Description                                                                                     |
|-----------|-------------------------------------------------------------------------------------------------|
| created   | Order has been created. Basic status for orders not processed by sales manager                  |
| confirmed | Order has been confirmed by sales manager                                                       |
| delivered | Order has been successfully delivered to customer                                               |
| cancelled | Order has been canceled by sales manager or payment by card has been declined by payment system |

Payment statuses:

| Payment Status | Description                                |
|----------------|--------------------------------------------|
| unpaid         | Waiting for payment by card                |
| paid           | Payment by card has been successfully done |

Payment method:

| Payment Method | Description     |
|----------------|-----------------|
| card           | Payment by card |
| cash           | Payment by cash |

Source type:

| Source Type | Description                           |
|-------------|---------------------------------------|
| web         | Order has been placed from web        |
| mobile      | Order has been placed from mobile app |

### Example:
##### Request
`GET /internal_api/orders.json&start_date=2022-03-05T14:00:00.000+06:00&end_date=2022-03-05T18:00:00.000+06:00`

##### Response
```json
{
  "orders": [
    {
      "id": 1,
      "created_at": "2022-03-05T17:50:13.513+06:00",
      "status": "created",
      "payment_status": "unpaid",
      "payment_method": "card",
      "source_type": "web",
      "comment": "Do not call me!!!",
      "change": "",
      "products": [
        {
          "internal_id": "internal_448_2",
          "quantity": 1,
          "price": {
            "base_for_one": "2600.00",
            "base_total": "3150.00"
          },
          "additions": [
            {
              "internal_id": "internal_0_0"
            },
            {
              "internal_id": "internal_486_0"
            }
          ]
        },
        {
          "internal_id": "internal_195_0",
          "quantity": 2,
          "price": {
            "base_for_one": "1850.00",
            "base_total": "4000.00"
          },
          "additions": [
            {
              "internal_id": "internal_0_0"
            }
          ]
        },
        {
          "internal_id": "internal_143_0",
          "quantity": 1,
          "price": {
            "base_for_one": "1400.00",
            "base_total": "1400.00"
          },
          "additions": []
        }
      ],
      "customer": {
        "id": 1,
        "name": "Ivan",
        "mobile_phone": "79000000000"
      },
      "delivery": {
        "address": "Алматы, жилой комплекс Клубный дом на Чайковского, 149, кв/оф 123",
        "datetime": "Как можно скорее",
        "price": {
          "base_total": "400.00"
        }
      },
      "price": {
        "delivery_base": "400.00",
        "products_base": "8550.00",
        "order_base_total": "8950.00"
      }
    },
    {
      "id": 2,
      "created_at": "2022-03-05T17:50:32.148+06:00",
      "status": "created",
      "payment_status": "unpaid",
      "payment_method": "cash",
      "source_type": "mobile",
      "comment": "",
      "change": "2500",
      "products": [
        {
          "internal_id": "internal_448_0",
          "quantity": 1,
          "price": {
            "base_for_one": "1850.00",
            "base_total": "1850.00"
          },
          "additions": []
        }
      ],
      "customer": {
        "id": 2,
        "name": "Sam",
        "mobile_phone": "71234567890"
      },
      "delivery": {
        "address": "Алматы, улица Досмухамедова, 54А, кв/оф 23",
        "datetime": "14:30 05.03.22",
        "price": {
          "base_total": "400.00"
        }
      },
      "price": {
        "delivery_base": "400.00",
        "products_base": "1850.00",
        "order_base_total": "2250.00"
      }
    }
  ]
}
```



