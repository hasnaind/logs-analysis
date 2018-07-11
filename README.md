# Logs Analysis
> Hasnan Yaqoob
## About
Logs analysis project of udacity fullstack web developer nanodegree. In this project, a large database with over a million rows is explored by building complex SQL queries to draw business conclusions for the data. The project mimics building an internal reporting tool for a newpaper site to discover what kind of articles the site's readers like. The database contains newspaper articles, as well as the web server log for the site.
# Required Libraries and Dependencies
You will following softwares to run this project.
* Python 3.
* Virtual Box.
* Vagrant.
# Setup
1. Install virtual box.
2. Install vagrant.
3. Download virtual machine configuration files.
4. Run <code>vagrant up</code> command in vagrant directry in terminal.
5. Run <code>vagrant ssh</code> command to login to virtual machine.
  
# To Run the app 
To load the data, use the command <code>psql -d news -f newsdata.sql</code> to connect a database and run the necessary SQL statements.
To execute the program, run python newsdata.py from the command line.

# The Database
The database includes following tables.
* Authors table.
* Article table.
* Log table.

# Viwes Made

* Popular_Articles
> create or replace view popular_articles as

> select title, count(title) as views from articles,log
where log.path = concat('/article/',articles.slug)
group by title order by views desc
* Popular_Authors
> create or replace view popular_authors as
select authors.name, count(articles.author) as views from articles, log, authors
where log.path = concat('/article/',articles.slug) and articles.author = authors.id
group by authors.name order by views desc
* Log_status
> create or replace view log_status as
select Date,Total,Error, (Error::float*100)/Total::float as Percent from
(select time::timestamp::date as Date, count(status) as Total,
sum(case when status = '404 NOT FOUND' then 1 else 0 end) as Error from log
group by time::timestamp::date) as result
where (Error::float*100)/Total::float > 1.0 order by Percent desc;
