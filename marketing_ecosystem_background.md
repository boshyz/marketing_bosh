### Marketing ecosystem reporting general break down

##### Marketing metrics usually come a variety of sources. The below section will breifly outline what they are, & how or when they are integrated into a global business intelligence source of truth i.e. a Data Visulisation Platform

* As a general rule, marketing data is the messiest data there is, because unlike product data that appears as rendered key value pairs entered by developers, the frquency of campaign deployments makes them subject to poor data integrity because all dimension data must be manually configured. 
* To track cross platforms careful considersation needs to be paid to naming convenion of campaign heirachies and tracking parameters to ensure that matches between different source platforms can be made
* You won't know what metrics to include without talking to marketing team first. 
* The marketing/media team will instruct you on how to break out the taxonomy entered into the campaign heirachies in order to create the reporting segments they want. 
* Marketing campaigns should be based on business objectives and describe the audience and intended call to action that the campaign is designed to aquire. 
* Digial campaigns are often based off a busineses's website architecure (url path sections) as it forms the basis of how the customer interacts with the business, if it its not tagged it can't be segmented.
* Rule of thumb general business communication to it's customers can be made by segmenting analytics to the url path 3 or path 4 depending on the site content detail, as segments will not be worth persuing unless they are sufficent in volume,url paths 3 and 4 are inclusive of the individual page paths. The site path captures the interest of the user/customer whilst the action/event will signal their intent on that topic
* You can't, or really you SHOULD NOT guess & make inferences about marketing data, or site analytics data in general, just by looking at the account structure, talk to your media team to understand why campaigns were set up in certain way and your web developer team to understand how the taggin was configured. You will not be able to make sense of anything without a data dictionary- especially for web anayltics if you youself do not have access to the tag configuration, you won't understand what the metrics actually mean, they are customized to capture different events.


#### AdServers (Must have source of Truth)

* Marketing metrics from ad servers, are segmented by two types:
    * Cost Metrics - related to budget of campaign bought on CPC or CPM model usually
        * Cost
        * Impressions
        * Cllicks
        * Reach
    * Conversion metrics - usually pixels embeded on site that signal and capture a specific desired action, determined by conversion filtered to a conversion tag name

* For businesses, generally only cost metrics from Ads platforms (Cost & Impressions always, sometimes clicks) are considered a source of truth for a business. 
* Whilst Ads platform conversion metrics are generally not considered a source of truth for the business they are imperative for media teams to have in their campaign monitoring dashboards because in platform conversions are the only metric that media teams can optimize towards. Business source of truth metrics from salesforce/web anayltics only serve as a campaign objective, but in platform metrics are required as marker for campaign optimisiation.
* Cost, impressions, clicks are mutally exclusive and can be added up, but Reach is a distinct count of user id and will change depending on how you segment. Since the actual ids are not given to you just the count of the them, you don't know how to de dupe across days, or placments/creatives 

#### DSPs  (Must have source of Truth if running)

* Most common DSP is DV360 
* Marketing metrics from DSPs, are segmented by two types:
    * Cost Metrics - related to budget of campaign bought on CPC or CPM model usually
        * Cost
        * Impressions
        * Cllicks
    * Conversion metrics - usually pixels embeded on site that signal and capture a specific desired action, determined by conversion filtered to a conversion tag name
    * Appears auto tagged in in Google anayltics as source dbm
    * Different campain structure
        * DV360 IO = CM Camapaign 
        * DV360 line item - houses targeting stratgey sits below campaign but above placement IO : Line Item = 1:Many - Thus unfortunately 
        * DV360 creative = CM mediabuy Line Item: DV360 Creative = Many: Many
        * DV360 does not house the actual creatives 
       

##### Campaign manager <br/>


* For large companies and agencies, ads served in other platforms will also be trafficked in Google CM - the most commonly used Ads Managers
* Trafficking entails that the same campaign structure that exsits in an external ads platform such as Facebook, or Tiktok is also created in Campaign Manager in such a way that the data model would be 
    * Social Sources
        * Social Campaign -> CM Campaign
        * Social Adset/Placment -> Mediabuy Name
        * Creative -> Creative
        * Creatives are housed in Native Social platform
    * Search Sources
        * Adwords campaigns usually have to manaully trafficked
        * However as a rule of thumb, businesses that can afford CM can afford SA360 - that you can sync and manage Adwords/Google Ads in, so you can just enable the 360 auto tracking feature in CM 
            * SA360 appears in CM under the campaign name DART SEARCH, SA360 Accounts get moved down to media buy, you have to manually traffic in search campaign under creative, sometimes for convenience people just apply a percentage mulitplitive from account to campaigns if campaigns are not trafficked but that is just an estimtor as the actual granualrity does not exist. 
            * No creatives housed
    * Direct buys with publishers 
        * CM houses actual physical creatives under creative heiarchy 


* The purpose of CM is to create a campaign audit and reconcile what was booked with what was delivered from the publisher's platform (Ad plaform, DFP and or DSPs) to ensure accuracy
    * Ad ops team will create CM click & impressions trackers (floodlights) in DCM and give them to Ad ops team to place in platform usually seen as 1x1 trackers.
    * The impressions and click trackers allow CM to break down conversions by post impression and post click. Total conversions sums the two, but depending on the business, you post click and post impression broken out. 
    * The advantage of CM it accounts for impression tracking (conversions made from serving (seeing) the ad but not clicking on the link) which web analytics cannot account for.
    * Although click through conversions are generally accepted as showing gretaer intent, post impression conversions can be useful to understand campaigns who's purpose is to generate awareness by targeting page lands
    * Conversions have recongised look back windows to when to stop attributing to conversion the campaign, default is generally 90 days but you can always custom configure



##### Web & App Analytics  <br/>

* Depending on the business type analyics can be used to track different things, Ad Manager trackers, Ad platform trackers e.g. facebook pixel need to be given to the Web developer to implement on the website/app to make sure things site conversions are tracked
* It is almost always the source of truth for visits, and marketing leads (sign ups)
* If the site is ecommerce it can also be the source of truth for revenue
* Depending on the business it is also of often the primary generator of click stream data, though some businesses like to process their data for click stream data in mixpanel or amplitude etc
* Campaign activity is tracked by appending the relevent utm parameters and campaign heiarchy values to the landing page url of ads
    * CM & SA360 and Google Ads are all auto tageed in Google Anlaytics as DFA, Dart 

* Analytics data is based on sessions - usually 30 min window from openinning to no activity, or till the application is closed
* Session data feeds up into cookie ID which is unique tracker, usually based of device ID, that acts a proxy for a user, also expires in 90 days
* User id is the registered id generated for user who has signed up to your business, usually idenfited by a email or phone number depending on how they signed up, a user can have multp 
* Reports are pulled with last click attribution, so dimension attriubted to a metric will be whatever last product/segment/feature they interacted with, so the time segment of reports is important, depending on the type of activity... e.g. for streaming platforms it might better to have hourly data, because users are likely to browse more than 1 show (video plays) during a session, same for ecom depending on complexity. Pulling by day will show you the last touch page for the customer that day for a specfic action/interaction. 

#### Salesforce Core/CRMs/Marketo  <br/>

* Depending on the business type, business that are generally B2B, utilize salesforce or marketo to create marketing campaign segments (develop personas and marketing messaging) from customer profiles based of demographics, customer life time value recognised reveneue, and sometimes other campaigns/product features they engaged with
* Commmon salesforce core (sales and or service cloud) metrics include:
    * opportunies
    * leads
    * engagement
    * sales
    * revenue
    * call
* Metrics are broken out by business units for large enough businesses and individual sales agents, the campaign (whatever pitch they are pitching) and the contact details and interactions logs of leads and aquired accounts
* Similar to ads platform data, everything has to be manually entered by a sales agent, and attributed to the right campaign so it's important naming conventions are considered here to map it to back to the marketing leads 
* What metrics you track depends on the campaign objetive that was breifed in, the tpye of business and where you sit in sales funnel 

