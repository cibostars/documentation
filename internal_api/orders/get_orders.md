# Orders - Get list

Get list of paid and not confirmed orders.

### Request
`GET /internal_api/orders.json`

### Response
```json
{
  "orders": [
    {
      "id": "string",
      "created_at": "string, ISO 8601 datetime format",
      "status": "string",
      "payment_status": "string",
      "payment_method": "string",
      "source_type": "string",
      "comment": "string",
      "change": "string",
      "brand": "string",
      "products": [
        {
          "internal_id": "string",
          "title": "string",
          "quantity": "integer",
          "price": {
            "base_for_one": "string, price for one product without discounts",
            "base_total": "string, total price for product (+ quantity and additions) without discounts"
          },
          "additions": [
            {
              "internal_id": "string",
              "title": "string"
            }
          ],
          "paid_in_bonuses": "boolean",
          "promo": {
            "promo_id": "integer",
            "promo_title": "string"
          },
          "promo_code": {
            "promo_code_id": "integer",
            "promo_code_value": "string"
          }
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
        "address_level": "string",
        "address_entrance": "string",
        "address_apt": "string",
        "address_home": "string",
        "address_street": "string",
        "address_city": "string",
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

Payment statuses:

| Payment Status      | Description                                                                                                 |
|---------------------|-------------------------------------------------------------------------------------------------------------|
| paid                | Payment by card has been successfully done                                                                  |

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

Brand:

| Source Type | Description                         |
|-------------|-------------------------------------|
| cibosano    | Order has been placed for Cibo Sano |
| meteor      | Order has been placed for Meteor    |

### Example:
##### Request
`GET /internal_api/orders.json`

##### Response

```json
{
  "orders": [
    {
      "id": "7d424e65-3309-4064-a7d3-0c3da24b22a3",
      "created_at": "2022-03-05T17:50:13.513+06:00",
      "status": "created",
      "payment_status": "paid",
      "payment_method": "card",
      "source_type": "web",
      "comment": "Do not call me!!!",
      "change": "",
      "brand": "cibosano",
      "products": [
        {
          "internal_id": "internal_448_2",
          "title": "Маргарита",
          "quantity": 1,
          "price": {
            "base_for_one": "2600.00",
            "base_total": "3150.00"
          },
          "additions": [
            {
              "internal_id": "internal_0_0",
              "title": "Салями"
            },
            {
              "internal_id": "internal_486_0",
              "title": "Оливки"
            }
          ],
          "promo": {
            "promo_id": 12,
            "promo_title": "Первый заказ через мобильное приложение"
          },
          "promo_code": {
            "promo_code_id": 5,
            "promo_code_value": "Cibo2022"
          }
        },
        {
          "internal_id": "internal_195_0",
          "title": "Грибная",
          "quantity": 2,
          "price": {
            "base_for_one": "1850.00",
            "base_total": "4000.00"
          },
          "additions": [
            {
              "internal_id": "internal_0_0",
              "title": "Салями"
            }
          ]
        },
        {
          "internal_id": "internal_143_0",
          "quantity": 1,
          "paid_in_bonuses": true,
          "price": {
            "base_for_one": "0.00",
            "base_total": "0.00"
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
        "datetime": null,
        "address_level": "",
        "address_entrance": "",
        "address_apt": "123",
        "address_home": "149",
        "address_street": "жилой комплекс Клубный дом на Чайковского",
        "address_city": "Алматы",
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
      "id": "cdb3d536-92d6-4eb9-8840-1b2ad164b4ce",
      "created_at": "2022-03-05T17:50:32.148+06:00",
      "status": "created",
      "payment_status": "paid",
      "payment_method": "cash",
      "source_type": "mobile",
      "comment": "",
      "change": "2500",
      "brand": "meteor",
      "products": [
        {
          "internal_id": "internal_448_0",
          "title": "Маргарита",
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
        "datetime": "14:30 05:03:22",
        "address_level": "",
        "address_entrance": "",
        "address_apt": "23",
        "address_home": "54А",
        "address_street": "улица Досмухамедова",
        "address_city": "Алматы",
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



