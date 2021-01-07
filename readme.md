# EPM 11.2.2 Install Guide

## Install

> Install instructions have not changed since 11.1.2.4

1. Download EPM 11.2.2 Install files from edelivery.oracle.com
2. Unzip all files to a single location (The path should have no spaces)
3. Run installTool as administrator
   
   ![](./assets/images/demoInstall.gif)

4. Duplicate on the rest of the servers in your deployment. The foundation server must have all the products intended for the environment installed locally in addition to the remote server where the product will live.

## Configuration

1. Create all necessary EPM databases including EPMS_RCU which is required for a successfull configuration. In 11.1.2.4 this was only required for certain products, but in 11.2.2 it is required for all products.

     * Use the following link to help with the creation of your databases: [Oracle Link](https://docs.oracle.com/en/applications/enterprise-performance-management/11.2/hitis/microsoft_sql_server_database_creation_requirements.html)
2. Run the following rcu bat file to create the require infrastructure schemas:
    * middleware home\oracle_commoon\bin\rcu.bat

    ![](./assets/images/rcuRun.gif)
3. Enter connection information for your SQL\Oracle DB server. The user used must be a system admin.
   
   ![](./assets/images/rcuRun.gif)