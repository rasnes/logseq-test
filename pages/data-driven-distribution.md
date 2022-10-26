- {{query (task now)}}
  query-table:: false
-
-
- ## general
- DONE Add scheduler to SAP marketing pipeline
  :LOGBOOK:
  CLOCK: [2022-10-18 Tue 20:00:06]
  CLOCK: [2022-10-18 Tue 20:00:13]--[2022-10-18 Tue 21:35:53] =>  01:35:40
  CLOCK: [2022-10-25 Tue 13:14:35]--[2022-10-25 Tue 15:08:29] =>  01:53:54
  :END:
- LATER Remove dangling containers in europe-north1 (manually)
  :LOGBOOK:
  CLOCK: [2022-10-19 Wed 15:49:33]--[2022-10-25 Tue 13:14:42] =>  141:25:09
  :END:
- NOW Set up dev environment before starting on the dashboard?
  :LOGBOOK:
  CLOCK: [2022-10-25 Tue 13:14:47]
  :END:
- LATER make it easy to touch a file in both `test` and `production`
  collapsed:: true
	- Alternative in pure python: `bucket.get_blob(blob_name).update()` , it seems to do the same as `touch` , to update the metadata to most recent.
	- This should be made in the datafactory-data project.
- LATER Jinja - rename config-template.json to config.template.json.jinja.
- LATER add `pre-commit` to the repository?
  collapsed:: true
	- Seems like a nice tool, and could be a good experience to try out. Should include tools: black, flake8, spellcheck, something that checks Makefiles.
- LATER `rclone` sftp to bucket sync: add lifecycle policy for the files to delete files after some time? 2 years?
- LATER add proper logging to pipelines (not just `print`?) `print` seems to log fine though, so maybe not necessary?
- LATER Terraform: add file on APIs in shared.
- DONE Terraform: move `goblet-members-export` Artifact Registry to `europe-west1`
  :LOGBOOK:
  CLOCK: [2022-10-20 Thu 20:15:22]
  CLOCK: [2022-10-20 Thu 20:15:23]--[2022-10-25 Tue 10:44:25] =>  110:29:02
  :END:
-
- DONE check how `posten_routes` is created, how does it create `ContactUUID`?
  :LOGBOOK:
  CLOCK: [2022-10-19 Wed 09:41:37]
  CLOCK: [2022-10-19 Wed 09:42:00]--[2022-10-19 Wed 12:25:36] =>  02:43:36
  :END:
- ## dashboard
- LATER Make Coop øst (Alexander) work
  collapsed:: true
  :LOGBOOK:
  CLOCK: [2022-10-18 Tue 20:26:29]
  CLOCK: [2022-10-18 Tue 20:26:57]--[2022-10-19 Wed 15:37:49] =>  19:10:52
  :END:
	- dbt: configure to read the new imported file `members-routes`
	- dbt blocker: `final_routes` should be able to filter on `s-lag` and `store`
	- Update references in dashboard. Ask Kari for the list.
- NOW grant myself permissions to configure OAuth2 via clickops
  collapsed:: true
  :LOGBOOK:
  CLOCK: [2022-10-18 Tue 20:33:39]
  CLOCK: [2022-10-18 Tue 20:33:45]
  :END:
	- For both `test` and `production` envs
- NOW add Norsk Butikkdrift CSV to the folder `dashboard/data` and import with polars and join with API request results
  :LOGBOOK:
  CLOCK: [2022-10-18 Tue 20:54:41]
  CLOCK: [2022-10-18 Tue 20:54:43]
  :END:
- NOW parametrize OAuth2 config, so that it will fetch the right credentials for the different envs/projects
  collapsed:: true
  :LOGBOOK:
  CLOCK: [2022-10-19 Wed 15:50:19]
  :END:
	- How can I do this by both having it working locally and in production? Use secrets in production
- LATER make function that detects a feasible starting zoom for the map.
- LATER deprecate tabs that will not be used in the first version of the dashboard.
- LATER document functions
- NOW parametrize tables queried by project.
  :LOGBOOK:
  CLOCK: [2022-10-18 Tue 21:14:04]
  :END:
- LATER add `mypy` static checks?
- LATER add some unit tests to the most important, high level functions
-
-
-
- ## dbt
- LATER Gammelt oppsett: ta vare på dbt docs, det holder for arkiv.
  collapsed:: true
	- Flytt til mappen `models-archive`
	- Skriv en kort, forklarende README.md
- LATER add sql-fluff linting as part of CI?
- LATER improve `dbt` setup by mimicking `offers-recommendations` setup?
- LATER use authorised views instead of viewerAccess on tables in `aadatastorage-production`?
- LATER turn on `json_logging`?
  collapsed:: true
	- https://github.com/coopnorge/offers-recommendations/blob/main/dbt/profiles.yml#L6
- LATER set up and configure auto-deployment of `dbt docs`
-
- ## pipeline-export
- LATER create a longer term append table with ingested-at partitions and clustering + VIEW/scheduled table to get current state.
- LATER set up alerting for all pipelines.
- LATER add `release.yml` workflows for `members-export`
  :LOGBOOK:
  CLOCK: [2022-10-19 Wed 20:05:05]
  CLOCK: [2022-10-19 Wed 20:05:12]--[2022-10-21 Fri 08:38:28] =>  36:33:16
  CLOCK: [2022-10-25 Tue 10:47:23]--[2022-10-25 Tue 15:08:38] =>  04:21:15
  :END:
- LATER add data tests to the (dataframe to export to) CSV with Great Expectations.
  collapsed:: true
	- Uniqueness test on UniqueKey column (CoopID)
	- A range of rows (minimum 1 mill and max 2, for example)
		- This should be a test for 1 is the number of data points reasonable and 2 do they have consent?
	- Which columns that should not be empty. E.g. phonenumber etc.
- LATER Remove golang code from repo
-
-
- ## documentation
- Include links to Cloud Build history areas, and mention that this may be relevant if you're debugging. In particular, if it seems like your image doesn't reflect latest changes in `test`.
- Explain how clickops were used to enable credentials
-
-
- ## round-off
- LATER delete AZDO projects.