# MS-Store-API
## Trying to figure out the Microsoft Store API

Currently there's no publicly documented API for accessing products (including Apps, Games) available in the Microsoft Store.
With the release of the product [badge tool for the Microsoft Store](https://blogs.windows.com/buildingapps/2018/05/18/a-new-product-badge-for-microsoft-store-applications/) I found a publicly accessible API endpoint that allows you to retreive product information by ID (and more?).

## Get product information

* [v8.0/sdk](endpoints/v8.0/products.md)

## Search for a product

`GET`
`https://storeedgefd.dsx.mp.microsoft.com/v9.0/pages/searchResults?appVersion=22203.1401.0.0&market=US&locale=en-US&deviceFamily=windows.desktop&query=calculator`

### URL Parameters

- `market` - Region in the form of a country code
- `locale` - Language for response
- `deviceFamily` - What device to base response on
- `query` - What to search for

### Response format

```jsonc
[
  {}, // Metadata
  {
    "$type": "Microsoft.Marketplace.Storefront.Contracts.V1.ResponseItem, Microsoft.Marketplace.Storefront.Contracts",
    
    "Payload": {
      "$type": "Microsoft.Marketplace.Storefront.Contracts.V9.SearchResponse, Microsoft.Marketplace.Storefront.Contracts",
      
      "SearchResults": [
        {
          "$type": "Microsoft.Marketplace.Storefront.Contracts.V8.One.CardModel, Microsoft.Marketplace.Storefront.Contracts",
          
          "ProductId": "<PRODUCT ID>",
          "Title": "<PRODUCT NAME/TITLE>",
          "Images": [ /*...*/ ],
          "PackageFamilyNames": ["<PACKAGE FAMILY NAME>"],
          "Price": /*<PRICE>*/
        }
      ]
    }
  }
]
```

# References
- https://docs.microsoft.com/de-de/windows/privacy/manage-windows-endpoints#microsoft-store
- https://blogs.windows.com/buildingapps/2018/05/18/a-new-product-badge-for-microsoft-store-applications/#wxXtV2V8lebI1R4W.97
- http://displaycatalog.mp.microsoft.com/
- pti.store.microsoft.com
