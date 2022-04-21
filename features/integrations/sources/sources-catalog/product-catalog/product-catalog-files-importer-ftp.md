# Product catalog files importer (FTP)

You can import your product catalog through our file importer (FTP).

The file could contain the followed fields:

#### Properties <a href="#properties" id="properties"></a>

| Name               | Type                   | Required | Restrictions | Description                                                                                                                                                                                                                                               |
| ------------------ | ---------------------- | -------- | ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                 | string(1-50)           | true     | none         | Unique identifier for the article (try using the most specific identifier or SKU), such as a reference. If there are several occurrences for the same identifier, only the last one will be recorded                                                      |
| name               | string(1-500)          | false    | none         | Name of the article                                                                                                                                                                                                                                       |
| description        | string(max 5000 chars) | false    | none         | Description of the article                                                                                                                                                                                                                                |
| category\_1        | string(1-250)          | false    | none         | Main category of the article                                                                                                                                                                                                                              |
| category\_2        | string(1-250)          | false    | none         | Second sub-category of the article                                                                                                                                                                                                                        |
| category\_3        | string(1-250)          | false    | none         | Third sub-category of the article                                                                                                                                                                                                                         |
| category\_4        | string(1-250)          | false    | none         | Fourth sub-category of the article                                                                                                                                                                                                                        |
| category\_5        | string(1-250)          | false    | none         | Fifth sub-category of the article. If you have more than five levels of category you may choose to concatenate the remaining ones like 'Bikes/Parts/Wheels/Front' or simply ignore the remaining ones like 'Bikes', depending on your segmentation needs. |
| tags               | \[string]              | false    | none         | Array of tags for the product. Tags can be anything that labels the product: hand-made, eco-friendly, heat-resistant etc.                                                                                                                                 |
| condition          | string                 | false    | none         | Current status of the material in your store (see list of possible values below)                                                                                                                                                                          |
| availability       | string                 | false    | none         | Current availability of the item in your store. Make sure to indicate the availability of the item on your store page and keep it up to date (see list of possible values below)                                                                          |
| availability\_date | string(ISO-8601)       | false    | none         | Date when product became or will become available. See "Date formats" section above for a list of allowed formats.                                                                                                                                        |
| expiration\_date   | string(ISO-8601)       | false    | none         | Date when product became or will become unavailable. See "Date formats" section above for a list of allowed formats.                                                                                                                                      |
| price              | float                  | false    | none         | Default price for the article. In a conversion you can specify the real price at which the item was sold in case of sales, discounts etc.                                                                                                                 |
| sale\_price        | float                  | false    | none         | Default price for the article during sales periods. In a conversion you can specify the real price at which the item was sold in case of discounts                                                                                                        |
| currency           | string(ISO-4217)       | false    | none         | Currency used for given prices. Note that you have to use the same currency for products and conversions                                                                                                                                                  |
| image\_link        | string(url)            | false    | none         | URL of product image                                                                                                                                                                                                                                      |
| link               | string(url)            | false    | none         | URL to the website where you can buy the item                                                                                                                                                                                                             |
| brand              | string(1-250)          | false    | none         | Brand of the article                                                                                                                                                                                                                                      |
| width              | float                  | false    | none         | Width of the article in centimeters (cm)                                                                                                                                                                                                                  |
| length             | float                  | false    | none         | Length of the article in centimeters (cm)                                                                                                                                                                                                                 |
| height             | float                  | false    | none         | Height of the article in centimeters (cm)                                                                                                                                                                                                                 |
| weight             | float                  | false    | none         | Height of the article in centimeters (grams)                                                                                                                                                                                                              |
| size               | string(1-250)          | false    | none         | Size of the article when width, height and lengts are not applicable. You can use any value that describes the size. Examples: S, XL, large                                                                                                               |
| colors             | \[string]              | false    | none         | Colors of product                                                                                                                                                                                                                                         |
| gender             | string(1-250)          | false    | none         | Gender for gender specific products (male, female, unisex)                                                                                                                                                                                                |
| gtin               | string(1-250)          | false    | none         | International trade identification number of the article Supported numbers: UPC (North America, 12 digits), EAN (Europe, 13 digits), JAN (Japan, 8 to 13 digits), ISBN (books, 13 digits)                                                                 |
| mpn                | string(1-250)          | false    | none         | Manufacturer part number of the material                                                                                                                                                                                                                  |
| custom             | object                 | false    | none         | Object containing custom properties                                                                                                                                                                                                                       |

**Enumerated Values**

| Property     | Value          |
| ------------ | -------------- |
| condition    | new            |
| condition    | refurbished    |
| condition    | used           |
| availability | in\_stock      |
| availability | available      |
| availability | pre\_order     |
| availability | out\_of\_stock |
| gender       | male           |
| gender       | female         |
| gender       | unisex         |
