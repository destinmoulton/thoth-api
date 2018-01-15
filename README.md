### What is thoth?

Thoth is a log system that can be deployed on AWS Lambda. It uses a simple POST request to store data and has a simple query format for getting data.

Thoth is written using the fantastic [Serverless](https://github.com/serverless/) framework.

### Configuration

Custom configuration should be put into a file called private.config.yml. Rename the private.config.template file and replace the configuration values with your own.

### Not REST

This does not create a REST compliant API. Queries are performed via POSTed JSON, not via GET.

### Query Format

Queries to the /query portion of the API are sent via POST request. The queries are run as a DynamoDB "scan" so you can query inside the stored data rather than by key/index.

Example Query:

```
{
	"query": {
		"parts": [
			{
				"name": "app",
				"value": "App Name",
                "comparison": "="
			},
			{
				"name":"type",
				"value": "error",
				"comparison": "=",
                "bool": "AND"
			}
		]
	}
}
```

NOTE: "comparison" defaults to "=" and "bool" defaults to "AND".
