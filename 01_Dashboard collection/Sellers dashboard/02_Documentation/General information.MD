# Documentation regarding the sellers dashboard
There will be a short introduction about the business and then some documentation regarding the dashboard itself.

## TLDR of the business
Runescape 3 is an MMORPG, in this game there are "hard" bosses to defeat. Our service, as well as another competitor offer services to kill those bosses for you. 
The loot can be forced to them and for some titles some boss kills are required. There is also a "harder" game mode which means you can't buy things from a market and have to get the items yourself
Especially for these accounts our services are quite populair as some people struggle with a very specific boss.

All the orders are conducted through discord and are added to a google sheet afterwards. The move to google sheets was my iniative, but wasn't possible with another developer who created the bot for orders and sending thigns to the sheet.
With this in place we have been able to give customers a "rank" when they have sold x amount. This is updated as time goes on, so I haven't included it in the sheet. 

Now we are exploring more options to get more insights, we also have a PR dashboard showing the credentials of services sold (how many bosses and what kind).

## Goal of the dashboard
The goal is mainly to give the business insights in to what they have sold and their standings with other sellers. We have a system in place that rewards "frequent" sellers. 
A few things I have added for interactivity and use of the dashboard itself. Hopefully to create a "incentive" to sell more often too.

## Requirements

### The following pages are now created as per request:
Only 1 page is basically requested with the ability to drill down if need be to see one's own sales made.

The main items they want to see are:
- Favorite services to sell
- Customers served
- Orders completed
- Gp made
- Ranking 

Basically it should the ranking of sellers as well as the ability to filter it down. 
- Filter by Date
- Filter by Serivce type
    - For PvM services allow another way to filter by Boss for example
- Filter by Seller

### Security
It should not be possible to view the name (RSN's) of players. This dashboard will be published on the web, which means anyone has access to the data underneath.
Since it's a ingame company there is no other users on Power BI Service. Therefor RLS or OLS is sadly impossible.
Customers served is something that we need to show though, so I have implemented something through power query editor that generates a random ID in a seperate table.
That table we merge with the completed as a new table and we prevent the previous 2 tables from loading to the dashboard

## Implementation/data
The data itself is all hosted in a google sheets. Fortunately Power BI has a service that connects to google sheets, through a third party though. 
Since there will be multiple dashboards created from the same data, I decided to implement a dataflow on Power BI service and then have the report connect to that.