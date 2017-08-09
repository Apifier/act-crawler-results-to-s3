# act-crawler-results-to-s3
Apify act to upload results from Apify crawler to AWS S3.
It is designed to run from [crawler finish webhook](https://www.apifier.com/docs#finishWebhookUrl).

## Usage

For a specific crawler set:

### Finish webhook URL (`finishWebhookUrl`)
`https://api.apifier.com/v2/acts/vRrWzZg7LH29horY8/runs?token=APIFIER_API_TOKEN`
You can find Apifier API token on [your Apifier account page](https://www.apifier.com/account#api-integrations).

### Finish webhook data (`finishWebhookData`)
**Example:**
```json
{
  "awsS3Params": {
    "params": {
      "Bucket": "my-bucket"
    },
    "accessKeyId": "JighjGHklkfjh79dfds80",
    "secretAccessKey": "DA4dgweds56hdasdasd"
  },
  "executionResultsParams": {
    "format": "jsonl"
  },
  "itemsPerFile": 1000
}
```

**Parameters:**

**`awsS3Params`** - Overwrites [S3 params](http://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/S3.html#constructor-property). `AccessKeyId`, `secretAccessKey` and `params.Bucket` are required.

**`executionResultsParams`** - Overwrites [Apifier crawler execution results API call parameters](https://www.apifier.com/api-reference#/reference/results/execution-results/get-execution-results).

**`itemsPerFile`** - Number of web pages to store per file in S3. By default it is 1000.
