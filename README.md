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