Architecture of the Content Layer
=========================================

Backup Service
----------------------------------------

The backup service is responsible to create periodic backup of critical data
stored in the content layer.

Content Store Service
----------------------------------------

The content store service is responsible for storing all content in the network
that is not stored in a database.

Database Access Service
----------------------------------------

The database access service is responsible to provide access to data stored in
one of the databases utilized by the network. It mainly acts as a data cache
for the rest of the network to improve performance. It is the only service that
is allowed to communicate with the database storage service.

Database Storage Service
----------------------------------------

The database storage service is in direct contact with the actual databases
utilized by the platform and it is responsible to read and write data to those
databases. Only the database access service is allowed to communicate with
this service.

Update Service
----------------------------------------

The update service is responsible to keep all network nodes and clients up to
date by publishing network updates and provide the clients with locations to
aquire the latest content packages.