# Usage and Cost in Tinybird
This data project contains an API endpoint that utilizes the [Service Data Sources](https://www.tinybird.co/docs/monitoring/service-datasources.html) to estimate the total usage and cost of all data sources and pipes in your Tinybird workspace.

The endpoint returns the total processed and stored data:
- Data processed on ingestion from `tinybird.datasources_ops_log`
- Data processed on API requests from `tinybird.pipe_stats`
- Data stored from `tinybird.datasources_storage`

The API accepts 3 parameters to control the result:
- `start_date` and `end_date` to filter the date range (default to yesterday and today, respectively, if either is not defined)
- `resources` to filter on one or more data source or pipe (defaults to all if not defined)

To calculate cost, the endpoint uses the PRO pricing as listed on the [website](https://www.tinybird.co/pricing). For enterprise customers, Tinybird offers volume-based discounts. 

## Working with the Tinybird CLI

To start working with data projects as if they were software projects, first install the Tinybird CLI in a virtual environment.
Check the [CLI documentation](https://docs.tinybird.co/cli.html) for other installation options and troubleshooting.

```bash
python3 -mvenv .e
. .e/bin/activate
pip install tinybird-cli
tb auth --interactive
```

Choose your region: __1__ for _us-east_, __2__ for _eu_

Go to your workspace, copy a token with admin rights and paste it. A new `.tinyb` file will be created.


## Project Description

```bash
├── endpoints
│   └── tb_usage_cost.pipe
```

In the `/endpoints` folder, there is 1 API endpoint:
- `tb_usage_cost` returns the usage and cost for a given date range and resource(s).

Push the data project to your workspace:

```bash
tb push
```
