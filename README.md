# Actor - Pinterest Scraper

## Pinterest scraper

The Pinterest data scraper supports the following features:

-   Retrieve pin information - Get all the information per each pin. User information, videos, images, price, language and many other things!

-   Scrape comments - Harvest all the comments without any limits! Get users, comments and all the necessary information that you are looking for.

-   Get ideas - Fetch all the pins on an idea link.

-   Scrape user profile and user pins - Track any user and their pins. As easy as clicking a button.

-   Get collections - Want to get all the pins of a collection? Do it with ease with Pinterest Scraper!

-   Search and get any keyword results - Search any keyword you want and retrieve all the results right away.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/pinterest-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Pinterest that should be visited. Required fields are:

| Field                | Type    | Description                                                                                                                                                                                                    |
| -------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| startUrls | Array | (optional) List of Pinterest URLs. You should only provide pin detail, ideas, user profile, collection or search URLs |
| search               | String  | (optional) Keyword that you want to search on Pinterest.                                                                                                                                                       |
| includeComments       | Boolean | (optional) This will add all the comments that Pinterest provides into the pin objects. Please keep in mind that the time and resources the actor uses will increase proportionally by the number of reviews. |
| endPage              | Integer | (optional) Final number of page that you want to scrape. Default is `Infinite`. This is applies to all `search` request and `startUrls` individually.                                                          |
| maxItems             | Integer | (optional) You can limit scraped pins. This should be useful when you search through the big lists or search results.                                                                                                |
| proxy                | Object  | Proxy configuration                                                                                                                                                                                            |
| extendOutputFunction | String  | (optional) Function that takes a JQuery handle ($) as argument and returns object with data                                                                                                                    |
| customMapFunction | String  | (optional) Function that takes each objects handle as argument and returns object with executing the function                                                                                                                     |

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

##### Tip

When you want to have a scrape over a specific list URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all the detail requests. If actor doesn't block very often it'll scrape 100 listings in 1 minute with ~0.01-0.02 compute units.

### Pinterest Scraper Input example

```json
{
  "startUrls":[
    "https://www.pinterest.com/pin/1054827543951238554/",
    "https://www.pinterest.com/ideas/beauty/935541271955/",
    "https://www.pinterest.com/dudadelsanto/",
    "https://www.pinterest.com/dudadelsanto/nail-inspo/",
    "https://www.pinterest.com/search/pins/?q=Valentine%E2%80%99s%20Nail%20Art&rs=hub_page"
  ],
  "proxy":{
    "useApifyProxy":true
  },
  "search":"design",
  "endPage":1,
  "maxItems":10,
  "includeComments":false
}

```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Pinterest Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Pinterest actor.

## Scraped Pinterest Properties

The structure of each pin in Pinterest looks like this:

### Pin Detail

```json
{
	"type": "pin",
	"url": "https://www.pinterest.com/pin/672584525610478245",
	"access": [],
	"aggregated_pin_data": {
		"id": "5177796853051209185",
		"aggregated_stats": {
			"saves": 1454,
			"done": 0
		},
		"comment_count": 0,
		"is_shop_the_look": false
	},
	"alt_text": null,
	"attribution": null,
	"board": {
		"category": null,
		"id": "672584594289335576",
		"image_cover_url": "https://i.pinimg.com/200x150/61/ff/b5/61ffb537b37630b8a4eb1d8a301839c8.jpg",
		"map_id": "pinterest.ijz1714i",
		"owner": {
			"id": "672584663008554825",
			"image_medium_url": "https://i.pinimg.com/75x75_RS/3d/34/8d/3d348dde519fe850f2aa7b5d717ced10.jpg",
			"followed_by_me": false,
			"full_name": "maria eduarda",
			"indexed": true,
			"type": "user",
			"domain_verified": false,
			"follower_count": 11680,
			"username": "dudadelsanto",
			"is_ads_only_profile": false,
			"domain_url": null,
			"explicitly_followed_by_me": false,
			"blocked_by_me": false,
			"first_name": "maria eduarda",
			"locale": "pt-BR",
			"is_default_image": false,
			"is_verified_merchant": false,
			"ads_only_profile_site": null,
			"image_small_url": "https://i.pinimg.com/30x30_RS/3d/34/8d/3d348dde519fe850f2aa7b5d717ced10.jpg",
			"verified_identity": {}
		},
		"pin_thumbnail_urls": [
			"https://i.pinimg.com/150x150/b9/c7/25/b9c7251809ebd079fad0d5ab8f65c084.jpg",
			"https://i.pinimg.com/150x150/86/0d/21/860d21478b7b1090d169391940eac594.jpg",
			"https://i.pinimg.com/150x150/24/85/18/2485188b43babfa3e74a974e2e75285d.jpg",
			"https://i.pinimg.com/150x150/a8/6a/d7/a86ad7019453bcc41a3a0dd32c6d50bd.jpg",
			"https://i.pinimg.com/150x150/53/87/52/5387524714c636595f20cdba053a8526.jpg"
		],
		"url": "/dudadelsanto/nail-inspo/",
		"privacy": "public",
		"followed_by_me": false,
		"type": "board",
		"description": "",
		"is_collaborative": false,
		"layout": "default",
		"name": "nail inspo",
		"image_thumbnail_url": "https://i.pinimg.com/upload/672584594289335576_board_thumbnail_2023-01-06-04-21-17_78297_60.jpg",
		"collaborated_by_me": false,
		"access": []
	},
	"buyable_product_availability": null,
	"call_to_create_responses_count": 0,
	"call_to_create_responses_preview_image_urls": [],
	"call_to_create_source_pin": null,
	"call_to_create_source_pin_id": null,
	"can_delete_did_it_and_comments": false,
	"carousel_data": null,
	"category": "",
	"click_through_link_quality": null,
	"closeup_attribution": {
		"id": "699535892028793959",
		"image_medium_url": "https://i.pinimg.com/75x75_RS/2e/af/33/2eaf3346cf7b26067a1f615fd650f344.jpg",
		"followed_by_me": false,
		"full_name": "evasiviero",
		"indexed": false,
		"type": "user",
		"domain_verified": false,
		"follower_count": 10,
		"username": "lasiviii",
		"is_ads_only_profile": false,
		"domain_url": null,
		"explicitly_followed_by_me": false,
		"blocked_by_me": false,
		"first_name": "",
		"locale": "it",
		"is_default_image": false,
		"is_verified_merchant": false,
		"ads_only_profile_site": null,
		"image_small_url": "https://i.pinimg.com/30x30_RS/2e/af/33/2eaf3346cf7b26067a1f615fd650f344.jpg",
		"verified_identity": {}
	},
	"closeup_description": null,
	"closeup_unified_description": " ",
	"closeup_user_note": " ",
	"comment_count": 0,
	"comments_disabled": false,
	"content_sensitivity": {},
	"created_at": "Wed, 09 Feb 2022 20:32:10 +0000",
	"creator_class": null,
	"creator_class_instance": null,
	"ctc_source_pin_creator": null,
	"description": " ",
	"description_html": " ",
	"did_it_disabled": false,
	"domain": "Uploaded by user",
	"dominant_color": "#a8877d",
	"embed": null,
	"formatted_description": {},
	"grid_title": "💅🏼💅🏼",
	"hashtags": [],
	"id": "672584525610478245",
	"image_medium_url": "https://i.pinimg.com/200x/c7/2f/d8/c72fd8ee489409cdea7af99f4d944b0c.jpg",
	"image_signature": "c72fd8ee489409cdea7af99f4d944b0c",
	"images": {
		"60x60": {
			"width": 60,
			"height": 60,
			"url": "https://i.pinimg.com/60x60/c7/2f/d8/c72fd8ee489409cdea7af99f4d944b0c.jpg"
		},
		"136x136": {
			"width": 136,
			"height": 136,
			"url": "https://i.pinimg.com/136x136/c7/2f/d8/c72fd8ee489409cdea7af99f4d944b0c.jpg"
		},
		"170x": {
			"width": 170,
			"height": 299,
			"url": "https://i.pinimg.com/170x/c7/2f/d8/c72fd8ee489409cdea7af99f4d944b0c.jpg"
		},
		"236x": {
			"width": 236,
			"height": 416,
			"url": "https://i.pinimg.com/236x/c7/2f/d8/c72fd8ee489409cdea7af99f4d944b0c.jpg"
		},
		"474x": {
			"width": 474,
			"height": 836,
			"url": "https://i.pinimg.com/474x/c7/2f/d8/c72fd8ee489409cdea7af99f4d944b0c.jpg"
		},
		"564x": {
			"width": 564,
			"height": 995,
			"url": "https://i.pinimg.com/564x/c7/2f/d8/c72fd8ee489409cdea7af99f4d944b0c.jpg"
		},
		"736x": {
			"width": 736,
			"height": 1298,
			"url": "https://i.pinimg.com/736x/c7/2f/d8/c72fd8ee489409cdea7af99f4d944b0c.jpg"
		},
		"600x315": {
			"width": 600,
			"height": 315,
			"url": "https://i.pinimg.com/600x315/c7/2f/d8/c72fd8ee489409cdea7af99f4d944b0c.jpg"
		},
		"orig": {
			"width": 828,
			"height": 1461,
			"url": "https://i.pinimg.com/originals/c7/2f/d8/c72fd8ee489409cdea7af99f4d944b0c.jpg"
		}
	},
	"is_call_to_create": true,
	"is_eligible_for_aggregated_comments": true,
	"is_eligible_for_brand_catalog": false,
	"is_eligible_for_pdp": false,
	"is_hidden": false,
	"is_native": true,
	"is_oos_product": false,
	"is_playable": false,
	"is_promotable": false,
	"is_promoted": false,
	"is_quick_promotable": false,
	"is_quick_promotable_by_pinner": false,
	"is_repin": true,
	"is_stale_product": false,
	"is_video": false,
	"is_whitelisted_for_tried_it": true,
	"last_repin_date": null,
	"link": null,
	"link_domain": null,
	"method": "photos",
	"mobile_link": null,
	"native_creator": {
		"id": "699535892028793959",
		"image_medium_url": "https://i.pinimg.com/75x75_RS/2e/af/33/2eaf3346cf7b26067a1f615fd650f344.jpg",
		"followed_by_me": false,
		"full_name": "evasiviero",
		"indexed": false,
		"type": "user",
		"domain_verified": false,
		"follower_count": 10,
		"username": "lasiviii",
		"is_ads_only_profile": false,
		"domain_url": null,
		"explicitly_followed_by_me": false,
		"blocked_by_me": false,
		"first_name": "",
		"locale": "it",
		"is_default_image": false,
		"is_verified_merchant": false,
		"ads_only_profile_site": null,
		"image_small_url": "https://i.pinimg.com/30x30_RS/2e/af/33/2eaf3346cf7b26067a1f615fd650f344.jpg",
		"verified_identity": {}
	},
	"origin_pinner": {
		"id": "699535892028793959",
		"image_medium_url": "https://i.pinimg.com/75x75_RS/2e/af/33/2eaf3346cf7b26067a1f615fd650f344.jpg",
		"followed_by_me": false,
		"full_name": "evasiviero",
		"indexed": false,
		"type": "user",
		"domain_verified": false,
		"follower_count": 10,
		"username": "lasiviii",
		"is_ads_only_profile": false,
		"domain_url": null,
		"explicitly_followed_by_me": false,
		"blocked_by_me": false,
		"first_name": "",
		"locale": "it",
		"is_default_image": false,
		"is_verified_merchant": false,
		"ads_only_profile_site": null,
		"image_small_url": "https://i.pinimg.com/30x30_RS/2e/af/33/2eaf3346cf7b26067a1f615fd650f344.jpg",
		"verified_identity": {}
	},
	"pinned_to_board": null,
	"pinner": {
		"id": "672584663008554825",
		"image_medium_url": "https://i.pinimg.com/75x75_RS/3d/34/8d/3d348dde519fe850f2aa7b5d717ced10.jpg",
		"followed_by_me": false,
		"full_name": "maria eduarda",
		"indexed": true,
		"type": "user",
		"domain_verified": false,
		"follower_count": 11680,
		"username": "dudadelsanto",
		"is_ads_only_profile": false,
		"domain_url": null,
		"explicitly_followed_by_me": false,
		"blocked_by_me": false,
		"first_name": "maria eduarda",
		"locale": "pt-BR",
		"is_default_image": false,
		"is_verified_merchant": false,
		"ads_only_profile_site": null,
		"image_small_url": "https://i.pinimg.com/30x30_RS/3d/34/8d/3d348dde519fe850f2aa7b5d717ced10.jpg",
		"verified_identity": {}
	},
	"price_currency": "USD",
	"price_value": 0,
	"privacy": "public",
	"product_pin_data": null,
	"promoted_is_removable": false,
	"promoter": null,
	"reaction_counts": {},
	"related_article": {},
	"repin_count": 0,
	"rich_metadata": null,
	"section": null,
	"seo_description": "6/fev/2022 - maria encontrou este Pin. Encontre (e salve!) seus próprios Pins no Pinterest.",
	"seo_noindex_reason": null,
	"seo_title": "💅🏼💅🏼 | Unhas estranhas, Unhas coloridas, Unhas desenhadas",
	"seo_url": "/pin/672584525610478245/",
	"share_count": 0,
	"shopping_flags": [],
	"shopping_rec_disabled": false,
	"should_redirect_id_only_url_to_text_url": false,
	"sponsorship": null,
	"story_pin_data": null,
	"story_pin_data_id": null,
	"third_party_pin_owner": null,
	"title": "💅🏼💅🏼",
	"tracked_link": null,
	"tracking_params": "CwABAAAAEDUwMDQyMzE3MTAyMDkzNzgLAAcAAAAPdW5rbm93bi91bmtub3duAA",
	"tracking_params_map": {
		"PinResource": "CwABAAAAEDUwMDQyMzE3MTAyMDkzNzgLAAcAAAAPdW5rbm93bi91bmtub3duAA"
	},
	"via_pinner": {
		"id": "52776764291687360",
		"image_medium_url": "https://i.pinimg.com/75x75_RS/d0/a8/d5/d0a8d580f1578b6e23bf8ecf0d7ef04f.jpg",
		"followed_by_me": false,
		"full_name": "Sarah Cristina",
		"indexed": true,
		"type": "user",
		"domain_verified": false,
		"follower_count": 11,
		"username": "sarahcsr_",
		"is_ads_only_profile": false,
		"domain_url": null,
		"explicitly_followed_by_me": false,
		"blocked_by_me": false,
		"first_name": "Sarah",
		"locale": "pt-BR",
		"is_default_image": false,
		"is_verified_merchant": false,
		"ads_only_profile_site": null,
		"image_small_url": "https://i.pinimg.com/30x30_RS/d0/a8/d5/d0a8d580f1578b6e23bf8ecf0d7ef04f.jpg",
		"verified_identity": {}
	},
	"videos": null
}
```
