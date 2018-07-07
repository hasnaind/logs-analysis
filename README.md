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
4. Run <code>vagrant up<code> command in vagrant directry in terminal.
5. Run <code>vagrant ssh<code> command to login to virtual machine.
  
# To Run the app 
To load the data, use the command <code>psql -d news -f newsdata.sql<code> to connect a database and run the necessary SQL statements.
To execute the program, run python3 newsdata.py from the command line.

# The Database
The database includes following tables.
* Authors table.
* Article table.
* Log table.
