# Log query

By default, Insight collects node logs, container logs, and Kubernetes audit logs.
In the log query page, you can search for standard output (stdout) logs within the permissions
of your login account. This includes node logs, product logs, Kubernetes audit logs, etc.
You can quickly find the desired logs among a large volume of logs. Additionally, you can
use the source information and contextual raw data of the logs to assist in troubleshooting and issue resolution.

## Prerequisites

The cluster has [insight-agent installed](../../quickstart/install/install-agent.md)
and the application is in __running__ state.

## Query log

1. In the left navigation bar, select __Data Query__ -> __Log Query__ .

    ![Log Query](https://docs.daocloud.io/daocloud-docs-images/docs/en/docs/insight/images/log01.png)

2. After selecting the query criteria, click __Search__ , and the log records in the form of graphs will be displayed. The most recent logs are displayed on top.

    ![Search](https://docs.daocloud.io/daocloud-docs-images/docs/en/docs/insight/images/log02.png)

3. In the __Filter__ panel, switch __Type__ and select __Node__ to check the logs of all nodes in the cluster.

    ![Node](https://docs.daocloud.io/daocloud-docs-images/docs/en/docs/insight/images/log03.png)

4. In the __Filter__ panel, switch __Type__ and select __Event__ to view the logs generated by all Kubernetes events in the cluster.

**Lucene Syntax Explanation:**

1. Use logical operators (AND, OR, NOT, "") to query multiple keywords. For example: keyword1 AND (keyword2 OR keyword3) NOT keyword4.
2. Use a tilde (~) for fuzzy queries. You can optionally specify a parameter after the "~" to control the similarity of the fuzzy query. If not specified, it defaults to 0.5. For example: error~.
3. Use wildcards (*, ?) as single-character placeholders to match any character.
4. Use square brackets [ ] or curly braces { } for range queries. Square brackets [ ] represent a closed interval and include the boundary values. Curly braces { } represent an open interval and exclude the boundary values. Range queries are applicable only to fields that can be sorted, such as numeric fields, date fields, etc. For example: timestamp:[2022-01-01 TO 2022-01-31].
5. For more information, please refer to the [Lucene Syntax Explanation](../../faq/lucene.md).

## View log context

Clicking on the button next to a log will slide out a panel on the right side where you can view the
default 100 lines of context for that log. You can switch the __Display Rows__ option to view more contextual content.

![view](https://docs.daocloud.io/daocloud-docs-images/docs/en/docs/insight/images/log06.png)

## Export log

Click the download button located in the upper right corner of the list.

- You can configure the exported log fields. The available fields may vary depending on the log type,
  with the __Log Content__ field being mandatory.
- You can export the log query results in **.txt** or **.csv** format.

![export](https://docs.daocloud.io/daocloud-docs-images/docs/en/docs/insight/images/log05.png)
