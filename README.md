# OfferMarket API

### Context
 * This documentation is intended to help you integrate Mobrand's OfferMarket API.
 * You will find instructions on how to read all the offers available to you and make requests to get them approved.

###### Note: If you are an Account Manager and you are reading this, please do not be scared and pass it to a tech guy as they will for sure understand it.


## Get All offers
 * This Endpoint will only respond to GET.
 * All responses are in JSON.
 * Single Request. Paging not available.

| Field | Type | value |
|-|-|-|
|   url  | string | https://api.mobrand.net/{YOURUSERID}/bulk/offermarket/v1?apikey={YOURAPIKEY} |
| userid | String | {YOURUSERID} |
| apiKey | String | {YOURAPIKEY} |

#### Query Filters
| Field | Type | value | Required | Default |
|-|-|-|-|-|
| offerType | String | "cpi" , "cpa" or "cpl"  | No | "all" |

#### Example Url:
``` https://api.mobrand.net/{YOURUSERID}/bulk/offermarket/v1?apikey={YOURAPIKEY}&offerType="all" ```

### Response
#### Example Response:
```
[
    {
        "offerId":"KycyJDY4IjlxKjg2KzYaGwISDQIB",
        "numericId":1887,
        "title":"Olymp Trade - Mobile Trading",
        "iconUrl":"https://is5-ssl.mzstatic.com/image/thumb/Purple124/v4/b5/bc/16/b5bc1613-d8eb-1c53-7ffe-9d15d3695bb6/source/512x512bb.jpg",
        "previewUrl":"",
        "screenshots":[
            "https://is4-ssl.mzstatic.com/image/thumb/Purple124/v4/65/b6/0b/65b60b15-1d35-2f0a-02b5-10b406f9c281/pr_source.png/392x696bb.png",
            "https://is5-ssl.mzstatic.com/image/thumb/Purple114/v4/b6/e1/a4/b6e1a4ec-4d5a-7ec9-c8db-a1f1cae44632/pr_source.png/392x696bb.png",
            "https://is3-ssl.mzstatic.com/image/thumb/Purple114/v4/f2/39/02/f239028d-37b3-2710-f0a2-7a6256bef616/pr_source.png/392x696bb.png"
        ],
        "currency":"USD",
        "directOfferLink":"",
        "description":"description example",
        "notes":"notes example",
        "creativesURL": "https://api.mobrand.net/offermarket/creatives/1887.zip",
        "restrictions":[
            "No adult",
            "No incent",
            "No bot",
            "No misleading",
            "No desktop",
            "No iframe",
            "No auto sub",
            "No in-app"
        ],
        "kpi":[
            "CR: 0.03 - 0.05",
            "Install to registration 15%",
            "registration to purchase - 3%",
            "",
            "Billable event: FTD(purchase)"
        ],
        "details":{
            "payouts":[
                {
                    "payout":68.8,
                    "geos":[
                        "ID"
                    ],
                    "carriers":[]
                }
            ],
            "platforms":[
                "IOS"
            ],
            "capping":"",
            "device":"Multi",
            "flow":"Install + Register + FTD($)"
        },
        "status":null,
        "bundleID":"1053416106",
        "category":"Finance",
        "subCategory":"APPS",
        "type":"",
        "offerType":"cpi",
        "ts":1595412608139
    },
    {
        "offerId":"PTMkPDE9IGgmJDArLzUqPBIIHRgaICYjNHQ",
        "numericId":1889,
        "title":"ASHLEY MADISON: Life Is Short.",
        "iconUrl":"https://is2-ssl.mzstatic.com/image/thumb/Purple123/v4/5c/22/84/5c228474-ea7d-bfd6-399c-7afc0613cf00/source/512x512bb.jpg",
        "previewUrl":"",
        "screenshots":[
            "https://is2-ssl.mzstatic.com/image/thumb/Purple124/v4/68/ac/cb/68accb59-bbdf-d0fa-d2f3-5852d6a96db0/pr_source.png/392x696bb.png",
            "https://is2-ssl.mzstatic.com/image/thumb/Purple114/v4/1b/8c/db/1b8cdbca-c2a9-c973-ba8d-03f09612c72b/pr_source.png/392x696bb.png"
        ],
        "currency":"USD",
        "directOfferLink": "https://t.offerlink.net/offermarket/tracker/PUB?offerId=1889",
        "description":"description example",
        "notes":"notes example",
        "creativesURL":null,
        "restrictions":[
            "No adult",
            "No incent",
            "No bot",
            "No misleading",
            "No desktop",
            "No iframe",
            "No auto sub",
            "No in-app"
        ],
        "kpi":[
            "Minimum 2% FP (First purchase) against # of installs required for payment less any reversals (Ex. Out of 100 installs, 2 FP's - screenshot explanations attached)",
            "Higher FTD % rate (Optimize towards this for more caps allocation)"
        ],
        "details":{
            "payouts":[
                {
                    "payout":116,
                    "geos":[
                        "DE",
                        "NL"
                    ],
                    "carriers":[
                    ]
                }
            ],
            "platforms":[
                "IOS"
            ],
            "capping":"capping": "Daily Cap 25",
            "device":"Multi",
            "flow":"Install + 1st Purchase"
        },
        "status": {
            "status": "APPROVED",
            "ts": 1595951291880
        },
        "bundleID":"359478823",
        "category":"Social Networking",
        "subCategory":"APPS",
        "type":"",
        "offerType":"cpi",
        "ts":1595413969616
    }
]
```
### Response description
| Field | Type | Description |
|-|-|-|
| offerType | String | "cpi" , "cpa" or "cpl" |
| status | Object | null if not approved |
| status-status | String | "APPROVED" , "PENDING" or "REJECTED" |
| directOfferLink | String | null if not approved |
| offerId | String | id used to make requests |
| payout | INTEGER | the payout in cents of "currency" |
| currency | String | currency of the payout |
| capping | String | "Monthly Cap","Daily Cap","Daily Budget","Monthly Budget"  followed by a number|



## Request Offers
 * This Endpoint will only respond to POST.

| Field | Type | value |
|-|-|-|
|   url  | string | https://api.mobrand.net/{YOURUSERID}/bulk/offermarket/request?apikey={YOURAPIKEY} |
| userid | String | {YOURUSERID} |
| apiKey | String | {YOURAPIKEY} |

#### Body Example:
###### Note: Should be offerId not numericId
```
[
    "offerId1",
    "offerId2",
    "offerId3"
]
```

### Response description

###### Note: Request changes status to "PENDING", offers will need to be approved by your AM
