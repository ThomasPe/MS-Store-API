# /pages endpoint

## Search for a product

`GET`
`https://storeedgefd.dsx.mp.microsoft.com/v9.0/pages/searchResults`

## Example

`GET`
`https://storeedgefd.dsx.mp.microsoft.com/v9.0/pages/searchResults?appVersion=22203.1401.0.0&market=US&locale=en-US&deviceFamily=windows.desktop&query=calculator`

## URL Parameters

- `market` - Region in the form of a country code
- `locale` - Language for response
- `deviceFamily` - What device to base response on
- `query` - What to search for

## Response format

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