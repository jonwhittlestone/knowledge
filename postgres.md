[#](#) Postgres

MySQL/Postgres equivalents
https://makandracards.com/makandra/18579-postgresql-cheat-sheet-for-mysql-lamers

    Connect to psql locally as postgres user         '/Applications/Postgres.app/Contents/Versions/9.6/bin/psql --user=postgres -p5432'
    
    List databases                  `\l`
    
## User Management    
    Show users and roles            `\du`
    Change owner                    `ALTER DATABASE test_howappedmarketing OWNER TO howappedmarketinguser;`
    Create Role                     `CREATE ROLE sentinel SUPERUSER;`
    
## DB Management 
    Create a DB                     `createdb test_howappedmarketing`
    Delete a database               `DROP DATABASE test_howappedmarketing;`
    Create a clone of a DB          `CREATE DATABASE test_howappedmarketing WITH TEMPLATE howappedmarketing;`
    Use Database
    
    
# Querying json  / querying json
Source: https://hackernoon.com/how-to-query-jsonb-beginner-sheet-cheat-4da3aa5082a3

    SELECT * FROM transactions_transaction WHERE data->>'transcation_id' = '6a655beb-b178-4c1d-aacc-b41902f89871';
    
 # Importing zipped postgres dump
 - https://gist.github.com/brock/7a7a70300096632cec30 
 - `tar -czvf 30b92370.sql.tar.gz 30b92370_v2.sql`
 - `gunzip < 30b92370.sql.tar.gz | psql thn_db`
