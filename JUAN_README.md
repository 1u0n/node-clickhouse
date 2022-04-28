the original repo @apla/clickhouse has bugs:

* when streaming a response, if you didn't specify any format, the default format (Array) breaks the stream
* if you specify a text format (i.e CSV, TSV), the lib will accumulate the whole response instead of streaming it

what I've done:

* send data to the stream in case of text format response
* don't accumulate the response if there's no final callback waiting to be called

how to use this fork:

* always specify a text, non-json format in your queries. You can still specify callback to get the whole response at the end.