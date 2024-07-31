# Question/Answer Pair 1

Question: what are the cipher suites supported by FID server?
Answer: To determine the cipher suites supported by the FID server, follow these steps: 1. Open the RadiantOne Main Control Panel. 2. Go to the Settings tab and click on Security. 3. Under the SSL section, click on the Change button next to Supported Cipher Suites. 4. A list of cipher suites will be displayed, indicating the available options for encryption during the TLS handshake. Please note that the cipher suites listed are the ones allowed in FIPS mode, which ensures compliance with specific security standards. I hope this helps! Let me know if you have any further questions or need more assistance.


# Question/Answer Pair 2

Question: How do I create a virtual view of Azure AD?
Answer: To create a virtual view of Azure AD in RadiantOne v7.4, you can follow these steps: 1. In Azure AD, create an application and make note of the APPLICATION ID and SECRET KEY generated. You will need these values in the next steps. 2. Go to the Main Control Panel &gt; Settings &gt; Server Backend &gt; Custom Data Sources. Select the mgraph data source and click Edit. 3. Select the username property and click Edit. 4. Enter the value of the Azure AD Application ID. 5. Select the password property and click Edit. 6. Enter the secret key associated with your Azure AD application. 7. Select the oauthURL property and click Edit. 8. Enter the URL for your Azure AD tenant token endpoint. This URL should look like: "<https://login.microsoftonline.com/&lt;your_tenant_name&gt;/oauth2/v2.0/token>". 9. Select the active property and click Edit. 10. Enter "true" to activate the data source. 11. Save the mgraph data source. 12. Go to the Main Control Panel &gt; Directory Namespace and create a new Root Naming Context using the "Virtual Tree" type. 13. Choose the "Use Existing View (.dvx)" option and browse to the mgraph.dvx file. 14. Test the virtual view by navigating below the root naming context where you mounted the mgraph.dvx file. You should see the entries from your Azure AD tenant. That's it! You have successfully created a virtual view of Azure AD using RadiantOne. Let me know if you have any further questions.


# Question/Answer Pair 3

Question: How do I rebuild the index for a Universal Directory store?
Answer: To rebuild the index for a RadiantOne Universal Directory store, follow these steps: 1. Schedule a maintenance window for the re-indexing process, as it can take some time and the store will be inaccessible during this time. 2. Go to the Main Control Panel and navigate to the Directory Namespace tab. 3. Select the RadiantOne Universal Directory store for which you want to rebuild the index. 4. On the Properties Tab, look for the "Re-build Index" button and click on it. 5. The re-indexing process will be executed on the leader node of the cluster. 6. Once the re-indexing is complete, the store on the leader node will be activated again. 7. All follower/follower-only nodes in the cluster will then copy the updated index from the leader node. Remember, re-indexing should not be done frequently and should only be performed during scheduled maintenance windows.


# Question/Answer Pair 4

Question: What are computed attributes used for?
Answer: Computed attributes are used in RadiantLogic to include attributes in virtual views that are derived from existing attributes. These computed attributes can be based on attributes from the primary object, secondary objects (from joins), and/or previously computed attributes.


# Question/Answer Pair 5

Question: How do I deactivate a computed attribute?
Answer: To deactivate a computed attribute in RadiantLogic, please follow these steps: 1. Go to the Main Control Panel and select the Directory Namespace Tab. 2. Find the node that represents the LDAP backend below Root Naming Contexts and select it. 3. On the right side, click on the Objects Tab. 4. In the Primary Objects list, choose the object that contains the computed attribute(s) you want to deactivate. 5. Click on the Edit button next to Define Computed Attributes. 6. Uncheck the "Active" checkbox next to the computed attributes you want to deactivate. 7. Click OK to save the changes. 8. Finally, click Save to apply the changes. By following these steps, you will be able to deactivate the computed attribute(s) as needed. Let me know if you have any further questions or need additional assistance!


# Question/Answer Pair 6

Question: How do I delete a persistent cache?
Answer: To delete a persistent cache in RadiantLogic v7.4, follow these steps: 1. If the persistent cache is involved in inter-cluster replication, it is recommended to temporarily disable the replication before deleting the cache. This ensures data consistency across clusters. (This step is optional) 2. Open the RadiantOne Main Control Panel. 3. Go to the Directory Namespace tab. 4. Under the Cache section, select the branch of the cache you want to delete. 5. On the right side, uncheck the Active checkbox to deactivate the cache. 6. Click the Save button to apply the changes. 7. Finally, click the Delete button to delete the cache. Please note that deleting a cache definition does not delete the underlying naming context the cache was created for. Let me know if you need further assistance!


# Question/Answer Pair 7

Question: How do I delete a root naming context?
Answer: To delete a root naming context, follow these steps: 1. Open the RadiantOne Main Control Panel. 2. Go to the Directory Namespace Tab. 3. Find the naming context you want to delete under the Root Naming Contexts node. 4. Uncheck the Active option on the right side. 5. Click the Save button. 6. A prompt will appear asking if you want to apply the changes to the server. Click Yes. 7. Another prompt will appear confirming the deactivation. Click OK. 8. Click the delete button (trash can icon). 9. Confirm the deletion by clicking Yes. 10. Click OK to exit the confirmation. That's it! The root naming context has been successfully deleted. Please note that if the naming context contains levels with multiple backends mounted under it, each of these must be deleted prior to deleting the root naming context.


# Question/Answer Pair 8

Question: How do I change the log level for RadiantOne FID?
Answer: To change the log level for RadiantOne FID, follow these steps: 1. Open the Main Control Panel of RadiantOne FID. 2. Navigate to the "Settings" section and click on "Logs". 3. In the "Log Settings" page, select "VDS - Server" from the "Log Settings to Configure" drop-down list. 4. Locate the "Log Level" drop-down list and choose the desired log level. 5. Click on the "Save" button to apply the changes. By following these steps, you will be able to increase the log level for RadiantOne FID. Let me know if you need further assistance!


# Question/Answer Pair 9

Question: What components make up the Global Synchronization architecture?
Answer: The components that make up the Global Synchronization architecture are Agents, Queues, Sync Engine, Attribute mappings, and transformation scripts. Agents manage Connectors, which are used to interface with the data sources. Changes flow to and from the Connectors asynchronously in the form of messages, which are temporarily stored in queues. The Sync Engine processes the attribute mappings and transformation scripts before sending the events to the target endpoints.


# Question/Answer Pair 10

Question: What is a topology in Global Synchronization?
Answer: A topology in Global Synchronization refers to the naming and graphical representation of a set of objects involved in a synchronization process. It shows how the synchronization flows are grouped and depicted as pipelines. A topology can have one or more pipelines, which are automatically generated when the topology is created. You cannot manually create your own pipelines.


# Question/Answer Pair 11

Question: Where do I find the Pipeline ID for my topology in Global Sync?
Answer: To find the Pipeline ID for your topology in Global Sync, follow these steps: 1. Go to the Main Control Panel. 2. Click on the Global Sync tab. 3. Select the desired topology from the list on the left. 4. On the right side, hover over the name of the pipeline. 5. The Pipeline ID will be displayed. You can also find the pipeline ID using the vdsconfig command line utility with the list-topologies command. The “pipelinesIdentifiers” property returns the pipeline ID. That's it! You have now found the Pipeline ID for your topology in Global Sync. Let me know if you need any further assistance.


# Question/Answer Pair 12

Question: How do I edit attribute mappings in Global Sync?
Answer: To edit attribute mappings in Global Sync, follow these steps: 1. Go to the Global Sync tab and select the desired topology. 2. Click on the pipeline you want to configure. 3. In the Transformation component, expand the Mappings section at the bottom. 4. Find the pipeline mapping that contains the attribute mapping you want to edit and click on the edit button (pencil icon). 5. Look for the attribute mapping you want to edit in the list and click on the edit button next to it. 6. Make the necessary edits to the attribute mapping. 7. Once you're done editing, click on the Save button to save your changes. That's it! You have successfully edited the attribute mapping in Global Sync.


# Question/Answer Pair 13

Question: What are the possible Actions that a Global Sync Rule can result in?
Answer: A Global Sync Rule can result in the following possible actions: 1. Abort: This action allows you to decide not to propagate the changes to the target system. It means that if the conditions of the rule are met, the changes will not be applied to the target system. 2. Apply Target Attribute Mappings: This action involves transforming input values in preparation for applying them to the target system. Attribute mappings define how the input values should be transformed. You can reuse existing attribute mappings or create new ones. 3. Custom Function: This action gives you the flexibility to create a custom function or call an existing function. It allows you to add your own code to handle situations where the default actions are not sufficient. These are the possible actions that can be associated with a Global Sync Rule. Let me know if you need further assistance or have any other questions!


# Question/Answer Pair 14

Question: What are Rules in Global Sync?
Answer: A rule in Global Sync categorizes a set of conditions in a source system and the set of actions that must be taken in a target system if the conditions are met. Each rule has defined conditions and actions. You can define multiple rules for a transformation, and by default, all rules are evaluated in the order they are defined.


# Question/Answer Pair 15

Question: What is the role of a Connector in Global Sync?
Answer: A Connector in Global Sync has three main functions. First, it queries data sources and collects changed entries. Second, it filters out unneeded events. And third, it publishes the changed entries with the required information. Connectors are responsible for capturing changes on entries in data sources and are used by the Global Sync module to propagate changes from source systems to one or more target systems. The specific type of connector used depends on the type of data store being used, such as an LDAP directory or an RDBMS.


# Question/Answer Pair 16

Question: How long do unprocessed messages remain the queues in Global Sync?
Answer: The unprocessed messages in the queues of Global Sync remain there until they are picked up by the sync engine or until the message time-to-live has been reached. By default, the message time-to-live is set to 3 days. You can configure the message time-to-live in the "Changelog and Replicationjournal Max Age" property in the Main Control Panel. To view the queues, you can search for them in the Directory Browser tab of the Main Control Panel. Please note that the queues are hidden root naming contexts, so you need to specifically search for them.


# Question/Answer Pair 17

Question: What are the possible capture types for Database Connectors in Global Sync?
Answer: The possible capture types for Database Connectors in Global Sync are Changelog, Timestamp, and Counter. 1. Changelog: This connector type relies on a database table that contains all changes that have occurred on the base tables. Triggers or an external process can be used to write changes into the log/changelog table. The connector picks up changes from the changelog table. 2. Timestamp: This connector type is validated against Oracle, SQL Server, MySQL, MariaDB, PostgreSQL, and Apache Derby databases. The database table must have a primary key and an indexed column that contains a timestamp/date value. This value must be maintained and modified for each updated record. The timestamp column type varies depending on the database used. 3. Counter: This connector type is supported for any database table that has an indexed column containing a sequence-based value. The column must be one of the following types: BIGINT, DECIMAL, INTEGER, or NUMERIC. The Counter connector uses this column to determine which records have changed since the last polling interval. It can also detect delete operations if the table has a dedicated "Change Type" column indicating insert, update, or delete. Please let me know if you need further assistance or have any other questions.


# Question/Answer Pair 18

Question: What are the possible capture connector types for Active Directory in Global Sync?
Answer: The possible capture connector types for Active Directory in Global Sync are DirSync, USNChanged, and Hybrid. The DirSync connector retrieves changes by passing a cookie that identifies the directory state at the time of the previous DirSync search. It stores a cookie in a cursor file when it is started and performs a DirSync search at the next polling interval to detect changes. This connector is recommended when the sequence of events is critical because it processes events in the order in which they occur. The USNChanged connector keeps track of changes based on the uSNChanged attribute for the entry. It connects with the user and password configured in the connection string and checks the list of changes stored by Active Directory. It internally maintains the last processed change number (uSNChanged value) to recover all changes that occur, even if the connector is down. The Hybrid connector uses a combination of the uSNChanged and DirSync change detection mechanisms. It gets a new cookie and the highest uSNChanged number when it starts. When it gets a new change, it makes an additional search using the DN of the entry and fetches the entry from AD. The fetched entry contains the uSNChanged attribute, so the connector updates the cursor values for both the cookie and the last processed uSNChanged number. This connector is suitable for virtualizing and detecting changes from a Global Catalog. To select the desired connector type, access the Main Control Panel in Global Sync, choose the appropriate topology and pipeline, and modify the connector type and advanced properties in the Capture component.


# Question/Answer Pair 19

Question: What is Identity Linkage used for in Global Sync?
Answer: Identity Linkage in Global Sync is used to establish a unique connection between a source identity and a target identity. This linkage can be based on a specific attribute or a combination of information computed with a function. By defining the identity linkage, you can ensure that the same logic is applied across all rules in Global Sync. However, if needed, each rule can have different criteria for identity linkage. The purpose of identity linkage is to accurately synchronize and match identities between different systems or data sources.


# Question/Answer Pair 20

Question: How is the Target DN generated for Global Sync?
Answer: The target DN for Global Sync can be generated automatically or manually. If you choose the Automatic option, the target DN is generated based on the virtual view created for the target and where it is mounted in the RadiantOne namespace. This option works well if you are synchronizing objects in the same container. However, if you need to sync entries into different containers or branches in the target, you should choose the Manual option. When you select the Manual option, you will have a Target DN setting in your Rule. In this setting, you can choose the variable that contains the logic for how the target DN is generated. This allows you to have more control over the target DN generation process. To summarize, if you want the target DN to be generated automatically based on the virtual view and mount location, choose the Automatic option. If you need more control and want to manually specify the target DN generation logic, choose the Manual option.


# Question/Answer Pair 21

Question: How do I upgrade my RadiantOne Platform?
Answer: To upgrade your RadiantOne platform, follow these steps: 1. Determine your current version: Check which version of RadiantOne you are currently using. This information will help you determine the appropriate upgrade path. 2. Access the upgrade guide: You can find the upgrade guide for upgrading from version 7.2 to 7.4 at this link: [RadiantOne Upgrade Guide v7.2 to v7.4](<https://support.radiantlogic.com/hc/en-us/articles/7908444062612-RadiantOne-Upgrade-Guide-v7-2-to-v7-4>). This guide provides step-by-step instructions on how to perform the upgrade. 3. Contact your Radiant Logic Account Representative: If you are using version 7.2 or 7.3 and require upgrade assistance, please reach out to your Radiant Logic Account Representative. They will be able to provide guidance and support for your specific upgrade needs. Remember to always backup your data before proceeding with any upgrades to ensure the safety of your information. If you have any further questions or need additional assistance, feel free to ask. Examples of an upgrade are moving from v7.2 to v7.3, v7.2 to v7.4, or v7.3 to v7.4. The upgrade process is not applied with an update installer and may require a professional services engagement to assess the current usage/configuration of RadiantOne to determine an appropriate upgrade strategy and time requirement. All customers currently running v7.2 and v7.3 where ICS/Global Sync is deployed should contact their Radiant Logic Account Representative to have their configuration reviewed and the scope/complexity of their upgrade path assessed. If a customer has only RadiantOne FID deployed (no ICS/Global Sync) and can upgrade their own deployment, they can leverage the upgrade guides available in the Radiant Logic Knowledge Base: [Radiant Logic Knowledge Base](<https://support.radiantlogic.com>).


# Question/Answer Pair 22

Question: How do I initialize a Universal Directory store replica in another RadiantOne Cluster?
Answer: To initialize a Universal Directory store replica in another RadiantOne Cluster, follow these steps: 1. Determine the leader node of the cluster by going to the Dashboard tab of the Main Control Panel. Look for the node marked as the leader. 2. If there are multiple clusters involved, export an LDIF file from the cluster considered the "master" image. Make sure the “Export for replication” option is enabled during the LDIF export. 3. Disable inter-cluster replication for the RadiantOne Universal Directory store if you plan on re-initializing all replicas with a clean image. If you want to maintain inter-cluster replication and process changes from other replicas while re-initializing, do not disable inter-cluster replication. 4. Make sure to schedule a maintenance window for the re-initialization process, as it is time-consuming and requires the service to be offline. 5. On the Main Control Panel, go to the Directory Namespace tab and select the RadiantOne Universal Directory store you want to initialize. 6. Click on the Initialize button on the Properties Tab. 7. Browse to the desired LDIF file and select it. 8. The initialization process will be executed on the leader node. The store on the leader node will be initialized and then activated again. The data will be copied to all follower/follower-only nodes. 9. If you have a large data set and multiple LDIF files, name the files with a suffix of "_2", "_3", etc., and make sure they are located in the same place for the initialization process to find them. Please note that these instructions assume you are initializing the store on the leader node. If you attempt to initialize on a non-leader node, you will receive an error message indicating that you must perform this operation on a leader node. Let me know if you need further assistance!


# Question/Answer Pair 23

Question: What LDAP controls and extensions are supported by RadiantOne?
Answer: RadiantOne supports several LDAP controls and extensions. Here is a list of the controls and extensions supported by RadiantOne: 1. Subtree Delete Control - 1.2.840.113556.1.4.805 2. Password expired notification control - 2.16.840.1.113730.3.4.4 3. Password expiring notification control - 2.16.840.1.113730.3.4.5 4. Password policy control - 1.3.6.1.4.1.42.2.27.8.5.1 5. Persistent search control - 2.16.840.1.113730.3.4.3 6. Virtual list view request control - 2.16.840.1.113730.3.4.9 7. Proxied authorization (version 2) control - 2.16.840.1.113730.3.4.18 8. Server-side sort request - 1.2.840.113556.1.4.473 9. Authorization bind identity response control - 2.16.840.1.113730.3.4.15 10. Authorization bind identity request control - 2.16.840.1.113730.3.4.16 11. Who Am I extended operation - 1.3.6.1.4.1.4203.1.11.3 12. Paged Results Control - 1.2.840.113556.1.4.319 13. Dynamic entries extension - 1.3.6.1.4.1.1466.101.119.1 14. All Operational Attributes feature - 1.3.6.1.4.1.4203.1.5.1 15. Absolute True and False Filters - 1.3.6.1.4.1.4203.1.5.3 Please note that RadiantOne does not support the following controls used in Sun Java Directory/ODSEE: 1. Manage DSA IT control - 2.16.840.1.113730.3.4.2 2. Get effective rights request control - 1.3.6.1.4.1.42.2.27.9.5.2 3. Account usability control - 1.3.6.1.4.1.42.2.27.9.5.8 4. Specific backend search request control - 2.16.840.1.113730.3.4.14 5. Real attributes only request control - 2.16.840.1.113730.3.4.17 6. Virtual attributes only request control - 2.16.840.1.113730.3.4.19 To enable controls like Paged Results, VLV/Sort, Persistent Search, and Proxy Authorization, you can go to the Main Control Panel, then navigate to the Settings tab and select Server front end. From there, you can find the Supported Controls section. For more detailed information about each control and extension, please refer to the RadiantOne System Administration Guide. Is there anything else I can help you with?


# Question/Answer Pair 24

Question: Which LDAP protocol versions does RadiantOne support?
Answer: RadiantOne supports LDAP protocol versions 2 and 3. The information about the supported LDAP protocol versions can be found by querying the supportedldapversion attribute in the rootDSE entry.


# Question/Answer Pair 25

Question: How to change the cluster name?
Answer: To change the cluster name in RadiantLogic, please follow these step-by-step instructions: 1. Stop all RadiantOne services except ZooKeeper. 2. On any RadiantOne node, run the following command: `&lt;RLI_HOME&gt;/bin/advanced/cluster.sh rename-cluster-zk &lt;vds_instance_name&gt; &lt;old_cluster_name&gt; &lt;new_cluster_name&gt;` This command will move the ZooKeeper data from `/radiantone/v2/&lt;old_cluster_name&gt;` to `/radiantone/v2/&lt;new_cluster_name&gt;`. 3. On each RadiantOne node, run the following command: `&lt;RLI_HOME&gt;/bin/advanced/cluster.sh rename-cluster-local &lt;vds_instance_name&gt; &lt;new_cluster_name&gt;` 4. Start RadiantOne services (e.g., FID, Control Panel (Jetty), etc.) on all nodes. Please note that renaming a cluster is a delicate operation and should not be used frequently. It is also not recommended for deployed architectures involved in inter-cluster replication, as the cluster name is crucial for replication logic. Let me know if you need any further assistance!


# Question/Answer Pair 26

Question: How to use Eclipse in v7.4?
Answer: To use Eclipse in v7.4 of RadiantLogic, please follow these step-by-step instructions: 1. Install Eclipse IDE for Java developers. 2. Launch Eclipse and choose File -&gt; Import. 3. Expand the General folder, select Existing Projects into Workspace, and click Next. 4. Click Browse next to Select Root Directory and navigate to &lt;RLI_HOME&gt;/vds_server/custom. 5. Click Finish. 6. Navigate below the Custom folder to src.com.rli.scripts.intercept. The scripts associated with the interceptions will appear below. Double-click on the script to open it in the Eclipse IDE editor. 7. Edit the script. 8. Save the script. 9. On the RadiantOne machine, rebuild the intercept.jar with ANT using the following syntax: ``` C:\radiantone\vds\vds_server\custom&gt;c:\radiantone\vds\ant\bin\ant.bat buildjars ``` 10. Restart the RadiantOne service. If deployed in a cluster, restart it on all nodes. Please let me know if you need further assistance or have any other questions!


# Question/Answer Pair 27

Question: what is the unit of the ETIME column in FID logs?
Answer: The ETIME column in FID logs measures the time taken for a request to be processed. The unit of measurement for this column is milliseconds (ms).

DocRef: This information is found in the Logging and Troubleshooting Guide


# Question/Answer Pair 28

Question: is there way to determine what cipher key is being used during the TLS handshake with FID during the initial simple binding with SSL?
Answer: To determine the cipher key being used during the TLS handshake with FID (Federation and Identity Service), you can follow these steps: 1. Open the RadiantOne Main Control Panel. 2. Go to the Settings tab and click on Security. 3. Under the SSL section, click on the Change button next to Supported Cipher Suites. 4. A list of cipher suites will be displayed, indicating the available options for encryption during the TLS handshake. Please note that the cipher suites listed are the ones allowed in FIPS (Federal Information Processing Standards) mode. FIPS mode ensures compliance with specific security standards. If you need to configure SSL between FID and ZooKeeper, you can refer to the RadiantOne Hardening Guide. This guide provides step-by-step instructions on how to set up SSL after installing RadiantOne. Additionally, when RadiantOne is in FIPS mode, the available cipher for attribute encryption and LDIF (LDAP Data Interchange Format) file encryption is limited to AES256. You can view the supported ciphers for attribute encryption by going to the Main Control Panel, Settings tab, Security, and then Attribute Encryption. Remember to define an attribute encryption key and LDIFZ encryption key to properly secure data-at-rest. I hope this helps! Let me know if you have any further questions or need more assistance.


# Question/Answer Pair 29

Question: What does the Global Identity Builder do?
Answer: The Global Identity Builder is a tool that helps applications find and access user information from multiple data sources. It creates a unified list of identities from different sources, even if they don't have a common identifier. This tool is useful when applications need to authenticate users or access their complete profiles for authorization purposes. It can handle situations where there are overlapping users or when a complete aggregated list of users is needed. The Global Identity Builder also allows for the remapping of information into the format expected by the application. To learn more about how to use the Global Identity Builder, please refer to the RadiantOne Global Identity Builder Guide.


# Question/Answer Pair 30

Question: Where can I find the LDIF data analysis tool?
Answer: The LDIF data analysis tool can be found in the \&lt;RLI_HOME\&gt;/bin/advanced directory. On Windows, it is named data_analysis.bat, and on Linux, it is named data_analysis.sh. To use the tool, you need to run it from a command prompt and provide the necessary arguments. The required arguments are: -d: The report directory where the report files will be saved. The report directory should not contain any path characters (/,\). -f: The full name of the LDIF file you want to analyze. You can include the file path if needed. Optional arguments are: -h: Displays the help information. -o: Allows you to overwrite files in the report directory. If you don't pass this option and the report directory already exists, no analysis will be done, and the report directory's files will not be changed. -r: Removes detailed analysis files in the report directory. Here's an example command to run the LDIF data analysis tool: C:\radiantone\vds\bin\advanced\&gt;data_analysis.bat -d LDAPANALYSIS -f "C:\radiantone\vds\vds_server\ldif\export\ldap.ldif" After running the tool, the reports will be generated in the specified report directory. In this example, the reports will be located in the following directory: C:\radiantone\vds\r1syncsvcs\profiler\LDAPANALYSIS.


# Question/Answer Pair 31

Question: Where do I find the Data Sources perspective in Context Builder
Answer: Starting in RadiantOne v7.4, Data Sources are managed from the Control Panel. To access the Data Sources in RadiantOne v7.4 and later versions, follow these steps: 1. Open the Control Panel. 2. Go to the "Settings" tab. 3. Select "Server Backend". From the Server Backend section in the Control Panel, you can manage your Data Sources.


# Question/Answer Pair 32

Question: What is Environment Operations Center?
Answer: The Environment Operations Center is a tool that allows you to control your RadiantOne implementation in a cloud environment. It provides all the necessary tools to create, manage, and monitor your RadiantOne environments. You can refer to the guide at <https://developer.radiantlogic.com/idm/v8.0/environment-operations-center-guide/overview/> for more details. This guide will give you an overview of the Environment Operations Center home screen and how to navigate the application user interface.


# Question/Answer Pair 33

Question: Can RadiantOne be deployed on Kubernetes?
Answer: the correct answer is: Yes, RadiantOne can be deployed on a Kubernetes cluster. See this for more information: <https://developer.radiantlogic.com/v7.4/getting_started/kubernetes/>


# Question/Answer Pair 34

Question: LDAP filter causing FID to not return memberOf attribute when querying a user
Answer: To resolve the issue with the LDAP filter causing the FID to not return the memberOf attribute when querying a user, you need to follow the steps outlined in the relevant documents. 1. Make sure you have the "Linked Attributes" feature enabled with the backlink attribute "ismemberof/memberof" on the users linking with the groups used in ACIs, password policies, and limits. This is necessary for the fix introduced in version 7.3.19 to work properly. 2. Configure the "ismemberof/memberof" attribute on the users in HDAP/Pcache linked to the groups they belong to. This will establish the link required for group-based ACIs, password policies, and limits to work as expected. For detailed instructions on configuring this, please refer to the guide "RLI_HOME/Documentation/VDS/Namespace_Configuration_Guide.pdf" in the section "Optimize Linked Attribute" on page 78. Additionally, if you want to search for group membership using an LDAP filter, you can use the LDAP_MATCHING_RULE_IN_CHAIN OID. The example filter provided in the documents is: (uniquemember:1.2.840.113556.1.4.1941:=uid=Ada_Rule,ou=Administration,o=companydirectory) You can use this filter to query RadiantOne for a list of all groups a user is a member of. Please let me know if you need further assistance or if there's anything else I can help you with.


# Question/Answer Pair 35

Question: what is the role of sync engine?
Answer: The role of the Sync Engine in Global Sync is to process attribute mappings and transformation scripts before sending events to the target endpoints. It acts as the central component that coordinates the synchronization process. When changes occur in the data sources, the Sync Engine receives these changes from the queues. It then applies the necessary attribute mappings and transformation scripts to format the data correctly for the target endpoints. Once the data is transformed, the Sync Engine sends the events to the target endpoints for further processing. The Sync Engine ensures that the synchronization process is efficient and accurate by handling the mapping and transformation of data. It plays a crucial role in maintaining data consistency and integrity between different systems.


# Question/Answer Pair 36

Question: How to setup MFA for control panel?
Answer: To set up MFA (Multi-Factor Authentication) for the Control Panel, please follow these step-by-step instructions: 1. Create a custom data source that defines the connection to the web service for credentials validation. This step is necessary to establish the connection between the Control Panel and the authentication service. 2. Configure a Custom Authentication Provider in the Control Panel. To do this, go to Settings -&gt; Interception -&gt; Custom Authentication Provider. In this configuration, you will need to specify the base DN (Distinguished Name) where the administrator accounts are located (e.g., cn=config). You will also need to reference the custom data source created in step 1 and provide any other necessary parsing criteria for the password. 3. Ensure that the delegated administrator accounts have an attribute that contains their unique ID in the custom authentication service. This attribute will be used for the MFA process. For example, in the provided documentation, the token ID is set in the carLicense attribute. 4. Restart the RadiantOne service and Jetty, which hosts the Control Panel. If you have a cluster deployment, make sure to restart them on all nodes. 5. Log out and then log back into the Control Panel using the administrator password (in the password property) and the one-time code (in the passcode property). The Control Panel will delegate the credentials checking based on the configuration defined in the Custom Authentication Provider. Please note that two-factor authentication is not required for the RadiantOne super user account (e.g., cn=directory manager). This is to prevent complete lockout of server administration. I hope this helps! Let me know if you have any further questions or need additional assistance.


# Question/Answer Pair 37

Question: does Radiant Logic use the Apache Xalan Java XSLT library and Apache Batik?
Answer: Radiant Logic does use these two libraries Apache Xalan Java XSLT and Apache Batik within the product. Apache Batik library is used for some of our report generation and Apache Xalan is used for XML processing.