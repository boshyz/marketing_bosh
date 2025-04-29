### Marketing ecosystem reporting general break down


* Marketing metrics usually come from a variety of sources. 

* The below section will briefly outline what they are, & how or when they are integrated into a global business intelligence source of truth i.e. a Data Visualization Platform


* As a general rule, marketing data is the messiest data there is, because unlike product data that appears as rendered key value pairs entered by developers, the frequency of campaign deployments makes them subject to poor data integrity because all dimension data must be manually configured.


* To track cross platforms careful consideration needs to be paid to naming convention of campaign hierarchies and tracking parameters to ensure that matches/joins between different source platforms can be made


* You won't know what metrics to include without talking to the marketing team first, since not all campaigns use have the same objective, e.g. awareness vs sales vs lead gen, you will need the specific tag name & or weighting to report accurately to meet their needs vs salesforce emails, calls, open etc.


* The marketing/media team will also instruct you on how to break out the taxonomy entered into the campaign hierarchies in order to create the reporting segments they want.


* Marketing campaigns should be based on business objectives and describe the targeted audience and intended call to action that the campaign is designed to acquire/achieve.


* Digital campaigns are often based off a business's website architecture (url path sections) as it forms the basis of how the customer interacts with the business, if it's not tagged it can't be segmented.


* Rule of thumb, general business communication to customers can be made by segmenting analytics user level data at url path 3 or url path 4 depending on the site content detail.


* Url path 3 or 4 are good starters, because segments must be sufficient in volume, in order to be worth the time/resource to create a campaign for. Url paths 3 and 4 are inclusive of the individual page paths. 

* The url path captures the interest of the user/customer whilst the action/event will signal their intent on that topic
  
* You can't, or really you SHOULD NOT guess & make inferences about marketing data, or site analytics data in general just by looking at the account structure. Instead talk to your media team to understand why campaigns were set up in a certain way and your web developer team to understand how the tagging was configured. You will not be able to make sense of anything without a data dictionary- especially for web analytics if you yourself do not have access to the tag configuration, you won't understand what the metrics actually mean, they are customized to capture different events and the labeling is also custom manual entry.




#### AdServers (Must have source of Truth)


* Marketing metrics from ad servers, are segmented by two types:
   * Cost Metrics - related to budget of campaign bought on CPC or CPM model usually
       * Cost
       * Impressions
       * Clicks
       * Reach
   * Conversion metrics - usually pixel/floodlights embedded on site that signal and capture a specific desired action, determined by conversions filtered to a specific conversion tag name(s)


* For businesses, generally only cost metrics from Ads platforms (Cost & Impressions always, sometimes clicks) are considered a source of truth for a business.


* Whilst Ads platform conversion metrics are generally not considered a source of truth for the business they are imperative for media teams to have in their campaign monitoring dashboards because in platform conversions are the only metric that media teams can optimize towards. Business source of truth metrics from salesforce/web analytics only serve as a campaign objective, but in platform metrics are required as marker for campaign optimisation.


* Cost, impressions, clicks are mutually exclusive and can be added up, but Reach is a distinct count of user id and will change depending on how you segment the data. Since the actual ids are not given to you just the count of the them, you need to be aware you can’t dedupe across time interval eg. days, weeks or campaign hierarchy level e.g. placements/creatives. E.g whilst summing the cost of placements will equate to campaign cost, summing reach across placements will generally be more than the campaign level 


#### DSPs  (Must have source of Truth if running)


* Most common DSP is DV360
* Marketing metrics from DSPs, are segmented by two types:
   * Cost Metrics - related to budget of campaign bought on CPC or CPM model usually
       * Cost
       * Impressions
       * Clicks
   * Conversion metrics - usually pixels embedded on site that signal and capture a specific desired action, determined by conversion filtered to a conversion tag name
   * Appears auto tagged in in Google analytics as utm_source = dbm
   * Different campaign structure
       * DV360 IO = CM Campaign
       * DV360 line item - houses targeting strategy sits below DCM campaign/DV360 IO but above DCM placement and usually where budget break down occurs
           * DCM placement: DV360 Line Item, you can’t control how much IO budget will be allocated to a specific DV360 creative, as they are live bids.
       * DV360 creative = CM mediabuy Line Item: DV360 Creative = Many: Many
       * DV360 does not house the actual creatives
     


##### Campaign manager <br/>




* For large companies and agencies, ads served in other platforms will also be trafficked in Google CM - the most commonly used Ads Managers


* Trafficking entails that the same campaign structure that exists in an external ads platform such as Facebook, or Tiktok is also created in Campaign Manager in such a way that the data model would be
   * Social Sources
       * Social Campaign -> CM Campaign
       * Social Adset/Placement -> Media Buy Name
       * Creative -> Creative
       * Creatives are housed in Native Social platform
   * Search Sources
       * Adwords campaigns usually have to be manually trafficked
       * However as a rule of thumb, businesses that can afford CM can usually afford SA360 - that you can sync manage Adwords/Google Ads in, so you can just enable the SA360 auto tracking feature in CM
           * SA360 appears in CM under the campaign name DART SEARCH, SA360 Accounts get moved down to the CM media buy level, you have to manually traffic in search campaign under creative, sometimes for convenience people just apply a percentage multiplicative from account to campaigns if campaigns are not trafficked manually - but that is just an estimator as the actual granularity does not exist.
           * No creatives housed in CM for search or other ad platforms
   * Direct buys with publishers
       * CM houses actual physical creatives under creative hierarchy




   * The purpose of CM is to create a campaign audit and reconcile what was booked with what was delivered from the publisher's platform (Ad platform, DFP and or DSPs) to ensure accuracy
     
   * Ad ops team will create CM click & impressions trackers (floodlights) in DCM and give them to Ad ops team to place in platforms usually seen as 1x1 media buy/placement.

   * The impressions and click trackers allow CM to break down conversions by post impression and post click. Total conversions sums the two, but depending on the business, you post click and post impression broken out.

   * The advantage of CM is that it accounts for impression tracking (conversions made from serving (seeing) the ad but not clicking on the link) which web analytics cannot account for.

   * Although click through conversions are generally accepted as showing greater intent, post impression conversions can be useful to understand campaigns whose purpose is to generate awareness by targeting page lands

   * Conversions have recognised look back windows to when to stop attributing to conversion the campaign, default is generally 90 days but you can always custom configure
 
   * CM can also track revenue, just enable the revenue tracking alongside counter tracking. 






##### Web & App Analytics  <br/>


* Depending on the business type, web/app analytics can be used to track different things, Ad Manager trackers, Ad platform trackers e.g. facebook pixel need to be given to the Web developer to implement on the website/app to make sure things like site conversions are tracked

* It is almost always the source of truth for visits, and marketing leads (sign ups)

* If the site is ecommerce it can also be the source of truth for revenue

* Depending on the business it is also of often the primary generator of clickstream data, though some businesses like to process their data for click stream data in mixpanel or amplitude etc

* Campaign activity is tracked by appending the relevant utm parameters and campaign hierarchy values to the landing page url of ads

   * CM & SA360 and Google Ads are all auto tagged in Google Analytics as DFA, Dart


* Analytics data is based on sessions - usually 30 min window from openinning to no activity, or till the application is closed

* Session data feeds up into cookie ID which is a unique tracker, usually based off device ID, that acts a proxy for a user, also expires in 90 days

* User id is the registered id generated for user who has signed up to your business, usually identified by a email or phone number depending on how they signed up, a user can have multiple cookies depending on the number of devices they have or if they have cleared their cache

* Reports are pulled with last click attribution, so dimension attributed to a metric will be whatever last product/segment/feature they interacted with, so the time segment of reports is important, depending on the type of activity... e.g. for streaming platforms it might be 
better to have hourly data, because users are likely to browse more than 1 show (video plays) during a session, same for ecom depending on complexity. Pulling by day will show you the last touch page for the customer that day for a specific action/interaction.


#### Salesforce Core/CRMs/Marketo  2nd most common source of truth <br/>


* Depending on the business type, business that are generally B2B, utilize salesforce, mailchimp or marketo to create marketing campaign segments (develop personas and marketing 
messaging) from customer profiles based of demographics, customer lifetime value recognised revenue, and sometimes other campaigns/product features they engaged with
CRMS are confusing because they have the word marketing in them, but generally they mean captured leads with contact info that you can utilize internal systems to create email campaigns for, set up times to reach out the clients via calls, events, or generate app notifications/messages


* Common salesforce core (sales and or service cloud) metrics include:
   * opportunities
   * leads
   * engagement
   * sales
   * revenue
   * call
   * emails (sends, opens, clicks ect)
   * tasks 


* Metrics are broken out by business units for large enough businesses and individual sales agents, the campaign (whatever pitch they are pitching) and the contact details and interactions logs of leads and acquired accounts


* Similar to ads platform data, everything has to be manually entered by a sales agent, and attributed to the right campaign so it's important naming conventions are considered here to map it to back to the marketing leads, you need to speak with a sales rep to know what features/metrics in the report they want to see. They will also brief you on naming convention. 


* What metrics end up in the sales reporting section of the Business Intelligence platform is entirely dependent on the campaign objective that was briefed in, the type of business and where you sit in sales funnel


### Key take ways

* You must be breifed what metrics and dimenions to include in the reporting by the media team or sales agent, or web developer who ever set up the campaign. Who ever set up the campaign dictates the campaign strategey which is what the results of the dashboard reflect and be able to answer the aims of the campaign - reiterated as questions. 
