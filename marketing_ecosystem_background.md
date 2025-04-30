# Marketing ecosystem reporting general break down




* Marketing metrics usually come from a variety of sources.
The below section will briefly outline what they are, & how or when they are integrated into a centralised business intelligence source of truth i.e. a Data Visualization Platform




* As a general rule, marketing data is the messiest data there is. 


Product data attributes, are generally a lot cleaner than marketing because:
     * They are usually only configured once upon completion of a new feature 
     * And appear as rendered key value pairs within a singular platform.


Marketing data in comparison, usually suffers from poor data integrity because of:
* The frequency of campaign deployments and turnarounds (especially seen in social)
* The same themes captured in naming attributes must be configured where applicable, across multiple un-integrated platforms, that are often run simultaneously
* The complexity of information that must be captured in attribute names, multiplicative across at least 3 different attribute hierarchies (campaign, placement, creative) in each platform.




* Thus in order to accurately capture and track cross platform marketing activity across different stages of the marketing funnel:
Awareness/brand
Acquisition/Conversion
Retention/Upsell
careful consideration to global standardised naming convention of campaign hierarchies and tracking parameters (that account for character limits as well as readability) must be made to ensure that matches/joins between different primary data sources(platforms) are possible.




* As an analyst, no matter how many years of experience you have, you won't know what metrics to include without talking to the marketing team first, since not all campaigns will have the same objective - metric of success, e.g. awareness vs sales vs lead gen, vs salesforce: emails, calls, etc. 


To select the right metrics, you will need the specific tag name & or sometimes metric weighting, to in order to accurately reflect the business’s reporting needs




* The marketing/media team will also instruct you on how to break out the taxonomy entered into the campaign hierarchies in order to create the reporting segments they want.




* Marketing campaigns should be based on business objectives and describe the targeted audience and intended call to action that the campaign is designed to acquire/achieve.




* Digital campaigns are often based on a business's website architecture (url path sections) as it forms the basis of how the customer interacts with the business, if it's not tagged it can't be segmented.




* Rule of thumb, general business communication to customers can be made by segmenting analytics user level data at url path 3 or url path 4 depending on the site content detail.




• Url path 3 or 4 are good starters, because segments must be sufficient in volume, in order to justify the time/resource to create a campaign. Url paths 3 and 4 are inclusive of the individual page paths.




The url path captures the interest of the user/customer whilst the action/event will signal their intent on that topic


* You can't, or really you SHOULD NOT guess & make inferences about marketing data, or site analytics data in general just by looking at the account structure. Instead talk to your media team to understand why campaigns were set up in a certain way and your web developer team to understand how the tagging was configured. You will not be able to make sense of anything WITHOUT a data dictionary - especially for web analytics if you yourself do not have access to the tag configuration, you won't understand what the metrics actually mean, they are customized to capture different events and the labeling is manually entered by whoever created it. 






### AdServers (Must have source of Truth)




* Marketing metrics from ad servers, are segmented by two types:
  * Cost Metrics - related to budget of campaign bought on CPC or CPM model usually
      * Cost
      * Impressions
      * Clicks
      * Reach
  * Conversion metrics - usually pixel/floodlights embedded on websites/apps that signal and capture a specific desired action, determined by conversions filtered to a specific conversion tag name(s)




* For businesses, generally only cost metrics from Ads platforms (Cost & Impressions always, sometimes clicks) are considered a source of truth for a business.




* Whilst Ads platform conversion metrics are generally not considered a source of truth for the business, they are imperative for media teams to have in their campaign monitoring dashboards.  This is because in platform conversions are the only metric that media teams can optimize towards. Business source of truth metrics from salesforce/web analytics, only serve as a campaign objective, but in platform metrics are required as marker for campaign optimisation.




* Cost, impressions, & clicks are mutually exclusive and can be added up, but Reach is a distinct count of user id and will change depending on how you segment the data. Since the actual ids are not given to you, it’s important to be aware you can’t dedupe reach figures across any type of segmentation, including time interval eg. days, weeks or campaign hierarchy level e.g. placements/creatives. E.g whilst summing the cost of placements will equate to the overall campaign cost for the campaign they sit under, summing reach across placements under a campaign will generally be greater than the reach pulled at the just campaign level for that same campaign




### DSPs  (Must have source of Truth if running)


* Most common DSP is DV360
* Marketing metrics from DSPs, are segmented by two types:
  * Cost Metrics - related to budget of campaign usually
 bought on CPM model sometimes cpc       * Cost
      * Impressions
      * Clicks
  * Conversion metrics - code embedded on website/apps that signal and capture a specific desired action, determined by filtering a counter conversion to a conversion tag name
  * Appears auto tagged in in Google analytics as utm_source = dbm
  * Different campaign structure
      * DV360 Insertion Order = CM Campaign
      * DV360 line item:
* houses targeting strategy 
* line item sits below DCM campaign/DV360 IO but above CM placement and usually where budgets are allocated
* relationship cardinality of DV360 Line item to CM Placement = DV360 Creative is Many:Many
* you can’t control how much a line budget will be allocated to a specific DV360 creative, as they are intent driven live bids - programmatic is similar to paid search.
      * relationship cardinality between DV360 creative = CM placement is 1: 1
 * DV360 does not house the physical creatives, CM does.
   




### Campaign manager (CM) <br/> 


* For large companies and agencies, ads served in other platforms will also be trafficked in Google CM - the most commonly used Ads Manager. The placement level is called media buy in CM and is used interchangeably. 


* Trafficking entails that the same campaign structure that exists in an external ads platform such as Facebook, or Tiktok is also created in Campaign Manager in such a way that the data model match would be
  * Social Sources
      * Social Campaign -> CM Campaign
      * Social Adset/Placement -> Media Buy Name/Placement
      * Creative -> Creative
      * Creatives are housed in Native Social platform
  * Search Sources
      * Adwords campaigns usually have to be manually trafficked to appear in CM
      * However as a rule of thumb, businesses that can afford CM can usually afford SA360. 
* SA360 allows you to sync and manage Adword, so you can just enable the SA360 auto tagging feature to make the search data appear in CM
          * SA360 appears in CM under the campaign name DART SEARCH, as such SA360 Accounts get moved down to the CM media buy level, you have to manually traffic in search campaigns under creative, sometimes for convenience people just apply a percentage multiplicative from account to campaigns. However if campaigns are not trafficked manually - this approach is just an estimator as the actual granularity does not exist.
       * No creatives housed in CM for search or other social ad platforms
  	* Physical creatives housed in DCM are for Direct buys with publishers and or programmatic buys with DSPs
     


* The purpose of CM is to create a campaign audit and reconcile what was booked with what was delivered from the publisher's platform (Ad platform, DFP and or DSPs) to ensure accuracy. The accounts for direct buys/DSPs are usually reconciled on what was delivered in CM, and the number of impressions must match the budget negotiated * the rate (CPC or CPM) in CM. Thus for ad ops, it is good to practice to cap the cost, so that the cost does not appear inflated should the publisher over deliver on the buy model (impressions/clicks)


 * Ad ops team will create dynamic CM click & impressions trackers (floodlights) in CM and give them to Ad ops team to place in tag manager on the publisher’s website. Tracking for social ad platforms is done by piggybacking pixels to dynamic CM floodlights link: https://www.facebook.com/business/help/421433191260652?locale=en_GB


 * The impressions and click trackers allow CM to break down conversions by post impression and post click. Total conversions sums the two, but depending on the business, you post click and post impression broken out.


 * The advantage of CM is that it accounts for impression tracking (conversions made from serving (seeing) the ad but not clicking on the link) which site analytics cannot account for.


 * Although click through conversions are generally accepted as showing greater intent, post impression conversions can be useful to understand campaigns whose purpose is to generate awareness by targeting page lands


* Conversions have recognised look back windows to when to stop attributing the success action to the campaign, default & max is generally 90 days but you can always custom configure to be less


* CM can also track revenue, just enable the revenue tracking alongside counter tracking.
* Another advantage is because attribution models by default work on last click, trafficking in CM will allow you to dedupe conversions/clicks across platforms, so sometimes CM is given as the source of truth for clicks for this reason. 



### Web & App Analytics  <br/>


* Depending on the business type, web/app analytics can be used to track different things, Ad Manager trackers, Ad platform trackers e.g. facebook pixel need to be given to the Web developer to implement on the website/app to make sure site conversions driven from them are accurately reflected/tracked


* It is almost always the source of truth for visits, and marketing leads (sign ups)


* If the site is ecommerce it can also be the source of truth for revenue


* Site analytics is last click based and does not reflect impression tracking, the attribution of clicks/conversions based on paid vs organic will differ from that of CM


* Depending on the business, site analytics is also often the primary generator of clickstream data, though some businesses like to process their data for click stream data in mixpanel or amplitude etc


* Campaign activity is tracked by appending the relevant utm parameters and campaign hierarchy values to the landing page url of ads
 
* CM & SA360 and Google Ads are all auto tagged in Google Analytics as medium = DFA, and cpc respectively


* Analytics data is based on sessions - usually 30 min window from openinning to no activity, or till the application is closed


* Session ID are the lowest level of granularity and sit under cookie ID - which is a unique tracker, usually based off device ID, that acts a proxy for a user, that expires in 90 days from first touch or till cookie cache clearing


* User id is the registered id generated for users who has signed up to your business, usually identified by a email or phone number depending on how they signed up, a user can have multiple cookies depending on the number of devices they have or if they have cleared their cache
* Reports are pulled with last click attribution, so dimension attributed to a metric will be whatever last product/segment/feature they interacted with, so the time interval you choose to segment reports is important, and the appropriate level will differ depending on the type of activity... e.g. for streaming platforms it might be better to have the time interval be minute based -seleceted for a certain time period e.g. only between 6-7 pm, because users are likely to browse more than 1 show (video plays) during a session, same for ecom depending on complexity. Pulling by day will show you the last touch page for the customer that day for a specific action/interaction.




### Salesforce Core/CRMs/Marketo  2nd most common source of truth <br/>


* Depending on the business type, business that are generally B2B, utilize salesforce, mailchimp or marketo to create marketing campaign segments (develop personas and marketing messaging) from customer profiles based off demographics, recognised customer lifetime revenue, and sometimes other campaigns/product features they engaged with
* In regards to reporting purposes, CRMs e.g  marketing cloud salesforce are primarily used to track marketing metrics for internal marketing methods such as email campaigns, in app messages, and or device notifications. 
* You can use salesforce to select existing customers to share with facebook/ or another ad server platform so that you can create look-alike audiences to prospect to, but the metrics you would pull for the campaign would come from the native ad server.
* You can also report on sales metrics like 


* Common salesforce core (sales and or service cloud) metrics include:
  * opportunities 
  * leads
  * sales
  * revenue
  * calls
  * Tasks
  * Deal size
  * Customer lifetime value


* Similar to how different facebook campaign objectives have different metrics salesforce marketing metrics and attributes are determined by:
* Method of approach:
	* omnichannel
	* email
	* Push notification
	* In platform
      *Whats app
	
* All of these approaches all have an associated campaign (whatever pitch they are pitching), Case/Individual clients/accounts the approach was designed to interact with. It is important to distinguish between sent vs event date, as event date is date the action occurred. 


* Similar to ads platform data, everything has to be manually entered by a sales agent, and attributed to the right campaign so it's important naming conventions are considered here to map it to back to the marketing leads, you need to speak with a sales rep to know what features/metrics in the report they want to see. They will also brief you on naming convention.




* What metrics end up in the sales reporting section of the Business Intelligence platform is entirely dependent on the campaign objective that was briefed in, the type of business and where you sit in sales funnel









### Key take ways

* You must be breifed what metrics and dimenions to include in the reporting by the media team or sales agent, or web developer who ever set up the campaign. Who ever set up the campaign dictates the campaign strategey which is what the results of the dashboard reflect and be able to answer the aims of the campaign - reiterated as questions. 
