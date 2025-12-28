# JSON-ответ
Результаты распознавания документов сервер отправляет в виде json файла.
В каждом документе есть параметр `document_type`, содержащее тип документа, и объект `documents`, в котором хранятся все распознанные данные из этого документа.
## УПД
---

## Счёт-фактура
Для счёт-фактуры параметр `document_type` имеет значение `"invoice-doc"`.

Схема данных:
```json
{
    "documents": [
        {
            "document_type": "invoice-doc",
            "document": {
                "head": {
                    "number": "number",
                    "date": "date",
                    "correction_number": "number",
                    "correction_date": "date",
                    "seller": "string",
                    "seller_address": "string",
                    "seller_INN/KPP": "string",
                    "product_sender-and_his_adress": "string",
                    "product_recipient_and_his_adress": "string",
                    "number_to_payment_document": "number",
                    "date_to_payment_document": "date",
                    "buyer": "string",
                    "buyer_address": "string",
                    "buyer_INN/KPP": "string",
                    "currency_name": "string",
                    "currency_code": "number"
                },
                "products": [
                    {
                        "name": "string",
                        "code_unit_measurement": "number",
                        "name_unit_measurement": "string",
                        "quantity": "number",
                        "unit_price": "number",
                        "subtotal": "number",
                        "sum-excise": "number",
                        "tax_rate": "string",
                        "tax_sum": "number",
                        "subtotal_with_tax": "number",
                        "origin_country_code": "number",
                        "origin_country_name": "string",
                        "customs_declaration_number": "string"
                    }
                ],
                "total": {
                    "total_to_pay": "number",
                    "total_tax_to_pay": "number",
                    "total_with_tax_to_pay": "number"
                }
            }
        }
    ]
}
```
##### Список полей в шапке документа ("head")
| Название ключа                     | Тип данных | Описание                                  |
|------------------------------------|------------|-------------------------------------------|
| `number`                           | `number`   | Номер счёт-фактуры                        |
| `date`                             | `date`     | Дата                                      |
| `correction_number`                | `number`   | Номер исправления                         |
| `correction_date`                  | `date`     | Дата исправления                          |
| `seller`                           | `string`   | Продавец                                  |
| `seller_address`                   | `string`   | Адрес                                     |
| `seller_INN/KPP`                   | `string`   | ИНН/КПП продавца                          |
| `product_sender-and_his_adress`    | `string`   | Грузоотправитель и его адрес              |
| `product_recipient_and_his_adress` | `string`   | Грузополучатель и его адрес               |
| `number_to_payment_document`       | `number`   | К платежно-расчетному документу (номер)   |
| `date_to_payment_document`         | `date`     | К платежно-расчетному документу от (дата) |
| `buyer`                            | `string`   | Покупатель                                |
| `buyer_address`                    | `string`   | Адрес покупателя                          |
| `buyer_INN/KPP`                    | `string`   | ИНН/КПП покупателя                        |
| `currency_name`                    | `string`   | Валюта: наименование                      |
| `currency_code`                    | `number`   | Валюта: код                               |

##### Список полей в таблице товаров или услуг ("products")
| Название ключа               | Тип данных | Описание                                  |
|------------------------------|------------|-------------------------------------------|
| `name`                       | `string`   | Наименование товара                       |
| `code_unit_measurement`      | `number`   | Код единицы измерения                     |
| `name_unit_measurement`      | `string`   | Условное обозначение единицы измерения    |
| `quantity`                   | `number`   | Количество (объем)                        |
| `unit_price`                 | `number`   | Цена за единицу                           |
| `subtotal`                   | `number`   | Стоимость товаров без налога              |
| `sum-excise`                 | `number`   | В том числе сумма акциза                  |
| `tax_rate`                   | `string`   | Налоговая ставка                          |
| `tax_sum`                    | `number`   | Сумма налога для покупателя               |
| `subtotal_with_tax`          | `number`   | Стоимость товаров с налогом               |
| `origin_country_code`        | `number`   | Код страны происхождения                  |
| `origin_country_name`        | `string`   | Краткое наименование страны происхождения |
| `customs_declaration_number` | `string`   | Номер таможенной декларации               |

##### Список полей в блоке Итого ("total")

| Название ключа          | Тип данных | Описание                  |
|-------------------------|------------|---------------------------|
| `total_to_pay`          | `number`   | Всего к оплате без налога |
| `total_tax_to_pay`      | `number`   | Всего к оплате налога     |
| `total_with_tax_to_pay` | `number`   | Всего к оплате с налогом  |

{% cut "Пример" %}

```json
{
  "documents": [
    {
      "document_type": "invoice-doc",
      "document": {
        "head": {
          "number": 30248,
          "date": "2016-12-10",
          "correction_number": null,
          "correction_date": null,
          "seller": "ООО \"Конфетпром\"",
          "seller_address": "127434, Москва г, 1812 года ул, дом No 1",
          "seller_INN/KPP": "7799555550/779901001",
          "product_sender-and_his_adress": "он же",
          "product_recipient_and_his_adress": "адрес: ООО \"Торговый дом \"Комплексный\",121170, Москва г, Кутузовский пр-кт, дом No 1/7, строение 2",
          "number_to_payment_document": null,
          "date_to_payment_document": null,
          "buyer": "ООО \"Торговый дом \"Комплексный\"",
          "buyer_address": "121170, Москва г, Кутузовский пр-кт, дом No 1/7, строение 2",
          "buyer_INN/KPP": "7799434926/779901001",
          "currency_name": "Российский рубль",
          "currency_cod": 643
        },
        "products": [
          {
            "name": "",
            "code_unit_measurement": 796,
            "name_unit_measurement": "шт.",
            "quantity": 404000,
            "unit_price": 144.21,
            "subtotal": 58258.95,
            "sum-excise": null,
            "tax_rate": "18%",
            "tax_sum": 10486.61,
            "subtotal_with_tax": 6264.88,
            "origin_country_cod": 384,
            "origin_country_name": "КОТ Д'ИВУАР",
            "customs_declaration_number": "10001000/010216/0005897"
          },
          {
            "name": "",
            "code_unit_measurement": 796,
            "name_unit_measurement": "шт.",
            "quantity": 404000,
            "unit_price": 144.21,
            "subtotal": 58258.95,
            "sum-excise": null,
            "tax_rate": "18%",
            "tax_sum": 10486.61,
            "subtotal_with_tax": 6264.88,
            "origin_country_cod": 384,
            "origin_country_name": "КОТ Д'ИВУАР",
            "customs_declaration_number": "10001000/010216/0005897"
          }
        ],
        "total": {
          "total_to_pay": 72653.10,
          "total_tax_to_pay": 13077.56,
          "total_with_tax_to_pay": 85730.66
        }
      }
    }
  ]
}
```

{% endcut %}

## ТОРГ-12
---