# PostgreSQL16 High Availability Lab Setup

This repo contains code for HA database setup for PostgreSQL16 following this [guide](https://www.youtube.com/watch?v=Az6GE5Y5usg&list=PLpm71E6Qw2tCIakNQNQKoxhSOJP3PpNhQ&index=1). The components are:

![](images\Roadmap.png)

## Cluster Diagram

![](images\Diagram.png)

Each node has PostgreSQL16 installed together with RepMGR in order to replicate changes across three nodes. Furthermore, HAProxy and Keepalived is also installed for load balancing and ensure service availability by routing network traffic to a backup server if the primary server fails, as well as maintaining a virtual IP for the whole setup, respectively.

Finally, there is a backup server which contains the backup hard drive; barman; and Postgres Client.

## Conclusion

This setup run on Oracle Linux 9, which is a niche OS so it's usage is rather limited. The guide is also primarily manual work, thus will not be easy to maintain/upgrade. Using Debian; Ansible; and Terraform would be much more robust and convenient.

Functionally, this HA setup share similarity with autobase setup in usages of HAProxy; and Keepalived. But it is far less sophisciated with only a simple backup server managed by pgbarman.
