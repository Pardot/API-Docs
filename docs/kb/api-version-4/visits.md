
# Querying Visits


## Supported Operations<a name="20559-supported-operations" id="supported-operations"></a>

| **Operation** | **URL Format**                             | **Required Parameters** | **Description**  |
| ------------- | ------------------------------------------ | ----------------------- | -----------------|
| `query` | `/api/visit/version/4/do/query?...` | `user_key, api_key, (ids, visitor_ids, prospect_ids)` | Returns the visits matching the specified criteria parameters. See the [Using Visits](visits) section for a complete description of visit [XML Response Formats](visits#xml-response-formats). Also see [Visit](../object-field-references.md#visit) in [Object Field References](../object-field-references.md). |

## Supported Search Criteria

One of the following parameters must be used when issuing a visits query. A maximum of 200 visits will be returned with each query request. Since these parameter values could be quite large, we recommend using a POST request due to GET request URL character limits.

| **Parameter** | **Datatype**                               | **Options**             | **Description**  |
| ------------- | ------------------------------------------ | ----------------------- | -----------------|
| `ids` | `array` | `<comma_separated_ids>` | Selects visits with the given IDs. The IDs should be comma separated positive integers (no spaces). We recommend using a POST request when providing this criteria.</td>
| `visitor_ids` | `array` | `<comma_separated_ids>` | Selects visits with the given Visitor IDs. The IDs should be comma separated positive integers (no spaces). We recommend using a POST request when providing this criteria. |
| `prospect_ids` | `array` | `<comma_separated_ids>` | Selects visits with the given Prospect IDs. The IDs should be comma separated positive integers (no spaces). We recommend using a POST request when providing this criteria. |

## Manipulating the Result Set

Since `query` result sets are limited to 200 results each, the results returned may not include all the visits matched by the query. To retrieve the remaining results, the following criteria can be used to navigate through the result set.

| **Parameter** | **Datatype**                               | **Options**             | **Description**  |
| ------------- | ------------------------------------------ | ----------------------- | -----------------|
| `limit` | `integer` | `<any_positive_integer>` | Specifies the number of results to be returned. _Default value:_ `200`. **_Note:_** This number cannot be larger than 200. |
| `offset` | `integer` | `<any_positive_integer>` | Specifies the first matching visit to be returned in the query response. The first `offset` matching visits will be omitted from the response. _Default value:_ `0`. **_Example:_** Specifying `offset=400` will return the results starting with the 401st visit matched by the provided criteria. |


## Sort Order

Visits are returned in order of ascending IDs.


## XML Response Format

```
<rsp stat="ok" version="1.0">
    <result>
        <total_results>...</total_results>
        <visit>...</visit>
            ...
    </result>
</rsp>
```

| **Tag** | **Description** |
| ------- | --------------- |
| `<result>` | Contains the resulting visits for the specified query. |
| `<total_results>` | Contains the number of visits selected by this query. If this value is higher than 200, then several query requests may be necessary to retrieve all of the matched visits. |
| `<visit>` | The data for an individual visit. See [Using Visits](visits) for complete descriptions of visit [XML Response Formats](visits#xml-response-formats). Also see [Visit](../object-field-references.md#visit) in [Object Field References](../object-field-references.md). |

# Using Visits


## Supported Operations<a name="14846-supported-operations"></a>

For a complete list of fields involved in visitor operations, see the [Visit](../object-field-references.md#visit) section of [Object Field References](../object-field-references.md).

| **Operation** | **URL Format**   | **Required Parameters** | **Description**  |
| ------------- | ---------------- | ----------------------- | -----------------|
| `read` | `/api/visit/version/4/do/read/id/<id>?...` | `user_key, api_key, id` | Returns the data for the visit specified by `<id>`, including associated visitor page views. `<id>` is the Pardot ID for the target visit. |

<a name="14846-xml-response-formats"></a>

## XML Response Formats

```
<rsp stat="ok" version="1.0">
    <visit>
        ...
        <visitor_page_views>
            <visitor_page_view>
                ...
            </visitor_page_view>
        </visitor_page_views>
    </visit>
</rsp>
```

| **Tag**                    | **Description** |
|----------------------------|-----------------|
| `<visit>` | Parent tag. Contains data fields for target visit.  For complete field listing, see [Visit](../object-field-references.md#visit) in [Object Field References](../object-field-references.md). |
| `<visitor_page_views>` | Contains all visitor page views associated with this visitor.  Contains only `<visitor_page_view>` tags. |
| `<visitor_page_view>` | Contains data fields for a visitor page view.  For complete field listing, see [Visitor Page View](../object-field-references.md#visitor-page-view) in [Object Field References](../object-field-references.md). |
