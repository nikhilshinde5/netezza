# IBM Integrated Analytics System

## Architecture

![Architecture](https://www.ibm.com/docs/en/SSHRBY/com.ibm.swg.im.iias.admin.doc/images/iias_arch.png)

platform utilities
Platform services:
platform manager

NTP-network type protocol
rhel-red hat enterprise linux
gpfs- 
docker->call home, db2 warehouse

call home - reports issue, opening a case to IBM

db2 warehouse- actual database recides




hardware related issue --> system engineer
db2 related issue --> db engineer

main area to focus-> db2 warehouse & web console also docker to some extend

commands:
su apuser
ap sw
ap node
ap ds -> data slice -> db partitions -> total 11 partitions

customers can have 'n' number of servers

command to enter into docker:
docker exec -it dashDB bash
docker ps

super user:db2inst1
su db2inst1

rah date->login to db2 nodes. also for checking if nodes are up

ssh node0103-fab -> for connecting to differrent node
logout->for disconnecting

hostname -> checking curr node

as we have logined through inst1

ps -ef | grep -i db2sys -> processes on curr server(node)

rah ps -ef | grep -i db2sys -> processes on all server (node)


instance is also called as database manager

information about  db2:
db2 get snapshot for dbm | less

db2 list db directory

database entry type -> gives location of db -> indirect=present locally(focus), remote=not present locally

db2 list active databases->check for active db

db2_all "db2 list active database"->checks active db on all partitions

if u want to go partition by use->db2_all

db2 connect to bludb<name_of_db>
db2_all "db2 connect to bludb<name_of_db>"

db2 get db cfg for bludb | less

db2 get dbm cfg |  less 

db2_all "db2 attach to db2inst1;db2 get dbm cfg"

db2_all "db2 connect to blub"

tables are stored under table space

db2pd -> gives comprehensive information about db
db2pd -d bludb bufferpool | less(makes less content as output)

IBMDEFAULTBP -> whenever we create db

We cannot use IBMSYSTEMBP<page_size>.

This all bufferpools are associated with every table space.

db2pd -d bludb -tablespace | less

types of table space
DMS - database manage space (we can manage them) except SYSCATSPACE
SMS - system manage space(managed automatically by system)->they can broke until the size of your file system

SYSCATSPACE -> stores catalog information
TEMPSPACE -> for sorting purpose (provides space for join queries)
SYSTOOLS -> system related purpose
DSMSPACE -> DSM related appliance utility -> DSM
MONSPACE -> is used to serve with console (web console related data)
SYSTOOLSTMPSPACE 
QREPSPACE -> for qrep appliance (replication related tablespace)
USERSAPCE1 -> default tablespace for user purpose



db2 list applications show detail (for showing services)

export DB2NODE=6
db2 terminate
db2 connect bludb
db2 "values current node"

db2pd -d bludb -tablespace -all-members 

every tablespace which starts with SYS is manadatory and automatically created when you install DB2


cd /scratch
ls -tlr | grep -i tbspace

less tbspace -> gives documentation for creating tbspace

every tbspace will be associated with bufferpool

if u miss to give page size db2 will give 4k as size

we cannot alter page size afterwords.


df -h



cd local
cd db2inst1
ls -tlr

cd NODE0010
cd BLUDB
cd T


db2 list database partition group show detail | less



