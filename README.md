# Macys Documentation

## Introduction

**Unofficial Macys API** helps to query for all information about products,categories, events, etc… as on the official website.

## Authentication

The URL you need to use is the following: `https://macys4.p.rapidapi.com/api/`
The API requires the headers listed below:

- **`x-rapidapi-host`**: `macys4.p.rapidapi.com`
- **`x-rapidapi-key`**: `YOUR_API_KEY`

Make sure to replace `YOUR_API_KEY` with your API key. You can register one [here](https://rapidapi.com/belchiorarkad-FqvHs2EDOtP/api/macys4/pricing).
Some frameworks automatically add extra headers, you have to make sure to remove them in order to get a response from the API.

## Endpoints

The API is configured to accept only **GET** requests. Below are the available endpoints with their descriptions and required parameters.

### 1. **`GET /products/:productId`**

- **Description**: Retrieves detailed information about a specific product.

| Path Parameter | Type   | Default | Description                             | Required |
|----------------|--------|---------|-----------------------------------------|----------|
| `productId`    | string | -       | The ID of the product                   | Yes      |

| Query Parameter | Type   | Default | Description                            | Required |
|-----------------|--------|---------|----------------------------------------|----------|
| `currencyCode`  | string | `USD`   | The currency code                      | No       |
| `regionCode`    | string | `US`    | The region code                        | No       |

Example request:

```javascript
fetch('https://macys4.p.rapidapi.com/api/products/17342121', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'macys4.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
[
  {
    "id": 17342121,
    "identifier": {
      "productUrl": "/shop/product/dior-2-pc.-miss-dior-eau-de-parfum-gift-set?ID=17342121",
      "productId": 17342121,
      "topLevelCategoryID": "669",
      "topLevelCategoryName": "Beauty"
    },
    "department": {
      "departmentId": 647,
      "departmentName": "DIOR WOMENS FRAGRANCES"
    },
    "messages": {
      "info": [
        {}
      ]
    },
    "detail": {
      "name": "2-Pc. Miss Dior Eau de Parfum Gift Set",
      "description": "This limited-edition Miss Dior gift set features two sizes of the Eau de Parfum, presented in a couture and floral-inspired design.",
      "secondaryDescription": "",
      "seoKeywords": "DIOR, Dior 2-Pc. Miss Dior Eau de Parfum Gift Set",
      "flags": {
        "chanel": false,
        "hermes": false,
        "coach": false,
        "hasWarranty": false,
        "bigTicketItem": false,
        "phoneOnly": false,
        ...
```

### 2. **`GET /search/product`**

- **Description**: Searches for products using a keyword.

| Query Parameter | Type   | Default | Description                            | Required |
|-----------------|--------|---------|----------------------------------------|----------|
| `q`             | string | -       | The search keyword                     | Yes      |
| `currencyCode`  | string | `USD`   | The currency code                      | No       |
| `regionCode`    | string | `US`    | The region code                        | No       |
| `perPage`       | string | `20`    | Number of products per page            | No       |
| `pageIndex`     | string | `1`     | The page number for pagination         | No       |

Example request:

```javascript
fetch('https://macys4.p.rapidapi.com/api/search/product/?q=Miss%20Dior&perPage=12&pageIndex=2', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'macys4.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "result": [
    {
      "product": {
        "id": 18735808,
        "identifier": {
          "productUrl": "/shop/product/dior-mens-2-pc.-sauvage-eau-de-toilette-limited-edition-gift-set?ID=18735808&isDlp=true",
          "productId": 18735808
        },
        "detail": {
          "name": "Men's 2-Pc. Sauvage Eau de Toilette Limited-Edition Gift Set",
          "brand": "DIOR",
          "flags": {
            "registrable": true,
            "intlSuppressProduct": true,
            "PDPColorized": true,
            "isNew": true
          },
          "reviewStatistics": {
            "aggregate": {
              "rating": 5,
              "count": 1
            }
          },
          "typeName": "FRAGRANCE"
        },
        "relationships": {
          "taxonomy": {
            "defaultCategoryId": 30088
          }
          ...
```

### 3. **`GET /products/:productId/reviews`**

- **Description**: Retrieves reviews for a specific product.

| Path Parameter | Type   | Default | Description                             | Required |
|----------------|--------|---------|-----------------------------------------|----------|
| `productId`    | string | -       | The ID of the product                   | Yes      |

| Query Parameter | Type   | Default | Description                            | Required |
|-----------------|--------|---------|----------------------------------------|----------|
| `currencyCode`  | string | `USD`   | The currency code                      | No       |
| `regionCode`    | string | `US`    | The region code                        | No       |
| `limit`         | string | `50`    | The number of reviews to retrieve      | No       |
| `withImage`     | string | `false` | Filter to include reviews with images  | No       |

Example request:

```javascript
fetch('https://macys4.p.rapidapi.com/api/products/17342121/reviews', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'macys4.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "review": {
    "hasErrors": false,
    "includes": {
      "products": {
        "12661369": {
          "name": "Dior Miss Dior Eau de Parfum Fragrance Collection",
          "productId": 12661369,
          "description": "Miss Dior's New Eau De Parfum is a couture dream––a multi-colored perfume for women in a reinvented bottle adorned by an exceptional bow. The new Miss ...",
          "imageUrl": "https://slimages.macysassets.com/is/image/MCY/products/5/optimized/20314385_jpg.tif?bgc=255,255,255&wid=134&qlt=90,0&layer=comp&op_sharpen=0&resMode=bicub&op_usm=0.7,1.0,0.5,0&fmt=jpeg",
          "productPageUrl": "https://www.macys.com/shop/product/dior-miss-dior-eau-de-parfum-fragrance-collection?ID=12661369&CategoryID=30087",
          "reviewStatistics": {
            "averageOverallRating": 4.7,
            "ratingPercentage": 94,
            "overallRatingRange": 5,
            "ratingDistribution": [
              {
                "count": 14239,
                "ratingValue": 5
              },
              {
                "count": 2279,
                "ratingValue": 4
              },
              {
                "count": 741,
                "ratingValue": 3
              },
              {
                "count": 226,
                ...
```

### 4. **`GET /product/all`**

- **Description**: Retrieves products with pagination.

| Query Parameter | Type   | Default | Description                                          | Required |
|-----------------|--------|---------|------------------------------------------------------|----------|
| `page`          | string | `1`     | The page number of results to retrieve products from | No       |
| `perPage`       | string | `10`    | The number of products per page                      | No       |

Example request:

```javascript
fetch('https://macys4.p.rapidapi.com/api/product/all', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'macys4.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "status": "sucess",
  "products": {
    "0": {
      "product_id": "19345687",
      "name": "Scotch & Soda Men's Reversible Jacquard Jacket - Geo Tulip",
      "description": "Whether you're feeling laid back in jeans or you want a dressier look, this jacket from Scotch & Soda is the perfect companion. With its reversible design, you can effortlessly switch between bold patterning and subtle elegance.",
      "price": 318,
      "price_deal": 222.6,
      "price_old": 0,
      "deal_start_date": null,
      "deal_end_date": null,
      "available": 1,
      "gender": null,
      "min_age": null,
      "max_age": null,
      "retailer_sku": "8721051016391",
      "arrival_date": null,
      "country": "",
      "brand": null,
      "vanity_data": "",
      "deal_ratio": 70,
      "name2": "Scotch & Soda",
      "sku": "19345687",
      "shortDescription": "Whether you're feeling laid back in jeans or you want a dressier look, this jacket from Scotch & Soda is the perfect companion. With its reversible design, you can effortlessly switch between bold patterning and subtle elegance.",
      "regularPrice": 318,
      "salePrice": 222.6,
      "oldPrice": 0,
      "productUrl": "https://www.macys.com/shop/product/scotch-soda-mens-reversible-jacquard-jacket?ID=19345687",
      "SaleEndDate": "",
      ...
```

### 5. **`GET /categories`**

- **Description**: Retrieves all categories.

| Query Parameter | Type   | Default | Description                                            | Required |
|-----------------|--------|---------|--------------------------------------------------------|----------|
| `page`          | string | `1`     | The page number of results to retrieve categories from | No       |
| `perPage`       | string | `20`    | The number of products per page                        | No       |

Example request:

```javascript
fetch('https://macys4.p.rapidapi.com/api/categories', {
  method: 'GET',
  headers: {
    'x-rapidapi-host': 'macys4.p.rapidapi.com',
    'x-rapidapi-key': 'API_KEY' // Replace 'API_KEY' with your API key
  }
})
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

Example response:

```json
{
  "0": {
    "name": "Sofas",
    "category_id": "be-sofas2"
  },
  "1": {
    "name": "Watches",
    "category_id": "be-watches2"
  },
  "2": {
    "name": "Beauty",
    "category_id": "Beauty"
  },
  "3": {
    "name": "Baby & Toddler Accessories",
    "category_id": "ho-baby-clothing-accessories2"
  },
  "4": {
    "name": "Backpacks",
    "category_id": "ho-backpacks2"
  },
  "5": {
    "name": "Barware",
    "category_id": "ho-barware2"
  },
  "6": {
    "name": "BASE",
    "category_id": "ho-base2"
  },
  "7": {
    ...
```

## Error Handling

The  API returns standard HTTP status codes to indicate the success or failure of API requests. Below are common errors and suggestions for handling them.

|Status Code|Message|Description|Suggested Handling|
|--|--|--|--|
| **400** | Bad Request | The request was malformed or missing required parameters (e.g., `domain` parameter not provided). | Verify that all required parameters are included and correctly formatted. |
| **401** | Unauthorized | Invalid or missing API key in the request headers. | Check that a valid API key is included in `x-rapidapi-key`. |
| **403** | Forbidden | Access to the requested resource is denied, possibly due to rate limits or restricted access. | Review rate limits and ensure API permissions. Retry after a delay if rate limit exceeded. |
| **404** | Not Found | The requested domain information could not be found (e.g., domain does not exist). | Check the spelling or availability of the domain. |
| **429** | Too Many Requests | The API rate limit has been exceeded. | Implement rate-limiting logic and retry after the specified rate limit reset time. |
| **500** | Internal Server Error | A server error occurred while processing the request. | Retry the request after a few seconds. If the error persists, contact API support. |
| **503** | Service Unavailable | The API service is temporarily unavailable (e.g., due to maintenance). | Retry the request later or check the API status page for maintenance alerts. |
