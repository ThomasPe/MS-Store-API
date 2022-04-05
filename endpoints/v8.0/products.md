# /products endpoint

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

### URL Parameters

- `market`
- `locale`
- `deviceFamily`

### Body Parameters
- `productIds`
- `parentProductId` (optional)

```
{productIds: "9n9zxm79mqr7", parentProductId: ""}
```