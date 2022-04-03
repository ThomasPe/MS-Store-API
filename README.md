# MS-Store-API
## Trying to figure out the Microsoft Store API

Currently there's no publicly documented API for accessing products (including Apps, Games) available in the Microsoft Store.
With the release of the product [badge tool for the Microsoft Store](https://blogs.windows.com/buildingapps/2018/05/18/a-new-product-badge-for-microsoft-store-applications/) I found a publicly accessible API endpoint that allows you to retreive product information by ID (and more?).

## Base URL
`https://storeedgefd.dsx.mp.microsoft.com/v8.0/sdk/products`

## Get a single product
`POST`
`https://storeedgefd.dsx.mp.microsoft.com/v8.0/sdk/products?market=DE&locale=de-DE&deviceFamily=Windows.Desktop`

```
BODY
{productIds: "bwv5n56m5bvh"}
```

## Get multiple products

`POST`
`https://storeedgefd.dsx.mp.microsoft.com/v8.0/sdk/products?market=DE&locale=de-DE&deviceFamily=Windows.Desktop`

```
BODY
{productIds: "bwv5n56m5bvh,c1k748m3xp5d"}
``` 

### Response format

Simple documentation:

```jsonc
{
    "Products": [
        {
            "LocalizedProperties": [ // Holds a list of properties which may be localized to a language
                {
                    "DeveloperName": "Contoso", // The author of the product
                    "PublisherName": "Contoso", // The publisher of the product

                    "ProductDescription": "", // Description of the product
                    "ProductTitle": "Contoso IT Support", // Title of the app
                    "Language": "en-us" // Language of this localization
                }
            ],
            "ProductId": "XXXXXXXXXXXX", // The id of the product. Useful for other requests
            "Properties": {
                "PackageFamilyName": "contoso.com.ContosoItSupport_xxxxxxxxxxxxx" // The full package name of the product
            },
            "ProductKind": "Application", // What kind of product this is. May be "Game", "Application", or other.
            "DisplaySkuAvailabilities": [
                {
                    "Sku": {
                        "SkuId": "0010" // The id of the Sku. Not sure how it works. Have only seen it ever be "0010" or "0011".
                    }
                }
            ]
        }
    ]
}
```

<details>
<summary>Larger documentation (incomplete)</summary>

```jsonc
{
    "Products": [
        {
            "LocalizedProperties": [
                {
                    "DeveloperName": "<DEVELOPER NAME>",
                    "PublisherName": "<PUBLISHER NAME>",
                    "Images": [
                        {
                            "Caption": "<CAPTION>",
                            "Height": /*<HEIGHT>*/,
                            "ImagePurpose": "<Logo OR Tile>",
                            "Uri": "<IMAGE URI>" // The URI is in the format: //<host>/<path>, lacking the schema. HTTPS is assumed.
                        }
                    ],
                    "ProductDescription": "<DESCRIPTION>",
                    "ProductTitle": "<TITLE>",
                    "SearchTitles": [ // A list of search tags
                        {
                            "SearchTitleString": "<SEARCH RESULTS TAG>",
                            "SearchTitleType": "SearchHint"
                        },
                    ],
                    "Language": "<LANGUAGE>",
                    "ShortDescription": "<SHORT DESCRIPTION>"
                }
            ],
            "MarketProperties": [
                {
                    "RelatedProducts": [] // A list of related products
                }
            ],
            "ProductId": "<PRODUCT ID>",
            "Properties": {
                "PackageFamilyName": "<PACKAGE NAME>"
            },
            "ProductKind": "<Game OR App>",
            "DisplaySkuAvailabilities": [
                {
                    "Sku": {
                        "SkuId": "<SKU ID>"
                    }
                },
            ],
            "AverageRating": /*<RATING IN NUMBER OF STARS (1 decimal place)>*/,
            "TotalRatingsCount": /*<NUMBER OF RATINGS>*/
        }
    ]
}
```
</details>

## URL Parameters

- `market`
- `locale`
- `deviceFamily`

## Body Parameters
- `productIds`
- `parentProductId` (optional)

```
{productIds: "9n9zxm79mqr7", parentProductId: ""}
```



# References
- https://docs.microsoft.com/de-de/windows/privacy/manage-windows-endpoints#microsoft-store
- https://blogs.windows.com/buildingapps/2018/05/18/a-new-product-badge-for-microsoft-store-applications/#wxXtV2V8lebI1R4W.97
- http://displaycatalog.mp.microsoft.com/
- pti.store.microsoft.com