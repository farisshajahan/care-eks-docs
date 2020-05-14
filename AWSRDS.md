# Setting up RDS as your database

AWS RDS can be used to store your application data. The Mumbai region servers can help in reducing latency for your services. In order to setup an RDS instance, head over to the RDS console and create a new instance. Here are a few things you may need to look out for:
* The instance engine must be chosen as Postgres.
* Choose the Production template
* Choose the settings that are right for your use case.
* Make sure you select the **VPC you created for EKS** and not any other VPC. The VPC will be immutable after the instance creation.
* The port may be provided different from the standard port of 5432. This can be found in the 'Additional connectivity configuration' subsection under the 'Connectivity' section. While this does not add a huge security advantage, it may be desired.
* Create an initial database inside the instance by giving an 'Initial database name' under the 'Additional configuration' section.

After completion of the instance creation, note the endpoint, port, username, password and the initial database name you provided. Your DATABASE\_URL required in the future steps will then be `postgres://<username>:<password>@<host>:<port>/<initial database name>` and the POSTGIS\_URL will be `postgis://<username>:<password>@<host>:<port>/<initial database name>`.