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

<spoiler>
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
            
				{
					"Sku": {
						"LocalizedProperties": [
							{
								"SkuDescription": "Download Candy Crush Soda Saga now!\r\n\r\nFrom the makers of the legendary Candy Crush Saga comes Candy Crush Soda Saga! Unique candies, more divine matching combinations and challenging game modes brimming with purple soda and fun!\r\n\r\nThis mouth-watering puzzle adventure will instantly quench your thirst for fun. Join Kimmy on her juicy journey to find Tiffi, by switching and matching your way through new dimensions of magical gameplay. Take on this Sodalicious Saga alone or play with friends to see who can get the highest score!\r\n\r\nMonthly season updates bring unique quests and exciting gameplay for you to explore! Complete quests to progress through the Season Pass while earning rewards and boosters to help you on your Saga.\r\n\r\nShow your competitive side in the Episode Race! Compete against other players to see who can complete levels the fastest and progress the quickest. Or work as a team in the 4 in a Row game mode where players work together for Sodalicious rewards!\r\n\r\nCandy Crush Soda Saga Features:\r\n\r\n*Over 6000 match 3 Sodalicious levels\r\n\r\n*Mouth-watering graphics, with 3D characters and an ever changing environment\r\n\r\n*Monthly Seasons all year long, filled with challenging quests and a reward-fueled Season Pass\r\n\r\n*Game modes bubbling with fun and unique candy:\r\n\r\nSoda – Switch the bottles and match candies to release purple soda and save the Candy Bears\r\n\r\nFrosting – Match candy to smash the ice and set the Candy Bears free\r\n\r\nHoneycomb – Match candies next to honeycomb to release the trapped Candy Bears\r\n\r\nJam – Spread the jam across the board\r\n\r\n*Unique candies and scrumptious new matching combinations:\r\n\r\nMatch 4 candies in a square to make a Swedish Fish!\r\n\r\nMatch 7 candies for the all new Coloring Candy!\r\n\r\n*Explore juicy worlds and levels with even more characters!\r\n\r\n*Team up for tasty rewards in the 4 in a Row game mode \r\n\r\n*Complete levels in the fastest time for sweet prizes in the Episode Race!\r\n\r\n*Easy and fun to play, yet challenging to fully master\r\n\r\n*Players that Facebook Connect will have access to leaderboards where you can challenge your friends and compare your highscores!\r\n\r\n*Easily sync the game between devices to unlock the games full features when connected to the internet\r\n\r\nCandy Crush Soda Saga is completely free to play, but some in-game items such as extra moves or lives will require payment.\r\n\r\nBy downloading this game you are agreeing to our terms of service; http://about.king.com/consumer-terms/terms\r\n\r\nDo not sell my data: King shares your personal information with advertising partners to personalize ads. Learn more at https://king.com/privacyPolicy. If you wish to exercise your Do Not Sell My Data rights, you can do so by contacting us via the in game help centre or by going to https://soporto.king.com/\r\n\r\nFacebook @CandyCrushSodaSaga\r\n\r\nTwitter @CandyCrushSoda\r\n\r\nInstagram @CandyCrushSaga\r\n\r\nYouTube @CandyCrushOfficial\r\n\r\nLast but not least, a big THANK YOU goes out to everyone who has played Candy Crush Soda Saga!",
								"SkuTitle": "Candy Crush Soda Saga",
								"SkuButtonTitle": "",
								"SkuDisplayRank": [],
								"LegalText": {
									"Copyright": "© 2015 King.com Ltd. \"King\", \"Candy Crush Soda Saga\" and associated marks and logos are trademarks of King.com Ltd or related entities. ",
									"CopyrightUri": "",
									"PrivacyPolicy": "",
									"PrivacyPolicyUri": "https://king.com/privacyPolicy",
									"Tou": "By downloading this game you are agreeing to our terms of service; http://about.king.com/consumer-terms/terms",
									"TouUri": ""
								},
								"Language": "en-us"
							}
						],
						"Properties": {
							"FulfillmentType": null,
							"BundledSkus": [],
							"IsRepurchasable": false,
							"SkuDisplayRank": 0,
							"IsTrial": false
						},
						"SkuId": "0010",
						"RecurrencePolicy": null,
						"DisplayProperties": {
							"IsPreOrder": false
						}
					},
					"Availabilities": [
						{
							"Actions": [
								"Details",
								"Fulfill",
								"Purchase",
								"Browse",
								"Curate",
								"Redeem"
							],
							"AvailabilityId": "9W3DNZ9G7MM9",
							"Conditions": {
								"EndDate": "9998-12-30T00:00:00Z"
							},
							"OrderManagementData": {
								"Price": {
									"CurrencyCode": "USD",
									"ListPrice": 0.0,
									"MSRP": 0.0,
									"StrikethroughPrice": "$0.00",
									"DisplayPrice": "$0.00"
								}
							},
							"DisplayRank": 0,
							"RemediationRequired": false
						},
						{
							"Actions": [
								"License",
								"Browse",
								"Details"
							],
							"AvailabilityId": "B2SR7JTT9RNR",
							"Conditions": {
								"EndDate": "9998-12-30T00:00:00Z"
							},
							"DisplayRank": 1,
							"RemediationRequired": false
						},
						{
							"Actions": [
								"License",
								"Details"
							],
							"AvailabilityId": "B16WRDJ2D4QK",
							"Conditions": {
								"EndDate": "9998-12-30T00:00:00Z"
							},
							"DisplayRank": 2,
							"RemediationRequired": false
						}
					]
				},
				{
					"Sku": {
						"LocalizedProperties": [
							{
								"SkuDescription": "Download Candy Crush Soda Saga now!\r\n\r\nFrom the makers of the legendary Candy Crush Saga comes Candy Crush Soda Saga! Unique candies, more divine matching combinations and challenging game modes brimming with purple soda and fun!\r\n\r\nThis mouth-watering puzzle adventure will instantly quench your thirst for fun. Join Kimmy on her juicy journey to find Tiffi, by switching and matching your way through new dimensions of magical gameplay. Take on this Sodalicious Saga alone or play with friends to see who can get the highest score!\r\n\r\nMonthly season updates bring unique quests and exciting gameplay for you to explore! Complete quests to progress through the Season Pass while earning rewards and boosters to help you on your Saga.\r\n\r\nShow your competitive side in the Episode Race! Compete against other players to see who can complete levels the fastest and progress the quickest. Or work as a team in the 4 in a Row game mode where players work together for Sodalicious rewards!\r\n\r\nCandy Crush Soda Saga Features:\r\n\r\n*Over 6000 match 3 Sodalicious levels\r\n\r\n*Mouth-watering graphics, with 3D characters and an ever changing environment\r\n\r\n*Monthly Seasons all year long, filled with challenging quests and a reward-fueled Season Pass\r\n\r\n*Game modes bubbling with fun and unique candy:\r\n\r\nSoda – Switch the bottles and match candies to release purple soda and save the Candy Bears\r\n\r\nFrosting – Match candy to smash the ice and set the Candy Bears free\r\n\r\nHoneycomb – Match candies next to honeycomb to release the trapped Candy Bears\r\n\r\nJam – Spread the jam across the board\r\n\r\n*Unique candies and scrumptious new matching combinations:\r\n\r\nMatch 4 candies in a square to make a Swedish Fish!\r\n\r\nMatch 7 candies for the all new Coloring Candy!\r\n\r\n*Explore juicy worlds and levels with even more characters!\r\n\r\n*Team up for tasty rewards in the 4 in a Row game mode \r\n\r\n*Complete levels in the fastest time for sweet prizes in the Episode Race!\r\n\r\n*Easy and fun to play, yet challenging to fully master\r\n\r\n*Players that Facebook Connect will have access to leaderboards where you can challenge your friends and compare your highscores!\r\n\r\n*Easily sync the game between devices to unlock the games full features when connected to the internet\r\n\r\nCandy Crush Soda Saga is completely free to play, but some in-game items such as extra moves or lives will require payment.\r\n\r\nBy downloading this game you are agreeing to our terms of service; http://about.king.com/consumer-terms/terms\r\n\r\nDo not sell my data: King shares your personal information with advertising partners to personalize ads. Learn more at https://king.com/privacyPolicy. If you wish to exercise your Do Not Sell My Data rights, you can do so by contacting us via the in game help centre or by going to https://soporto.king.com/\r\n\r\nFacebook @CandyCrushSodaSaga\r\n\r\nTwitter @CandyCrushSoda\r\n\r\nInstagram @CandyCrushSaga\r\n\r\nYouTube @CandyCrushOfficial\r\n\r\nLast but not least, a big THANK YOU goes out to everyone who has played Candy Crush Soda Saga!",
								"SkuTitle": "Candy Crush Soda Saga",
								"SkuButtonTitle": "",
								"SkuDisplayRank": [],
								"LegalText": {
									"Copyright": "© 2015 King.com Ltd. \"King\", \"Candy Crush Soda Saga\" and associated marks and logos are trademarks of King.com Ltd or related entities. ",
									"CopyrightUri": "",
									"PrivacyPolicy": "",
									"PrivacyPolicyUri": "https://king.com/privacyPolicy",
									"Tou": "By downloading this game you are agreeing to our terms of service; http://about.king.com/consumer-terms/terms",
									"TouUri": ""
								},
								"Language": "en-us"
							}
						],
						"Properties": {
							"FulfillmentType": null,
							"BundledSkus": [],
							"IsRepurchasable": false,
							"SkuDisplayRank": 2,
							"IsTrial": true
						},
						"SkuId": "0011",
						"RecurrencePolicy": null,
						"DisplayProperties": {
							"IsPreOrder": false
						}
					},
					"Availabilities": [
						{
							"Actions": [
								"Details",
								"License",
								"Fulfill"
							],
							"AvailabilityId": "9WCFTHZ1653K",
							"Conditions": {
								"EndDate": "9998-12-30T00:00:00Z"
							},
							"DisplayRank": 0,
							"RemediationRequired": false
						},
						{
							"Actions": [
								"License",
								"Details"
							],
							"AvailabilityId": "9WT2W98RQV04",
							"Conditions": {
								"EndDate": "9998-12-30T00:00:00Z"
							},
							"DisplayRank": 1,
							"RemediationRequired": false
						}
					]
				}
			],
			"AverageRating": /*<RATING IN NUMBER OF STARS (1 decimal place)>*/,
			"TotalRatingsCount": /*<NUMBER OF RATINGS>*/
        }
    ]
}
```
</spoiler>

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