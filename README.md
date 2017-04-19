# Ruby script for transferring Postgres databases.

Based on ddollar's [heroku-pg-transfer](https://github.com/ddollar/heroku-pg-transfer) plugin.

	$ ./pg-transfer --help

	Usage: ./pg-transfer [options]
		-a, --app APP_NAME               Destination APP (get to URL from heroku DATABASE_URL config)
		-f, --from URL                   Source database URL
		-t, --to URL                     Target database URL
		-b, --tables-include TABLE_LIST  Tables to copy, defaults to all
		-B, --tables-exclude TABLE_LIST  Tables to exclude, defaults to none

Example:

	Transfer local database to app
	$ ./pg-transfer --from postgres://localhost/app-cz_development --app app-cz-staging-pr-276

	Transfer app database to local
	$ ./pg-transfer --to postgres://localhost/app-cz_development --app app-cz-staging-pr-276

	$ ./pg-transfer --from postgres://user1:pass1@host1/db1 --to postgres://user2:pass2@host2/db2

	Source database: db1 on host1:5432
	Target database: db2 on host2:5432
	Are you sure? [y/n]
	y
	pg_dump: reading extensions
	pg_dump: identifying extension members
	pg_dump: reading schemas
	...
	pg_restore: connecting to database for restore
	...
