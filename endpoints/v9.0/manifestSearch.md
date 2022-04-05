# /manifestSearch endpoint

## Search for a product

`POST`
`https://storeedgefd.dsx.mp.microsoft.com/v9.0/manifestSearch`

## Example

`POST`
`https://storeedgefd.dsx.mp.microsoft.com/v9.0/manifestSearch`

### Body

```jsonc
{
	"Query": {
		"KeyWord": "calculator",
		"MatchType": "Substring"
	}
}
```

## Request Body

```jsonc
{
	"Query": {
		"KeyWord": "<SEARCH_QUERY>", // What you want to search for
		"MatchType": "Substring" // Search method
	}
}
```

## Response format

```jsonc
{
	"$type": "Microsoft.Marketplace.Storefront.StoreEdgeFD.BusinessLogic.Response.ManifestSearch.ManifestSearchResponse, StoreEdgeFD",

	"Data": [
		{
			"$type": "Microsoft.Marketplace.Storefront.StoreEdgeFD.BusinessLogic.Response.ManifestSearch.ManifestSearchData, StoreEdgeFD",

			"PackageIdentifier": "<PRODUCT ID>", // Id of the product
			"PackageName": "<PACKAGE NAME>", // Name of the package
			"Publisher": "<PUBLISHER>", // Publisher
			"Versions": [
				{
					"$type": "Microsoft.Marketplace.Storefront.StoreEdgeFD.BusinessLogic.Response.ManifestSearch.ManifestSearchVersion, StoreEdgeFD",

					"PackageVersion": "Unknown", // Version
					"PackageFamilyNames": [
						"<PACKAGE FULL NAME>" // Package full name
					]
				}
			]
		},
	]
}
```