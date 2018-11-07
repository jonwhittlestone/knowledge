# Useful MySQL queries

## Run a query and export to a tab delimited file
    
    $ mysql -h sites-app-production-cluster.cluster-cae2rl5vpqei.eu-west-1.rds.amazonaws.com -u eb_tm -p ebury < ~/swiss_clients.sql > ~/swiss_clients.csv

## Basic Join

    SELECT `t`.id, `t`.merchant_name, `t`.payment_id, `t`.action_status, `t`.payment_date, `t`.resolved_at, `t`.created_at, `t`.request_currency, (`t`.request_amount/100) as 'request_amount', (`t`.gbp_equivalent/100) as 'gbp_equivalent', `t`.payer_individual_name, `t`.payer_company_name, `t`.ben_individual_name, `t`.ben_company_name, 
    `a`.note, `note_user`.name as 'note_user_name',
    `cl`.title as 'check_log_title',
    `cl`.message as 'check_log_message'
    FROM `transactions` as t
    JOIN attachments as `a`
    ON `a`.attachable_id=`t`.id
    JOIN users as `note_user`
    ON `note_user`.id = `a`.user_id
    JOIN check_logs as `cl`
    ON `t`.id=`cl`.transaction_id
    WHERE `t`.resolved_at IS NOT null 
    AND `t`.`action_status`='accepted'
    AND `a`.attachable_type='App\\Transactions\\Transaction'
    AND `cl`.level = 30
    ORDER BY `t`.id, `t`.resolved_at DESC

## Daily percentage change

source: https://stackoverflow.com/questions/13671230/how-to-calculate-percentage-increase-from-previous-row-day-after-complex-group-b

- creating the table

    CREATE TABLE `pc_change` (
            `ticker` varchar(10) NOT NULL DEFAULT '',
            `datetime` datetime NOT NULL,
            `volume` mediumint(11) unsigned NOT NULL,
            `open` decimal(8,4) unsigned NOT NULL,
            `high` decimal(8,4) unsigned NOT NULL,
            `low` decimal(8,4) unsigned NOT NULL,
            `close` decimal(8,4) unsigned NOT NULL,
            PRIMARY KEY (`datetime`,`ticker`),
            UNIQUE KEY `indxTickerDatetime` (`ticker`,`datetime`) USING BTREE

            )
            
- getting the percentage change in decimal and percentage

    select ticker, date_format(datetime,'%m-%d-%Y') as date, open, high,low,close,
           pxchange,concat(round(pxpct*100,4),'%') pxpct
           from (
                   select 
                   case when ticker <> @pxticker 
                   then @pxclose := null
                   end, 
                   p.*, 
                   (close-@pxclose) as pxchange,
                   (close-@pxclose)/@pxclose as pxpct,
                   (@pxclose := close),
                   (@pxticker := ticker) 
                   from pc_change p
                   cross join
                   (
                    select 
                    @pxclose := null, 
                    @pxticker := ticker
                    from pc_change 
                    order by ticker, datetime limit 1

                   )  as a
                   order by ticker, datetime 

           ) as b
           order by ticker, datetime asc
