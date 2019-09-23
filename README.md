# I/O CNA Adobe Analytics Core SDK
Javascript Core SDK wrapping [Adobe Analytics 2.0 APIs](https://adobedocs.github.io/analytics-2.0-apis/#/).


### Installing

```bash
$ npm install
```

### Usage
1) Initialize the SDK

```
var sdk = require('adobeio-cna-core-analytics');

async function sdkTest() {
  //initialize sdk
  const analyticsClient = await sdk.init('<companyID>', 'x-api-key', '<valid auth token>')
}
```
Init method returns an Instance of Class [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)

2) Call methods using initialized sdk

```
var sdk = require('adobeio-cna-core-analytics');

async function sdkTest() {
    //initialize sdk
    const analyticsClient = await sdk.init('<companyID>', 'x-api-key', '<valid auth token>')

    //get report suites
    const collections = await analyticsClient.getCollections({limit:5, page:0})

    //get metrics
    const metrics = await analyticsClient.getMetrics(rsid)

    //generate report
    const report = await analyticsClient.getReport(queryJSON)
}
```
All Methods available under sdk are documented [<code>here</code>](#AnalyticsCoreAPI)

<a name="AnalyticsCoreAPI"></a>

## AnalyticsCoreAPI
This class provides methods to call Adobe Analytics APIs.
Before calling any method initialize the instance by calling init method on it
with valid company id, apiKey and auth token

**Kind**: global class  

* [AnalyticsCoreAPI](#AnalyticsCoreAPI)
    * [.init(companyId, apiKey, token)](#AnalyticsCoreAPI+init)
    * [.getCalculatedMetrics(options)](#AnalyticsCoreAPI+getCalculatedMetrics)
    * [.getCalculatedMetricsById(id, options)](#AnalyticsCoreAPI+getCalculatedMetricsById)
    * [.getCollections(options)](#AnalyticsCoreAPI+getCollections)
    * [.getCollectionsById(rsid, options)](#AnalyticsCoreAPI+getCollectionsById)
    * [.getDateRanges(options)](#AnalyticsCoreAPI+getDateRanges)
    * [.getDateRangesById(dateRangeId, options)](#AnalyticsCoreAPI+getDateRangesById)
    * [.getDimensions(rsid, options)](#AnalyticsCoreAPI+getDimensions)
    * [.getDimensionsById(dimensionId, rsid, options)](#AnalyticsCoreAPI+getDimensionsById)
    * [.getMetrics(rsid, options)](#AnalyticsCoreAPI+getMetrics)
    * [.getMetricsById(id, rsid, options)](#AnalyticsCoreAPI+getMetricsById)
    * [.getReport(body)](#AnalyticsCoreAPI+getReport)
    * [.getSegments(options)](#AnalyticsCoreAPI+getSegments)
    * [.validateSegment(rsid, body)](#AnalyticsCoreAPI+validateSegment)
    * [.getUsers(options)](#AnalyticsCoreAPI+getUsers)
    * [.getCurrentUser()](#AnalyticsCoreAPI+getCurrentUser)

<a name="AnalyticsCoreAPI+init"></a>

### analyticsCoreAPI.init(companyId, apiKey, token)
Initialize sdk.

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| companyId | <code>string</code> | company ID to be used with Adobe Analytics. |
| apiKey | <code>string</code> | Your api key |
| token | <code>string</code> | Valid auth token |

<a name="AnalyticsCoreAPI+getCalculatedMetrics"></a>

### analyticsCoreAPI.getCalculatedMetrics(options)
Retrieve many calculated metrics.
A calculated metric response will always include these default items: *id, name, description, rsid, owner, polarity, precision, type
Other attributes can be optionally requested through the 'expansion' field:\n\n*
    modified: Date that the metric was last modified (ISO 8601)
    definition: Calculated metric definition as JSON object
    compatibility: Products that the metric is compatible with
    reportSuiteName*: Also return the friendly Report Suite name for the RSID
    tags*: Gives all existing tags associated with the calculated metric

For more information about calculated metrics go [here](https://github.com/AdobeDocs/analytics-2.0-apis/blob/master/calculatedmetrics.md)

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| options | <code>Object</code> | to control calculated metrics search. |
| options.calculatedMetricFilter |  | Filter list to only include calculated metrics in the specified list\n(comma-delimited list of IDs). |
| options.expansion |  | Comma-delimited list of additional metadata fields\nto include on response. |
| options.limit |  | Number of results per page. Default 10. |
| options.locale |  | Locale. |
| options.name |  | Filter list to only include calculated metrics that contains the Name. |
| options.ownerId |  | Filter list to only include calculated metrics owned by the\nspecified loginId. |
| options.page |  | Page number (base 0 - first page is \"0\"). Default 0. |
| options.rsids |  | Filter list to only include calculated metrics tied to specified\nRSID list (comma-delimited). |
| options.tagNames |  | Filter list to only include calculated metrics that contains one of\nthe tags. |

<a name="AnalyticsCoreAPI+getCalculatedMetricsById"></a>

### analyticsCoreAPI.getCalculatedMetricsById(id, options)
Retrieve a single calculated metric by id.
A calculated metric response will always include these default items: *id, name, description, rsid, owner, polarity, precision, type
Other attributes can be optionally requested through the 'expansion' field:\n\n*
    modified: Date that the metric was last modified (ISO 8601)
    definition: Calculated metric definition as JSON object
    compatibility: Products that the metric is compatible with
    reportSuiteName*: Also return the friendly Report Suite name for the RSID
    tags*: Gives all existing tags associated with the calculated metric

For more information about calculated metrics go [here](https://github.com/AdobeDocs/analytics-2.0-apis/blob/master/calculatedmetrics.md)

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>string</code> | The calculated metric ID to retrieve. |
| options | <code>Object</code> | to control calculated metric result |
| options.expansion |  | Comma-delimited list of additional metadata fields\nto include on response. |
| options.locale |  | Locale. |

<a name="AnalyticsCoreAPI+getCollections"></a>

### analyticsCoreAPI.getCollections(options)
Retrieves report suites that match the given filters.
Returns all report suite types in a single collection.

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| options | <code>Object</code> | to control report suites search. |
| options.expansion |  | Comma-delimited list of additional metadata fields to include on\nresponse. |
| options.limit |  | Number of results per page. Default 10. |
| options.page |  | Page number (base 0 - first page is \"0\"). Default 0. |
| options.rsids |  | Filter list to only include suites in this RSID list\n(comma-delimited). |
| options.rsidContains |  | Filter list to only include suites whose rsid contains rsidContains. |

<a name="AnalyticsCoreAPI+getCollectionsById"></a>

### analyticsCoreAPI.getCollectionsById(rsid, options)
Retrieves report suite by id.
Returns all report suite types in a single collection.

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| rsid | <code>string</code> | The rsid of the suite to return. |
| options | <code>Object</code> | to control eport suites search. |
| options.expansion |  | Comma-delimited list of additional metadata fields to include on\nresponse. |

<a name="AnalyticsCoreAPI+getDateRanges"></a>

### analyticsCoreAPI.getDateRanges(options)
Returns a list of dateranges for the user.
This function allows users to store commonly used date ranges so that they\ncan be reused throughout the product.

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| options | <code>Object</code> | to control date range search. |
| options.expansion |  | Comma-delimited list of additional metadata fields to include on\nresponse. |
| options.filterByIds |  | Filter list to only include date ranges in the specified list\n(comma-delimited list of IDs). |
| options.limit |  | Number of results per page. Default 10. |
| options.locale |  | Locale. |
| options.page |  | Page number (base 0 - first page is \"0\"). Default 0. |

<a name="AnalyticsCoreAPI+getDateRangesById"></a>

### analyticsCoreAPI.getDateRangesById(dateRangeId, options)
Retrieves configuration for a DateRange..

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| dateRangeId | <code>string</code> | The DateRange id for which to retrieve information. |
| options | <code>Object</code> | to control date range result. |
| options.expansion |  | Comma-delimited list of additional metadata fields to include on\nresponse. |
| options.locale |  | Locale. |

<a name="AnalyticsCoreAPI+getDimensions"></a>

### analyticsCoreAPI.getDimensions(rsid, options)
Returns a list of dimensions for a given report suite.

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| rsid | <code>string</code> | A Report Suite ID. |
| options | <code>Object</code> | to control dimensions search. |
| options.classifiable |  | Only include classifiable dimensions. |
| options.expansion |  | Comma-delimited list of additional metadata fields\nto include on response. |
| options.locale |  | Locale. |
| options.reportable |  | Only include dimensions that are valid within a report. |
| options.segmentable |  | Only include dimensions that are valid within a segment. |

<a name="AnalyticsCoreAPI+getDimensionsById"></a>

### analyticsCoreAPI.getDimensionsById(dimensionId, rsid, options)
Returns a dimension for the given report suite and dimension Id.

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| dimensionId | <code>string</code> | The dimension ID. For example a valid id is a value like 'evar1'. |
| rsid | <code>string</code> | A Report Suite ID. |
| options | <code>Object</code> | to control dimension result. |
| options.expansion |  | Comma-delimited list of additional metadata fields\nto include on response. |
| options.locale |  | Locale. |

<a name="AnalyticsCoreAPI+getMetrics"></a>

### analyticsCoreAPI.getMetrics(rsid, options)
Returns a list of metrics for the given report suite.
This returns the metrics list primarily for the Analytics product.
The platform identity API Returns a list of all possible metrics for the supported systems.

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| rsid | <code>string</code> | A Report Suite ID. |
| options | <code>Object</code> | to control dimension result. |
| options.expansion |  | Comma-delimited list of additional metadata fields\nto include on response. |
| options.locale |  | Locale that system named metrics should be returned in. |
| options.segmentable |  | Filter the metrics by if they are valid in a segment. |

<a name="AnalyticsCoreAPI+getMetricsById"></a>

### analyticsCoreAPI.getMetricsById(id, rsid, options)
Returns a metric for the given report suite.
This returns the metrics list primarily for the Analytics product.
The platform identity API Returns a list of all possible metrics for the supported systems.

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>string</code> | The id of the metric for which to retrieve info. Note ids are values\nlike pageviews, not metrics/pageviews. |
| rsid | <code>string</code> | A Report Suite ID. |
| options | <code>Object</code> | to control dimension result. |
| options.expansion |  | Comma-delimited list of additional metadata fields\nto include on response. |
| options.locale |  | Locale that system named metrics should be returned in. |

<a name="AnalyticsCoreAPI+getReport"></a>

### analyticsCoreAPI.getReport(body)
Runs a report for the request.
See the [Reporting User\nGuide](https://github.com/AdobeDocs/analytics-2.0-apis/blob/master/reporting-guide.md) for details.

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| body | <code>Object</code> | report query. |

<a name="AnalyticsCoreAPI+getSegments"></a>

### analyticsCoreAPI.getSegments(options)
Retrieve All Segments.

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| options | <code>Object</code> | to control segments search. |
| options.expansion |  | Comma-delimited list of additional metadata fields\nto include on response. |
| options.includeType |  | Include additional segments not owned by user. The \"all\" option\ntakes precedence over \"shared\". |
| options.limit |  | Number of results per page. Default 10. |
| options.locale |  | Locale that system named metrics should be returned in. |
| options.name |  | Filter list to only include segments that contains the Name. |
| options.page |  | Page number (base 0 - first page is \"0\"). Default 0. |
| options.rsids |  | Filter list to only include segments tied to specified RSID list\n(comma-delimited). |
| options.segmentFilter |  | Filter list to only include segments in the specified list\n(comma-delimited list of IDs). |
| options.tagNames |  | Filter list to only include segments that contains one of the tags. |

<a name="AnalyticsCoreAPI+validateSegment"></a>

### analyticsCoreAPI.validateSegment(rsid, body)
Validate a Segment.
Returns a segment validation for the segment contained in the post body of the report.

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| rsid | <code>string</code> | A Report Suite ID. |
| body | <code>Object</code> | JSON Segment Definition. |

<a name="AnalyticsCoreAPI+getUsers"></a>

### analyticsCoreAPI.getUsers(options)
Returns a list of users for the current user's login company.
Retrieves a list of all users for the company designated by the auth\ntoken.

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  

| Param | Type | Description |
| --- | --- | --- |
| options | <code>Object</code> | to control user search. |
| options.limit |  | Number of results per page. Default 10. |
| options.page |  | Page number (base 0 - first page is \"0\"). Default 0. |

<a name="AnalyticsCoreAPI+getCurrentUser"></a>

### analyticsCoreAPI.getCurrentUser()
Get the current user.

**Kind**: instance method of [<code>AnalyticsCoreAPI</code>](#AnalyticsCoreAPI)  
### Contributing

Contributions are welcome! Read the [Contributing Guide](./.github/CONTRIBUTING.md) for more information.

### Licensing

This project is licensed under the Apache V2 License. See [LICENSE](LICENSE) for more information.
