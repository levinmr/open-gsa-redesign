---
title: analytics.usa.gov API
banner-heading: analytics.usa.gov API
---

<!-- Beta status alert -->
<div class="usa-alert usa-alert-warning" id="site-wide-alert" role="alert">
   <div class="usa-alert-body">
     <strong>
       This project is in BETA
     </strong>
     <p class="usa-alert-text">
       This API is under active development, and breaking changes may be made without warning.
       Have feedback or questions? <a href="https://github.com/18F/analytics.usa.gov/issues">Please let us know</a>!

       Please note we have recently updated to `v2.0.0`, please update your requests accordingly.
     </p>
   </div>
 </div>
<!-- end Beta status alert -->

## Overview

In addition to being published and available for download, the data generated for analytics.usa.gov  is also available via an API.

**Please note we have recently updated to `v2.0.0`, please update your requests accordingly.**

The URL for the API is `https://api.gsa.gov/analytics/dap/v2.0.0`, and it exposes 3 routes to query data:

- `/reports/<report name>/data`
- `/agencies/<agency name>/reports/<report name>/data`
- `/domain/<domain>/reports/<report name>/data`

<p><small><a href="#">Back to top</a></small></p>

## Getting Started

To begin using this API, you will need to register for an API Key. You can sign up for an API key below.  After registration, you will need to provide this API key in the `x-api-key` HTTP header with every API request.

{% raw %}
<div id="apidatagov_signup">Loading signup form...</div>
<script type="text/javascript">
  /* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
  var apiUmbrellaSignupOptions = {
    // Pick a short, unique name to identify your site, like 'gsa-auctions'
    // in this example.
    registrationSource: 'gsa-dap',

    // Enter the API key you signed up for and specially configured for this
    // API key signup embed form.
    apiKey: 'Wjww6pZMosePwXxnz7foeWBYa0ADCcw1NIMfuOoP',

    // Provide an example URL you want to show to users after they signup.
    // This can be any API endpoint on your server, and you can use the
    // special {{api_key}} variable to automatically substitute in the API
    // key the user just signed up for.
    exampleApiUrl: 'https://api.gsa.gov/analytics/dap/v2.0.0/reports/site/data?api_key={{api_key}}',

    // OPTIONAL: Provide extra content to display on the signup confirmation
    // page. This will be displayed below the user's API key and the example
    // API URL are shown. HTML is allowed. Defaults to ""
    // signupConfirmationMessage: '',

    // OPTIONAL: Provide a URL to your own contact page to link to for user
    // support. Defaults to "https://api.data.gov/contact/"
    contactUrl: 'https://github.com/gsa/gsa-apis/issues',

    // OPTIONAL: Set to true to verify the user's e-mail address by only
    // sending them their API key via e-mail, and not displaying it on the
    // signup confirmation web page. Defaults to false.
    // verifyEmail: true,

    // OPTIONAL: Set to false to disable sending a welcome e-mail to the
    // user after signing up. Defaults to true.
    // sendWelcomeEmail: false,

    // OPTIONAL: Provide the name of your developer site. This will appear
    // in the subject of the welcome e-mail as "Your {{siteName}} API key".
    // Defaults to "api.data.gov".
    // siteName: 'GSA Developer Network',

    // OPTIONAL: Provide a custom sender name for who the welcome email
    // appears from. The actual address will be "noreply@api.data.gov", but
    // this will change the name of the displayed sender in this fashion:
    // "{{emailFromName}} <noreply@api.data.gov>". Defaults to "".
    // emailFromName: 'GSA Developer Network',

    // OPTIONAL: Provide an extra input field to ask for the user's website.
    // Defaults to false.
    // websiteInput: true,

    // OPTIONAL: Provide an extra checkbox asking the user to agree to terms
    // and conditions before signing up. Defaults to false.
    // termsCheckbox: true,

    // OPTIONAL: If the terms & conditions checkbox is enabled, link to this
    // URL for your API's terms & conditions. Defaults to "".
    // termsUrl: "https://agency.gov/api-terms/",
  };

  /* * * DON'T EDIT BELOW THIS LINE * * */
  (function() {
    var apiUmbrella = document.createElement('script'); apiUmbrella.type = 'text/javascript'; apiUmbrella.async = true;
    apiUmbrella.src = 'https://api.data.gov/static/javascripts/signup_embed.js';
    (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(apiUmbrella);
  })();
</script>
<noscript>Please enable JavaScript to signup for an <a href="http://api.data.gov/">api.data.gov</a> API key.</noscript>
{% endraw %}

| HTTP Header Name | Description |
| ---- | ----------- |
| x-api-key | API key from api.data.gov.  For sample purposes, you can use `DEMO_KEY` as an API key. |

<p><small><a href="#">Back to top</a></small></p>

## OpenAPI Specification File

You can view the full details of this API in the OpenAPI Specification file available here:
<a href="v2/openapi.yaml">Open API specification file for the Digital Analytics Program API</a>

<p><small><a href="#">Back to top</a></small></p>

## The Response

The response represents the rows in the `data` array in the JSON reports that can be downloaded, or the rows in the CSV files that can be downloaded. They are returned as an array of JSON objects. Here is an example of one such object:

```
{
  "id": 60716,
  "report_name": "today",
  "report_agency": "justice",
  "date": "2017-04-07T14:00:00.000Z",
  "visits": "4240",
  "created_at": "2017-04-07T04:23:55.792Z",
  "updated_at": "2017-04-07T04:23:55.792Z"
}
```

Note that is has the following properties:

- `id`: The primary key of the data point
- `report_name`: The name of the data point's report
- `report_agency`: The name of the data point's agency
- `date`: The data/time the data in the data point corresponds to
- `visits`: The requested visit data for the data point.  This is shown as an example of possible data fields that will be included as siblings to the required properties above.  Properties such as visits, browser, screen size, and so on, can be included depending on the report.

## Querying reports

Reports can be queried by substituting `<report name>` in the path with the name of the report.

The following reports can be queried using the API:

- download  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/download/data?api_key=DEMO_KEY1))_
- traffic-source  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/traffic-source/data?api_key=DEMO_KEY1))_
- device-model  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/device-model/data?api_key=DEMO_KEY1))_
- domain  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/domain/data?api_key=DEMO_KEY1))_
- site  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/site/data?api_key=DEMO_KEY1))_
- second-level-domain  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/second-level-domain/data?api_key=DEMO_KEY1))_
- language  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/language/data?api_key=DEMO_KEY1))_
- os-browser  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/os-browser/data?api_key=DEMO_KEY1))_
- windows-browser  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/windows-browser/data?api_key=DEMO_KEY1))_
- browser  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/browser/data?api_key=DEMO_KEY1))_
- windows-ie  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/windows-ie/data?api_key=DEMO_KEY1))_
- os  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/os/data?api_key=DEMO_KEY1))_
- windows  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/windows/data?api_key=DEMO_KEY1))_
- ie  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/ie/data?api_key=DEMO_KEY1))_
- device  _([example](https://api.gsa.gov/analytics/dap/v2.0.0/reports/device/data?api_key=DEMO_KEY1))_

## Filtering based on agencies

Reports can be queried by substituting `<agency name>` in the path with the name of the agency. If the path without an agency name parameter is used, the reports correspond to government wide data.

The list of valid agency names includes:

| agency | API agency name | example API call for the agency |
| --------- | --------- | --------- |
| Agency for International Development | agency-international-development | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/agency-international-development/reports/site/data?api_key=DEMO_KEY1) |
| American Battle Monuments Commission | american-battle-monuments-commission | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/american-battle-monuments-commission/reports/site/data?api_key=DEMO_KEY1) |
| Commodity Futures Trading Commission | commodity-futures-trading-commission | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/commodity-futures-trading-commission/reports/site/data?api_key=DEMO_KEY1) |
| Consumer Financial Protection Bureau | consumer-financial-protection-bureau | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/consumer-financial-protection-bureau/reports/site/data?api_key=DEMO_KEY1) |
| Consumer Product Safety Commission | consumer-product-safety-commission | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/consumer-product-safety-commission/reports/site/data?api_key=DEMO_KEY1) |
| Corporation for National and Community Service | corporation-national-community-service | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/corporation-national-community-service/reports/site/data?api_key=DEMO_KEY1) |
| Defense Nuclear Facilities Safety Board | defense-nuclear-facilities-safety-board | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/defense-nuclear-facilities-safety-board/reports/site/data?api_key=DEMO_KEY1) |
| Department of Agriculture | agriculture | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/agriculture/reports/site/data?api_key=DEMO_KEY1) |
| Department of Commerce | commerce | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/commerce/reports/site/data?api_key=DEMO_KEY1) |
| Department of Defense | defense  | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/defense/reports/site/data?api_key=DEMO_KEY1) |
| Department of Education | education | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/education/reports/site/data?api_key=DEMO_KEY1) |
| Department of Energy | energy  | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/energy/reports/site/data?api_key=DEMO_KEY1) |
| Department of Health and Human Services | health-human-services | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/health-human-services/reports/site/data?api_key=DEMO_KEY1) |
| Department of Homeland Security | homeland-security | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/homeland-security/reports/site/data?api_key=DEMO_KEY1) |
| Department of Housing and Urban Development | housing-urban-development | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/housing-urban-development/reports/site/data?api_key=DEMO_KEY1) |
| Department of the Interior | interior | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/interior/reports/site/data?api_key=DEMO_KEY1) |
| Department of Justice | justice | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/justice/reports/site/data?api_key=DEMO_KEY1) |
| Department of Labor | labor | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/labor/reports/site/data?api_key=DEMO_KEY1) |
| Department of State | state | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/state/reports/site/data?api_key=DEMO_KEY1) |
| Department of Transportation | transportation | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/transportation/reports/site/data?api_key=DEMO_KEY1) |
| Department of the Treasury | treasury | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/treasury/reports/site/data?api_key=DEMO_KEY1) |
| Department of Veterans Affairs | veterans-affairs | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/veterans-affairs/reports/site/data?api_key=DEMO_KEY1) |
| Environmental Protection Agency | environmental-protection-agency | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/environmental-protection-agency/reports/site/data?api_key=DEMO_KEY1) |
| Equal Employment Opportunity Commission | equal-employment-opportunity-commission | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/equal-employment-opportunity-commission/reports/site/data?api_key=DEMO_KEY1) |
| Executive Office of the President | executive-office-president | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/executive-office-president/reports/site/data?api_key=DEMO_KEY1) |
| Farm Credit Administration | farm-credit-administration | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/farm-credit-administration/reports/site/data?api_key=DEMO_KEY1) |
| Federal Deposit Insurance Corporation | federal-deposit-insurance-corporation | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/federal-deposit-insurance-corporation/reports/site/data?api_key=DEMO_KEY1) |
| Federal Election Commission | federal-election-commission | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/federal-election-commission/reports/site/data?api_key=DEMO_KEY1) |
| Federal Energy Regulatory Commission | federal-energy-regulatory-commission | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/federal-energy-regulatory-commission/reports/site/data?api_key=DEMO_KEY1) |
| Federal Housing Finance Agency | federal-housing-finance-agency | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/federal-housing-finance-agency/reports/site/data?api_key=DEMO_KEY1) |
| Federal Maritime Commission | federal-maritime-commission | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/federal-maritime-commission/reports/site/data?api_key=DEMO_KEY1) |
| Federal Mine Safety and Health Review Commission | federal-mine-safety-health-review-commission | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/federal-mine-safety-health-review-commission/reports/site/data?api_key=DEMO_KEY1) |
| Federal Retirement Thrift Investment Board | federal-retirement-thrift-investment-board | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/federal-retirement-thrift-investment-board/reports/site/data?api_key=DEMO_KEY1) |
| Federal Trade Commission | federal-trade-commission | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/federal-trade-commission/reports/site/data?api_key=DEMO_KEY1) |
| General Services Administration | general-services-administration | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/general-services-administration/reports/site/data?api_key=DEMO_KEY1) |
| Institute of Museum and Library Services | institute-museum-library-services | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/institute-museum-library-services/reports/site/data?api_key=DEMO_KEY1) |
| Inter-American Foundation | inter-american-foundation | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/inter-american-foundation/reports/site/data?api_key=DEMO_KEY1) |
| International Development Finance Corporation | international-development-finance-corporation | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/international-development-finance-corporation/reports/site/data?api_key=DEMO_KEY1) |
| Merit Systems Protection Board | merit-systems-protection-board | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/merit-systems-protection-board/reports/site/data?api_key=DEMO_KEY1) |
| Millennium Challenge Corporation | millennium-challenge-corporation | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/millennium-challenge-corporation/reports/site/data?api_key=DEMO_KEY1) |
| National Aeronautics and Space Administration | national-aeronautics-space-administration | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/national-aeronautics-space-administration/reports/site/data?api_key=DEMO_KEY1) |
| National Archives and Records Administration | national-archives-records-administration | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/national-archives-records-administration/reports/site/data?api_key=DEMO_KEY1) |
| National Capital Planning Commission | national-capital-planning-commission | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/national-capital-planning-commission/reports/site/data?api_key=DEMO_KEY1) |
| National Council on Disability | national-council-disability | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/national-council-disability/reports/site/data?api_key=DEMO_KEY1) |
| National Credit Union Administration | national-credit-union-administration | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/national-credit-union-administration/reports/site/data?api_key=DEMO_KEY1) |
| National Education Association | national-education-association | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/national-education-association/reports/site/data?api_key=DEMO_KEY1) |
| National Endowment For The Humanities | national-endowment-humanities | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/national-endowment-humanities/reports/site/data?api_key=DEMO_KEY1) |
| National Labor Relations Board | national-labor-relations-board | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/national-labor-relations-board/reports/site/data?api_key=DEMO_KEY1) |
| National Mediation Board | national-mediation-board | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/national-mediation-board/reports/site/data?api_key=DEMO_KEY1) |
| National Reconnaissance Office | national-reconnaissance-office | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/national-reconnaissance-office/reports/site/data?api_key=DEMO_KEY1) |
| National Science Foundation | national-science-foundation | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/national-science-foundation/reports/site/data?api_key=DEMO_KEY1) |
| National Transportation Safety Board | national-transportation-safety-board | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/national-transportation-safety-board/reports/site/data?api_key=DEMO_KEY1) |
| Nuclear Regulatory Commission | nuclear-regulatory-commission | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/nuclear-regulatory-commission/reports/site/data?api_key=DEMO_KEY1) |
| Nuclear Waste Technical Review Board | nuclear-waste-technical-review-board | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/nuclear-waste-technical-review-board/reports/site/data?api_key=DEMO_KEY1) |
| Office of the Director of National Intelligence | office-director-national-intelligence | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/office-director-national-intelligence/reports/site/data?api_key=DEMO_KEY1) |
| Office of Government Ethics | office-government-ethics | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/office-government-ethics/reports/site/data?api_key=DEMO_KEY1) |
| Office of Navajo and Hopi Indian Relocation | office-navajo-hopi-indian-relocation | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/office-navajo-hopi-indian-relocation/reports/site/data?api_key=DEMO_KEY1) |
| Office of Personnel Management | office-personnel-management | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/office-personnel-management/reports/site/data?api_key=DEMO_KEY1) |
| Peace Corps | peace-corps | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/peace-corps/reports/site/data?api_key=DEMO_KEY1) |
| Pension Benefit Guaranty Corporation | pension-benefit-guaranty-corporation | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/pension-benefit-guaranty-corporation/reports/site/data?api_key=DEMO_KEY1) |
| Postal Regulatory Commission | postal-regulatory-commission | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/postal-regulatory-commission/reports/site/data?api_key=DEMO_KEY1) |
| Privacy and Civil Liberties Oversight Board | privacy-civil-liberties-oversight-board | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/privacy-civil-liberties-oversight-board/reports/site/data?api_key=DEMO_KEY1) |
| Public Buildings Reform Board | public-buildings-reform-board | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/public-buildings-reform-board/reports/site/data?api_key=DEMO_KEY1) |
| Securities and Exchange Commission | securities-exchange-commission | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/securities-exchange-commission/reports/site/data?api_key=DEMO_KEY1) |
| Small Business Adminstration | small-business-administration | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/small-business-administration/reports/site/data?api_key=DEMO_KEY1) |
| Social Security Administration | social-security-administration | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/social-security-administration/reports/site/data?api_key=DEMO_KEY1) |
| Special Inspector General for Afghanistan Reconstruction | special-inspector-general-afghanistan-restoration | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/special-inspector-general-afghanistan-restoration/reports/site/data?api_key=DEMO_KEY1) |
| Surface Transportation Board | surface-transportation-board | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/surface-transportation-board/reports/site/data?api_key=DEMO_KEY1) |
| Udall Foundation | udall-foundation | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/udall-foundation/reports/site/data?api_key=DEMO_KEY1) |
| U.S. Access Board | access-board | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/access-board/reports/site/data?api_key=DEMO_KEY1) |
| U.S. Agency for Global Media | agency-global-media | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/agency-global-media/reports/site/data?api_key=DEMO_KEY1) |
| U.S. Commission on Civil Rights | commission-civil-rights | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/commission-civil-rights/reports/site/data?api_key=DEMO_KEY1) |
| U.S. International Trade Commission | international-trade-commission | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/international-trade-commission/reports/site/data?api_key=DEMO_KEY1) |
| U.S. Postal Inspection Service | postal-inspection-service | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/postal-inspection-service/reports/site/data?api_key=DEMO_KEY1) |
| U.S. Postal Service | postal-service | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/postal-service/reports/site/data?api_key=DEMO_KEY1) |
| U.S. Railroad Retirement Board | railroad-retirement-board | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/railroad-retirement-board/reports/site/data?api_key=DEMO_KEY1) |
| U.S. Trade and Development Agency | trade-development-agency | [example](https://api.gsa.gov/analytics/dap/v2.0.0/agencies/trade-development-agency/reports/site/data?api_key=DEMO_KEY1) |

## Filtering by domain
For the `site`, `domain`, `download`, and `second-level-domain` reports you may use the `domain` route, to only return results by domain.

## Query params

The following query params are supported to work with the data:

- `limit`: Limit the number of data points that are rendered. The default is 1000 and the max is 10,000
- `page`: Pages through the results. If the limit is set to `1000`, using `page=2` will render the 1001st through 2000th data point.
- `after`: Limit the results to in dates on or after the date specified. Expects `YYYY-MM-DD`.
- `before`: Limit the results to in dates on or before the date specified. Expects `YYYY-MM-DD`.

## HTTP Response Codes

The API will return one of the following responses:

| HTTP Response Code | Description |
| ---- | ----------- |
| 200 | Successful. Data will be returned in JSON format. |
| 400 | Bad request. Verify the query string parmaters that were provided. |
| 403 | API key is not correct or was not provided. |
| 4XX | Additional 400-level are caused by some type of error in the information submitted. |

<p><small><a href="#">Back to top</a></small></p>

## Migrating from API V1 to API V2

### Background

Analytics API V1 returns data from Google Analytics V3, also known as Universal
Analytics (UA).

Google is retiring UA and is encouraging users to move to their new
version Google Analytics V4 (GA4) in 2024.

Analytics API V2 returns data from GA4.

### Migration details

#### Requests

The Analytics API endpoints are the same between V1 and V2, the only difference
for API requests is the API version string.

#### Responses

Response data is slightly different in Analytics API V2.  This change is due to
the data provided by Google Analytics. Some data fields were retired in GA4, and
some other useful data fields were added. The changes follow:

##### Deprecated fields

- browser_version
- has_social_referral
- exits
- exit_page

##### New fields

###### bounce_rate

The percentage of sessions that were not engaged.  GA4 defines engaged as a
session that lasts longer than 10 seconds or has multiple pageviews.

###### file_name

The page path of a downloaded file.

###### language_code

The ISO639 language setting of the user's device.  e.g. 'en-us'

###### session_default_channel_group

An enum which describes the session. Possible values:

'Direct', 'Organic Search', 'Paid Social', 'Organic Social', 'Email',
'Affiliates', 'Referral', 'Paid Search', 'Video', and 'Display'

<p><small><a href="#">Back to top</a></small></p>

## Contact Us

To suggest a feature or ask for help, please [file an issue in our project repository](https://github.com/18F/analytics.usa.gov/issues).

<p><small><a href="#">Back to top</a></small></p>
