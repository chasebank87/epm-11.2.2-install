# EPM 11.2.2 Install Guide

## Install

> Install instructions have not changed since 11.1.2.4

1. Download EPM 11.2.2 Install files from edelivery.oracle.com
2. Unzip all files to a single location (The path should have no spaces)
3. Run installTool as administrator
   
   ![](./assets/images/demoInstall.gif)

4. Duplicate on the rest of the servers in your deployment. The foundation server must have all the products intended for the environment installed locally in addition to the remote server where the product will live.

## Configuration

> IMPORTANT!! Do not start the configurator until all RCU steps have been completed

1. Create all necessary EPM databases including EPMS_RCU which is required for a successfull configuration. In 11.1.2.4 this was only required for certain products, but in 11.2.2 it is required for all products.

     * Use the following link to help with the creation of your databases: [Oracle Link](https://docs.oracle.com/en/applications/enterprise-performance-management/11.2/hitis/microsoft_sql_server_database_creation_requirements.html)
2. Run the following rcu bat file to create the require infrastructure schemas:
    * middleware home\oracle_commoon\bin\rcu.bat

    ![](./assets/images/rcuRun.gif)
3. Enter connection information for your SQL\Oracle DB server. The user used must be a system admin.

    > I am using localhost because this is a demo server but you will need to use a FQDN for your connection info, escpecially if you are running a distributed environment.
   
    ![](./assets/images/rcuConnection.gif)

4. Select required components, and set the schema password.

    ![](./assets/images/rcuComponents.gif)
5. Confirm all schemas were created successfully.

    ![](./assets/images/rcuSuccess.png)

6. Edit the following file to include the informatin used when creating the infrastructure schemas:
    * D:\Oracle\Middleware\EPMSystem11R1\common\config\11.1.2.0\RCUSchema.properties

      > IMPORTANT!! This file will need to be created on every server in the environment before starting the configurator. This file cannot just be pasted due to password encryption.

      * Use the following link to help with editing the file to fit your environment: [Oracle Link](https://docs.oracle.com/en/applications/enterprise-performance-management/11.2/hitis/updating_rcu_properties_100x6cc886df.html)
  
      ![](./assets/images/rcuProperty.gif)

      ![](./assets/images/rcuPropertyEdit.gif)

7. Run the EPM configuration by running the following bat file as administrator:
      * D:\Oracle\Middleware\EPMSystem11R1\common\config\11.1.2.0\configtool.bat

      ![](./assets/images/configRun.gif)

8. Configure the instance, and enter the Foundation connection information

      ![](./assets/images/configConnection.gif)

9. Configure Foundation only first

    > IMPORTANT!! Uncheck the deploy Java web application to a signle managed server option

    ![](./assets/images/configFND.gif)
    ![](./assets/images/configFND2.gif)

10. If you performed the RCU steps correctly you will get the following check marks:
    
    ![](./assets/images/fndConfigSuccess.png)

    > IMPORTANT!! If you don't get all greens checkboxes then you may have to investigate the config logs to see if you are getting login errors. This would mean the RCU steps were not performed correctly.
11. Once foundation is done you can move forward doing the same thing with all the other products remembering to change the database name for each product (See example below for CALC Manager). If you are on a distributed environment the RCU properties file will need to be edited on each server before starting the configurator. Save the configure web server for the last step.
    
    ![](./assets/images/configDBNameChange.png)

12. Configure Web Server

    ![](./assets/images/configFND2.gif)