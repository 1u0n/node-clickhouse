the original repo @apla/clickhouse has bugs:

* when streaming a response, if you didn't specify any format, the default format (Array) breaks the stream
* if you specify a text format (i.e CSV, TSV), the lib will accumulate the whole response instead of streaming it

what I've done:

* send data to the stream in case of text format response
* don't accumulate the response if there's no final callback waiting to be called

how to use this fork:

* you can use method 'query' which returns a stream (you can still pass optional callback to get whole response at the end)
* you can use method 'querying' which return a promise for the whole response
* specify a text, non-json format for your queries, or don't specify any format (lib uses TabSeparated internally)