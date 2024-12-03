# Question/Answer Pair 1

Question: what are the SSL/TLS protocols supported by RadiantOne v7.4?

Answer: To determine the cipher suites supported by the RadiantOne:
The default SSL/TLS protocol options are SSL v3, TLSv1, TLSv1.1 TLSv1.2 and TLS v1.3. Some of the less secure protocols in this list are disabled by default in the <RLI_HOME>/jdk/jre/lib/security/java.security file, noted in the jdk.tls.disabledAlgorithms property.
Out of the available protocols, not in the disabled list, you can limit which ones you want RadiantOne to support. You can limit the protocols from the Main Control Panel > Settings Tab > Security section > SSL sub-section. Click Change next to Enabled SSL Protocols. Select the protocols to support and click OK. Restart the RadiantOne service on all nodes.
If you want to support one of the less secure protocols, edit the java.security file and remove the protocol from the jdk.tls.disabledAlgorithms value. Then, make sure it is enabled in RadiantOne. Restart RadiantOne on all nodes. If a protocol is enabled in RadiantOne, but in the list of disabled algorithms in the java.security file, it will not be supported at runtime for SSL communication.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/sys-admin-guide/06-security/#supported-cipher-suites>


# Question/Answer Pair 2

Question: How do I create a virtual view of Entra ID (formerly named Azure AD) in RadiantOne v7.4?

Answer: To create a virtual view of Entra ID in RadiantOne v7.4, you can follow these steps:
1. In Entra ID, create an application and make note of the APPLICATION ID and SECRET KEY generated. You will need these values in the next steps.
2. Go to the Main Control Panel &gt; Settings &gt; Server Backend &gt; Custom Data Sources. Select the mgraph data source and click Edit.
3. Select the username property and click Edit.
4. Enter the value of the Entra ID Application ID.
5. Select the password property and click Edit.
6. Enter the secret key associated with your Entra ID application.
7. Select the oauthURL property and click Edit.
8. Enter the URL for your Entra ID tenant token endpoint. This URL should look like: "<https://login.microsoftonline.com/&lt;your_tenant_name&gt;/oauth2/v2.0/token>".
9. Select the active property and click Edit.
10. Enter "true" to activate the data source.
11. Save the mgraph data source.
12. Go to the Main Control Panel &gt; Directory Namespace and create a new Root Naming Context using the "Virtual Tree" type.
13. Choose the "Use Existing View (.dvx)" option and browse to the mgraph.dvx file.
14. Test the virtual view by navigating below the root naming context where you mounted the mgraph.dvx file. You should see the entries from your Entra ID tenant.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/namespace-configuration-guide/08-virtual-views-of-cloud-directories-or-services/#azure-active-directory>

# Question/Answer Pair 3

Question: How do I rebuild the index for a RadiantOne Directory store (formerly named HDAP)?

Answer: To rebuild the index for a RadiantOne Directory store, follow these steps:

1. Schedule a maintenance window for the re-indexing process, as it can take some time and the store will be inaccessible during this time.
2. Go to the Main Control Panel and navigate to the Directory Namespace tab.
3. Select the RadiantOne Directory store for which you want to rebuild the index.
4. On the Properties Tab, look for the "Re-build Index" button and click on it.
5. The re-indexing process will be executed on the leader node of the cluster.
6. Once the re-indexing is complete, the store on the leader node will be activated again.
7. All follower/follower-only nodes in the cluster will then copy the updated index from the leader node.
Remember, re-indexing should not be done frequently and should only be performed during scheduled maintenance windows.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/namespace-configuration-guide/05-radiantone-universal-directory/#rebuilding-indexes>

# Question/Answer Pair 4

Question: What are computed attributes used for?

Answer: Computed attributes are used in RadiantOne to include attributes in virtual views that are derived from existing attributes. These computed attributes can be based on attributes from the primary object, secondary objects (from joins), and/or previously computed attributes.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/sys-admin-guide/02-concepts/#computed-attributes>

# Question/Answer Pair 5

Question: How do I deactivate a computed attribute for an LDAP proxy view in RadiantOne v7.4?

Answer: To deactivate a computed attribute in RadiantOne v7.4 for an LDAP proxy view, please follow these steps:

1. Go to the Main Control Panel and select the Directory Namespace Tab.
2. Find the node that represents the LDAP backend below Root Naming Contexts and select it.
3. On the right side, click on the Objects Tab.
4. In the Primary Objects list, choose the object that contains the computed attribute(s) you want to deactivate.
5. Click on the Edit button next to Define Computed Attributes.
6. Uncheck the "Active" checkbox next to the computed attributes you want to deactivate.
7. Click OK to save the changes.
8. Finally, click Save to apply the changes.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/sys-admin-guide/02-concepts/#computed-attributes>

# Question/Answer Pair 6

Question: How do I delete a persistent cache in RadiantOne v7.4?

Answer: To delete a persistent cache in RadiantLogic v7.4, follow these steps:

1. If the persistent cache is involved in inter-cluster replication, it is recommended to temporarily disable the replication before deleting the cache. This ensures data consistency across clusters. (This step is optional)
2. Open the RadiantOne Main Control Panel.
3. Go to the Directory Namespace tab.
4. Under the Cache section, select the branch of the cache you want to delete.
5. On the right side, uncheck the Active checkbox to deactivate the cache.
6. Click the Save button to apply the changes.
7. Finally, click the Delete button to delete the cache.
Please note that deleting a cache definition does not delete the underlying naming context the cache was created for.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/deployment-and-tuning-guide/02-tuning-tips-for-caching-in-radiantone/#deleting-the-persistent-cache>


# Question/Answer Pair 7

Question: How do I delete a root naming context in RadiantOne v7.4?

Answer: To delete a root naming context in RadiantOne v7.4, follow these steps:

1. Open the RadiantOne Main Control Panel.
2. Go to the Directory Namespace Tab.
3. Find the naming context you want to delete under the Root Naming Contexts node.
4. Uncheck the Active option on the right side.
5. Click the Save button.
6. A prompt will appear asking if you want to apply the changes to the server. Click Yes.
7. Another prompt will appear confirming the deactivation. Click OK.
8. Click the delete button (trash can icon).
9. Confirm the deletion by clicking Yes.
10. Click OK to exit the confirmation.
Please note that if the naming context contains levels with multiple backends mounted under it, each of these must be deleted prior to deleting the root naming context.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/namespace-configuration-guide/02-directory-namespace-design/#deleting-naming-contexts>


# Question/Answer Pair 8

Question: How do I change the FID server log levels in RadiantOne v7.4?

Answer: To change the log level for FID in RadiantOne v7.4, follow these steps:

1. Open the Main Control Panel.
2. Navigate to the "Settings" section and click on "Logs".
3. In the "Log Settings" page, select "VDS - Server" from the "Log Settings to Configure" drop-down list.
4. Locate the "Log Level" drop-down list and choose the desired log level.
5. Click on the "Save" button to apply the changes.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/logging-and-troubleshooting-guide/03-radiantone-universal-directory/#radiantone-server-log>


# Question/Answer Pair 9

Question: What components make up the RadiantOne v7.4 Synchronization architecture?

Answer: The components that make up the Synchronization architecture are Agents, Queues, Sync Engine, Attribute mappings, and transformation scripts. Agents manage Connectors, which are used to interface with the data sources. Changes flow to and from the Connectors asynchronously in the form of messages, which are temporarily stored in queues. The Sync Engine processes the attribute mappings and transformation scripts before sending the events to the target endpoints.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/global-sync-guide/introduction/#architecture>

# Question/Answer Pair 10

Question: What is a topology in RadiantOne v7.4 Synchronization?

Answer: A topology in Synchronization refers to the naming and graphical representation of a set of objects involved in a synchronization process. It shows how the synchronization flows are grouped and depicted as pipelines. A topology can have one or more pipelines, which are automatically generated when the topology is created. You cannot manually create your own pipelines.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/global-sync-guide/concepts-and-definitions/topology/>


# Question/Answer Pair 11

Question: Where do I find the Pipeline ID for my topology in RadiantOne v7.4 Synchronization?

Answer: To find the Pipeline ID for your topology in Synchronization, follow these steps:

1. Go to the Main Control Panel.
2. Click on the Synchronization tab.
3. Select the desired topology from the list on the left.
4. On the right side, hover over the name of the pipeline.
5. The Pipeline ID will be displayed.
You can also find the pipeline ID using the vdsconfig command line utility with the list-topologies command. The “pipelinesIdentifiers” property returns the pipeline ID.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/global-sync-guide/concepts-and-definitions/topology/#pipeline-id>


# Question/Answer Pair 12

Question: How do I edit attribute mappings in RadiantOne v7.4 Synchronization?

Answer: To edit attribute mappings in RadiantOne v7.4 Synchronization, follow these steps:

1. Go to the Main Control Panel.
2. Click on the Synchronization tab.
3. Select the desired topology from the list on the left.
4. Click on the pipeline you want to configure.
5. In the Transformation component, expand the Mappings section at the bottom.
6. Find the pipeline mapping that contains the attribute mapping you want to edit and click on the edit button (pencil icon).
7. Look for the attribute mapping you want to edit in the list and click on the edit button next to it.
8. Make the necessary edits to the attribute mapping.
9. Once you're done editing, click on the Save button to save your changes.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/global-sync-guide/configuration/transformation/attribute-mappings/>

# Question/Answer Pair 13

Question: What are the possible Actions that a Synchronization Rule can result in?

Answer: A Synchronization Rule can result in the following possible actions:

1. Abort: This action allows you to decide not to propagate the changes to the target system. It means that if the conditions of the rule are met, the changes will not be applied to the target system.
2. Apply Target Attribute Mappings: This action involves transforming input values in preparation for applying them to the target system. Attribute mappings define how the input values should be transformed. You can reuse existing attribute mappings or create new ones.
3. Custom Function: This action gives you the flexibility to create a custom function or call an existing function. It allows you to add your own code to handle situations where the default actions are not sufficient.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/global-sync-guide/configuration/rules/actions/>

# Question/Answer Pair 14

Question: What are Rules in RadiantOne Synchronization?

Answer: A rule in RadiantOne Synchronization categorizes a set of conditions in a source system and the set of actions that must be taken in a target system if the conditions are met. Each rule has defined conditions and actions. You can define multiple rules for a transformation, and by default, all rules are evaluated in the order they are defined.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/global-sync-guide/configuration/rules/overview/>


# Question/Answer Pair 15

Question: What is the role of a Connector in RadiantOne Synchronization?

Answer: A Connector in Synchronization has three main functions. First, it queries data sources and collects changed entries. Second, it filters out unneeded events. And third, it publishes the changed entries with the required information. Connectors are responsible for capturing changes on entries in data sources and are used by RadiantOne Synchronization to propagate changes from source systems to one or more target systems. The specific type of connector used depends on the type of data store being used, such as an LDAP directory or an RDBMS.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/global-sync-guide/concepts-and-definitions/agents-and-connectors/>


# Question/Answer Pair 16

Question: How long do unprocessed messages remain the queues in RadiantOne v7.4 Synchronization?

Answer: The unprocessed messages in the queues of RadiantOne Synchronization remain there until they are picked up by the sync engine or until the message time-to-live has been reached. By default, the message time-to-live is set to 3 days. You can configure the message time-to-live in the "Changelog and Replicationjournal Max Age" property in the Main Control Panel, Settings, Log, Changelog section. To view the queues, you can search for them in the Directory Browser tab of the Main Control Panel. Please note that the queues are hidden root naming contexts, so you need to specifically search for them.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/global-sync-guide/concepts-and-definitions/queues/#message-time-to-live>


# Question/Answer Pair 17

Question: What are the possible capture types for Database Connectors in RadiantOne v7.4 Synchronization?

Answer: The possible capture types for Database Connectors in RadiantOne Synchronization are Changelog, Timestamp, and Counter. 

- Changelog: This connector type relies on a database table that contains all changes that have occurred on the base tables. Triggers or an external process can be used to write changes into the log/changelog table. The connector picks up changes from the changelog table.
- Timestamp: This connector type is validated against Oracle, SQL Server, MySQL, MariaDB, PostgreSQL, and Apache Derby databases. The database table must have a primary key and an indexed column that contains a timestamp/date value. This value must be maintained and modified for each updated record. The timestamp column type varies depending on the database used.
- Counter: This connector type is supported for any database table that has an indexed column containing a sequence-based value. The column must be one of the following types: BIGINT, DECIMAL, - INTEGER, or NUMERIC. The Counter connector uses this column to determine which records have changed since the last polling interval. It can also detect delete operations if the table has a dedicated "Change Type" column indicating insert, update, or delete.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/global-sync-guide/configuration/capture-connector/database-connectors/>

# Question/Answer Pair 18

Question: What are the possible capture connector types for Active Directory in RadiantOne v7.4 Synchronization?

Answer: The possible capture connector types for Active Directory in RadiantOne Synchronization are DirSync, USNChanged, and Hybrid. 

The DirSync connector retrieves changes by passing a cookie that identifies the directory state at the time of the previous DirSync search. It stores a cookie in a cursor file when it is started and performs a DirSync search at the next polling interval to detect changes. This connector is recommended when the sequence of events is critical because it processes events in the order in which they occur.

The USNChanged connector keeps track of changes based on the uSNChanged attribute for the entry. It connects with the user and password configured in the connection string and checks the list of changes stored by Active Directory. It internally maintains the last processed change number (uSNChanged value) to recover all changes that occur, even if the connector is down.

The Hybrid connector uses a combination of the uSNChanged and DirSync change detection mechanisms. It gets a new cookie and the highest uSNChanged number when it starts. When it gets a new change, it makes an additional search using the DN of the entry and fetches the entry from AD. The fetched entry contains the uSNChanged attribute, so the connector updates the cursor values for both the cookie and the last processed uSNChanged number. This connector is suitable for virtualizing and detecting changes from a Global Catalog.

To select the desired connector type, access the Main Control Panel, Synchronization tab. Then choose the appropriate topology (on the left) and pipeline, and modify the connector type and advanced properties in the Capture component.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/global-sync-guide/configuration/capture-connector/directory-connectors/>


# Question/Answer Pair 19

Question: What is Identity Linkage used for in RadiantOne v7.4 Synchronization?

Answer: Identity Linkage in RadiantOne Synchronization is used to establish a unique connection between a source identity and a target identity. This linkage can be based on a specific attribute or a combination of information computed with a function. By defining the identity linkage, you can ensure that the same logic is applied across all rules in RadiantOne Synchronization. However, if needed, each rule can have different criteria for identity linkage. The purpose of identity linkage is to accurately synchronize and match identities between different systems or data sources.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/global-sync-guide/configuration/rules/identity-linkage/>

# Question/Answer Pair 20

Question: How is the Target DN generated for RadiantOne v7.4 Synchronization?

Answer: The target DN for RadiantOne Synchronization can be generated automatically or manually. If you choose the Automatic option, the target DN is generated based on the virtual view created for the target and where it is mounted in the RadiantOne namespace. This option works well if you are synchronizing objects in the same container. However, if you need to sync entries into different containers or branches in the target, you should choose the Manual option.
When you select the Manual option, you will have a Target DN setting in your Rule. In this setting, you can choose the variable that contains the logic for how the target DN is generated. This allows you to have more control over the target DN generation process.
To summarize, if you want the target DN to be generated automatically based on the virtual view and mount location, choose the Automatic option. If you need more control and want to manually specify the target DN generation logic, choose the Manual option.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/global-sync-guide/configuration/rules/target-dn-variable/>

# Question/Answer Pair 21

Question: How do I upgrade my RadiantOne version?

Answer: To upgrade your RadiantOne version:

Examples of an upgrade are moving from v7.2 to v7.3, v7.2 to v7.4, or v7.3 to v7.4. The upgrade process is not applied with an update installer and may require a professional services engagement to assess the current usage/configuration of RadiantOne to determine an appropriate upgrade strategy and time requirement. All customers currently running v7.2 and v7.3 where ICS/Synchronization is deployed should contact their Radiant Logic Account Representative to have their configuration reviewed and the scope/complexity of their upgrade path assessed. If a customer has only RadiantOne FID deployed (no ICS/Synchronization) and can upgrade their own deployment, they can leverage the upgrade guides available in the Radiant Logic Knowledge Base: [Radiant Logic Knowledge Base](<https://support.radiantlogic.com>).

1. Determine your current version: Check which version of RadiantOne you are currently using. This information will help you determine the appropriate upgrade path.

2. Access the upgrade guide: For example, you can find the upgrade guide for upgrading from version 7.2 to 7.4 at this link: [RadiantOne Upgrade Guide v7.2 to v7.4](<https://support.radiantlogic.com/hc/en-us/articles/7908444062612-RadiantOne-Upgrade-Guide-v7-2-to-v7-4>). This guide provides step-by-step instructions on how to perform the upgrade.

3. Contact your Radiant Logic Account Representative: If you are using version 7.2 or 7.3 and require upgrade assistance, please reach out to your Radiant Logic Account Representative. They will be able to provide guidance and support for your specific upgrade needs.
Remember to always backup your data before proceeding with any upgrades to ensure the safety of your information.

For details about upgrading from v7.4 to v8.1, see: <https://developer.radiantlogic.com/idm/v7.4/upgrade-guides/upgrade74-81/> 

# Question/Answer Pair 22

Question: How do I initialize a RadiantOne v7.4 Directory store replica in another RadiantOne Cluster?

Answer: To initialize a RadiantOne Directory store replica in another RadiantOne Cluster, follow these steps:

1. Determine the leader node of the cluster by going to the Dashboard tab of the Main Control Panel. Look for the node marked as the leader (with a gold triangle).
2. If there are multiple clusters involved, export an LDIF file from the cluster considered the "master" image. Make sure the “Export for replication” option is enabled during the LDIF export.
3. Disable inter-cluster replication for the RadiantOne Directory store if you plan on re-initializing all replicas with a clean image. If you want to maintain inter-cluster replication and process changes from other replicas while re-initializing, do not disable inter-cluster replication.
4. Make sure to schedule a maintenance window for the re-initialization process, as it is time-consuming and requires the service to be offline.
5. On the Main Control Panel, go to the Directory Namespace tab and select the RadiantOne Directory store you want to initialize.
6. Click on the Initialize button on the Properties Tab.
7. Browse to the desired LDIF file and select it.
8. The initialization process will be executed on the leader node. The store on the leader node will be initialized and then activated again. The data will be copied to all follower/follower-only nodes.
9. If you have a large data set and multiple LDIF files, name the files with a suffix of "_2", "_3", etc., and make sure they are located in the same place for the initialization process to find them.
Please note that these instructions assume you are initializing the store on the leader node. If you attempt to initialize on a non-leader node, you will receive an error message indicating that you must perform this operation on a leader node.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/deployment-and-tuning-guide/07-deployment-architecture/#initialize-the-replicas>

# Question/Answer Pair 23

Question: What LDAP controls and extensions are supported by RadiantOne v7.4?

Answer: RadiantOne supports several LDAP controls and extensions. Here is a list of the controls and extensions supported by RadiantOne 7.4:

- Subtree Delete Control - 1.2.840.113556.1.4.805
- Password expired notification control - 2.16.840.1.113730.3.4.4
- Password expiring notification control - 2.16.840.1.113730.3.4.5
- Password policy control - 1.3.6.1.4.1.42.2.27.8.5.1
- Persistent search control - 2.16.840.1.113730.3.4.3
- Virtual list view request control - 2.16.840.1.113730.3.4.9
- Proxied authorization (version 2) control - 2.16.840.1.113730.3.4.18
- Server-side sort request - 1.2.840.113556.1.4.473
- Authorization bind identity response control - 2.16.840.1.113730.3.4.15
- Authorization bind identity request control - 2.16.840.1.113730.3.4.16
- Who Am I extended operation - 1.3.6.1.4.1.4203.1.11.3
- Paged Results Control - 1.2.840.113556.1.4.319
- Dynamic entries extension - 1.3.6.1.4.1.1466.101.119.1
- All Operational Attributes feature - 1.3.6.1.4.1.4203.1.5.1
- Absolute True and False Filters - 1.3.6.1.4.1.4203.1.5.3

Please note that RadiantOne does not support the following controls used in Sun Java Directory/ODSEE:
- Manage DSA IT control - 2.16.840.1.113730.3.4.2
- Get effective rights request control - 1.3.6.1.4.1.42.2.27.9.5.2
- Account usability control - 1.3.6.1.4.1.42.2.27.9.5.8
- Specific backend search request control - 2.16.840.1.113730.3.4.14
- Real attributes only request control - 2.16.840.1.113730.3.4.17
- Virtual attributes only request control - 2.16.840.1.113730.3.4.19

To enable controls like Paged Results, VLV/Sort, Persistent Search, and Proxy Authorization, you can go to the Main Control Panel, then navigate to the Settings tab and select Server front end. From there, you can find the Supported Controls section.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/sys-admin-guide/03-front-end-settings/#supported-controls-and-features>


# Question/Answer Pair 24

Question: Which LDAP protocol versions does RadiantOne v7.4 support?

Answer: RadiantOne supports LDAP protocol versions 2 and 3. The information about the supported LDAP protocol versions can be found by querying the supportedldapversion attribute in the rootDSE entry.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/operational-attributes-guide/02-general-operational-attributes/#supportedldapversion>


# Question/Answer Pair 25

Question: How to change the cluster name in RadiantOne v7.4?

Answer: To change the cluster name of RadiantOne v7.4, please follow these step-by-step instructions:
Please note that renaming a cluster is a delicate operation and should not be used frequently. It is also not recommended for deployed architectures involved in inter-cluster replication, as the cluster name is crucial for replication logic.

1. Stop all RadiantOne services except ZooKeeper.
2. On any RadiantOne node, run the following command:
   `&lt;RLI_HOME&gt;/bin/advanced/cluster.sh rename-cluster-zk &lt;vds_instance_name&gt; &lt;old_cluster_name&gt; &lt;new_cluster_name&gt;`
   This command will move the ZooKeeper data from `/radiantone/v2/&lt;old_cluster_name&gt;` to `/radiantone/v2/&lt;new_cluster_name&gt;`.
3. On each RadiantOne node, run the following command:
   `&lt;RLI_HOME&gt;/bin/advanced/cluster.sh rename-cluster-local &lt;vds_instance_name&gt; &lt;new_cluster_name&gt;`
4. Start RadiantOne services (e.g., FID, Control Panel (Jetty), etc.) on all nodes.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/operations-guide/02-cluster-management/#renaming-clusters>

# Question/Answer Pair 26

Question: How to use Eclipse in RadiantOne v7.4 to edit interception scripts?

Answer: To use Eclipse in RadiantOne v7.4, please follow these step-by-step instructions:

1. Install Eclipse IDE for Java developers.
2. Launch Eclipse and choose File -&gt; Import.
3. Expand the General folder, select Existing Projects into Workspace, and click Next.
4. Click Browse next to Select Root Directory and navigate to &lt;RLI_HOME&gt;/vds_server/custom.
5. Click Finish.
6. Navigate below the Custom folder to src.com.rli.scripts.intercept. The scripts associated with the interceptions will appear below. Double-click on the script to open it in the Eclipse IDE editor.
7. Edit the script.
8. Save the script.
9. On the RadiantOne machine, rebuild the intercept.jar with ANT using the following syntax:
   ```
   C:\radiantone\vds\vds_server\custom&gt;c:\radiantone\vds\ant\bin\ant.bat buildjars
   ```
10. Restart the RadiantOne service. If deployed in a cluster, restart it on all nodes. the RadiantOne service. If deployed in a cluster, restart it on all nodes. 

For more details on using Eclipse for writing transformation scripts for synchronization, see: <https://developer.radiantlogic.com/idm/v7.4/global-sync-guide/configuration/script/#use-a-java-ide-to-customize-scripts>


# Question/Answer Pair 27

Question: what is the unit of the ETIME column in the RadiantOne server logs?

Answer: The ETIME column in the server logs measures the time taken for a request to be processed. The unit of measurement for this column is milliseconds (ms). So, when you see a value in the ETIME column, it represents the time taken in milliseconds for that particular request to be processed.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/logging-and-troubleshooting-guide/03-radiantone-universal-directory/#log-details>


# Question/Answer Pair 28

Question: Is the wizards tab accessible from the Main Control Panel on Follower nodes of a cluster in RadiantOne 7.4?

Answer: The wizards tab is not accessible on follower nodes of a cluster in RadiantOne v7.4. The wizards tab is only available in the leader node of the cluster. The leader node is responsible for managing the configuration and changes in the cluster. Follower nodes, on the other hand, replicate the changes made by the leader node.
To access the wizards tab, you need to log in to the leader node of the cluster. Once logged in, you can navigate to the Main Control Panel and find the wizards tab. From there, you can access and use the various wizards available for configuration and setup.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/architect-guide/getting-started-with-radiantone/#identity-service-wizards>

# Question/Answer Pair 29

Question: What does the Global Identity Builder do?

Answer: The Global Identity Builder is a tool that creates a unified list of identities from different sources, even if they don't have a single attribute as an overlapping common identifier. This tool is useful when applications need to authenticate users or access their complete profiles for authorization purposes. It can handle situations where there are overlapping users or when a complete aggregated list of users is needed. The Global Identity Builder also allows for the remapping of information into the format expected by the application. 

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/global-identity-builder-guide/introduction/>

# Question/Answer Pair 30

Question: Where can I find the Identity Data Analysis tool in RadiantOne v7.4?

Answer: The Identity data analysis tool can be found in the \&lt;RLI_HOME\&gt;/bin/advanced directory. On Windows, it is named data_analysis.bat, and on Linux, it is named data_analysis.sh. To use the tool, you need to run it from a command prompt and provide the necessary arguments.
The required arguments are:
-d: The report directory where the report files will be saved. The report directory should not contain any path characters (/,\).
-f: The full name of the LDIF file you want to analyze. You can include the file path if needed.
Optional arguments are:
-h: Displays the help information.
-o: Allows you to overwrite files in the report directory. If you don't pass this option and the report directory already exists, no analysis will be done, and the report directory's files will not be changed.
-r: Removes detailed analysis files in the report directory.
Here's an example command to run the data analysis tool:
C:\radiantone\vds\bin\advanced\&gt;data_analysis.bat -d LDAPANALYSIS -f "C:\radiantone\vds\vds_server\ldif\export\ldap.ldif"
After running the tool, the reports will be generated in the specified report directory. In this example, the reports will be located in the following directory: C:\radiantone\vds\r1syncsvcs\profiler\LDAPANALYSIS.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/data-analysis-guide/03-using-identity-data-analysis-command-line-tool/#running-the-data-analysis>

# Question/Answer Pair 31

Question: Where do I find the Data Sources perspective in RadiantOne v7.4, Context Builder tool?

Answer: Starting in RadiantOne v7.4, Data Sources are managed from the Control Panel. To access the Data Sources in RadiantOne v7.4 and later versions, follow these steps:

1. Open the Control Panel.
2. Go to the "Settings" tab.
3. Select "Server Backend".
From the Server Backend section in the Control Panel, you can manage your Data Sources.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/sys-admin-guide/data-sources/>

# Question/Answer Pair 32

Question: What is Environment Operations Center?

Answer: The Environment Operations Center is a tool that allows you to control your RadiantOne environment for SaaS deployments. It provides all the necessary tools to create, manage, and monitor your RadiantOne environments. 

For more details, see: <https://developer.radiantlogic.com/idm/v8.0/environment-operations-center-guide/overview/>  


# Question/Answer Pair 33

Question: Can RadiantOne v7.4 be deployed on Kubernetes?

Answer: Yes, RadiantOne v7.4 can be deployed on a Kubernetes cluster. 

For details, see: <https://developer.radiantlogic.com/idm/v7.4/getting_started/kubernetes/>


# Question/Answer Pair 34

Question: Why is the RadiantOne v7.4 service not returning the memberOf attribute for queries on user entries?

Answer: To ensure the RadiantOne v7.4 service is able to return the computed back-link attribute memberOf for user entries, configure Special Attributes Handling.

For details, see: <https://developer.radiantlogic.com/idm/v7.4/sys-admin-guide/interception/#linked-attributes>

# Question/Answer Pair 35

Question: what is the role of sync engine in RadiantOne v7.4?

Answer: The role of the Sync Engine in RadiantOne v7.4 is to process attribute mappings and transformation scripts before sending events to the target endpoints. It acts as the central component that coordinates the synchronization process.
When changes occur in the data sources, the Sync Engine receives these changes from the queues. It then applies the necessary attribute mappings and transformation scripts to format the data correctly for the target endpoints. Once the data is transformed, the Sync Engine sends the events to the target endpoints for further processing.
The Sync Engine ensures that the synchronization process is efficient and accurate by handling the mapping and transformation of data. It plays a crucial role in maintaining data consistency and integrity between different systems.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/global-sync-guide/concepts-and-definitions/sync-engine-and-transformation/>

# Question/Answer Pair 36

Question: How do I setup MFA for the Control Panel in RadiantOne v7.4?

Answer: MFA handling is delegated to the Identity Provider configured for authenticating users for the RadiantOne Control Panel. OIDC is supported and MFA is handled by the OIDC Identity Provider.
For details, see: <https://developer.radiantlogic.com/idm/v7.4/sys-admin-guide/01-introduction/#openid-connect-token-authentication>

An example of using OKTA as an OIDC provider is provided here: <https://support.radiantlogic.com/hc/en-us/articles/25502043039124-Configuring-OIDC-with-Okta-to-login-to-Control-Panel>

# Question/Answer Pair 37

Question: How do I update the external ZooKeeper being used by RadiantOne 7.4?

Answer: To update external ZooKeeper which new patches provided by Radiant Logic, please follow these step-by-step instructions:

1. Copy the "rli-zookeeper-external\*" file to each of your ZooKeeper servers.
2. Unzip the new ZooKeeper version in a separate, temporary folder (other than the one it is currently installed on).
3. Stop ZooKeeper on the node you are updating.
4. If you haven't already done so, make a copy/backup of the existing ZooKeeper home location.
5. Copy the following folders from the new version (that you unzipped in step 2) to the existing setup:
   - /bin/ (copy)
   - /setup/ (remove from target first – remove all jars, then copy)
   - /zookeeper/bin/ (remove from target first, then copy)
   - /zookeeper/docs/ (remove from target first, then copy)
   - /zookeeper/lib/ (remove from target first, then copy)
   - /jdk/ (remove from target first, then copy)
6. Delete the temporary folder that you unzipped the new ZooKeeper version to in step 2.
7. Start ZooKeeper.
8. Repeat the steps above for each ZooKeeper server in your external ensemble.
Please note that the truststore and keystore are created when ZooKeeper is restarted after the update. If you want to use SSL/TLS access to ZooKeeper, ensure you have imported the required certificates.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/applying-patch/applying-patch/#updating-external-zookeeper-ensemble>

# Question/Answer Pair 38

Question: How do I create a virtual view that joins across multiple heterogeneous data sources in RadiantOne v7.4?

Answer: To create a virtual view that joins across multiple heterogeneous data sources in RadiantOne v7.4, you can follow these steps:

1. Open the Main Control Panel and navigate to the Context Builder tab.
2. Click on the View Designer tab.
3. Create a virtual view of the primary data source using the View Designer.
4. Next, create a virtual view of the secondary data source using the View Designer.
5. Open the virtual view of the primary data source in the View Designer.
6. In the view definition/tree, select the object where you want to define a join.
7. On the right side, select the Object tab.
8. In the "Join Profiles" section, click on the "NEW" button.
9. Select the "Regular" join type and click "NEXT".
10. Choose "Attribute Matching &gt; Join with Existing View" and click "NEXT".
11. Click on "Choose" and browse to select the virtual view of the secondary data source.
12. Select the attribute in the primary data source object and the secondary data source object that are in common and will indicate a link between matching entries across these sources.
13. Choose which attributes to return from the secondary object.
14. Click "Finish" and save the virtual view.
At runtime, RadiantOne will join the entries from the primary data source that have a matching entry in the secondary data source.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/context-builder-guide/view-designer/>

# Question/Answer Pair 39

Question: How does RadiantOne address challenges for implementing Zero Trust Architecture?

Answer: The identity system continues to decentralize and grow in complexity and volume, making it increasingly difficult for IT and security teams to combat cyber threats. Security control points are increasingly decentralized, but require real-time access to dispersed identity data to execute policies. Correlating and delivering that necessary data in the format required by each policy enforcement point is a prerequisite to Zero Trust Architecture. Implementation of practices like attribute-based access control requires a high-quality and rich set of information about each user to enforce security policy.
Identity-based controls are the modern way to secure the organization: but the hidden challenge is often delivering the identity data they require from across a complex infrastructure. Many organizations are dealing with identity sprawl:
- Identity data, including attributes for enforcing authorization, is dispersed
- Identity data might be stale, incomplete, or duplicative
RadiantOne addresses the requirement for access to high-quality identity data, delivering the required user context so that security policies can be precise.
- To deliver granular access control, complete and clean identity data is required
- Fine-grained authorization relies on access to detailed identity data
RadiantOne addresses identity complexity with integration, to:
- Deliver identity data that is: consistent, context-aware, and continuous
- Speed attribute-based access control with a unified source of identity data
- Reduce risk by implementing fine-grained authorization with many attributes
- Streamline compliance and audit with a 360-degree view of identity
- Decrease the attack surface, limit lateral movement, and prevent fraud

# Question/Answer Pair 40

Question: Where are ZooKeeper Logs stored in RadiantOne 7.4?

Answer: The log location for ZooKeeper (deployed internal/local to the RadiantOne nodes) is: `<RLI_HOME>\logs\zookeeper`. The rollover logs are also located at this location. Rollover file size (default of 100MB) and location are configured in: `<RLI_HOME>/config/logging/log4j2-zookeeper-server.json`.

The log location for external ZooKeeper ensemble logs is: <rli-zookeeper-external_install-path>\zookeeper\logs. The rollover logs are located in C:\rli-zookeeper-external\bin\logs\ for Windows deployments and rli-zookeeper-external/logs/ on Linux deployments. Rollover file size and location are configured in: `/zookeeper/conf/log4j2.xml`

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/logging-and-troubleshooting-guide/04-zookeeper/>

# Question/Answer Pair 41

Question: How is audit logging enabled in RadiantOne v7.4?

Answer: To enable audit logging:

1. In the file system, navigate to <RLI_HOME>/config/advanced.
2. In a file editor such as Notepad, open features.properties.
3. Set audit.logging.enabled=true.
4. If you want to enable logging delta changes, set audit.logging.diff.enabled=true.
5. If you want to enable logging for the vdsconfig utility, set vdsconfig.logging.enabled=true.
6. Save features.properties.
7. Restart the Control Panel.
8. Restart the RadiantOne service.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/logging-and-troubleshooting-guide/09-audit-logging/>

# Question/Answer Pair 42

Question: What activities are launched as tasks in RadiantOne 7.4?

Answer: The activities that are processed as tasks are:
- Exporting to LDIF
- Importing from LDIF
- Login analysis (initiated from the virtual identity wizard)
- Initializing a persistent cache or RadiantOne Universal Directory (HDAP) store
- Re-indexing a persistent cache or RadiantOne Universal Directory (HDAP) store
- Default monitoring

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/logging-and-troubleshooting-guide/06-task-scheduler-and-tasks/>

# Question/Answer Pair 43

Question: Where are events performed by administrators in the Control Panel logged, in RadiantOne v7.4?

Answer: The Control Panel access log file contains the save operations performed by administrators. When any user that is a member of the delegated administration groups saves changes in the Main or Server Control Panels, this activity is logged into: `<RLI_HOME>/vds_server/logs/jetty/web_access.log.` This is a CSV formatted log file with the delimiter being *TAB*. These settings are configured from the Main Control Panel > Settings tab > Logs > Log Settings section. Select Control Panel – Access from the Log Settings to Configure drop-down list. Define the log level, rollover size and number of files to keep archived.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/logging-and-troubleshooting-guide/02-control-panels-and-configuration-tools/#access-log>

# Question/Answer Pair 44

Question: How can I indicate to ignore logging events on specific naming contexts to avoid overloading log files with irrelevant events in RadiantOne v7.4?

Answer: To ignore logging for these naming contexts, expand below the Advanced section (requires Expert Mode) and check the box next to the naming context. Logging for the following naming contexts can be ignored.
- ROOT: this is for queries requesting the rootDSE (an empty base DN) and is often used by hardware load balancers to check the availability of the RadiantOne service.
- cn=changelog: modifications to entries in the RadiantOne namespace are tracked in the changelog. Other services can query the changelog frequently to check for changes.
- cn=clustermonitor: various statistics and availability of cluster nodes are retrieved by querying cn=clustermonitor.
- cn=replicationjournal: inter-cluster replication queries the cn=replicationjournal.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/logging-and-troubleshooting-guide/03-radiantone-universal-directory/#ignore-logging-for-internal-naming-contexts>

# Question/Answer Pair 45

Question: Where are logs for ADAP access to RadiantOne v7.4 located?

Answer: The adap_access.log file is in `<RLI_HOME>/<instance_name>/logs`. The default instance name is vds_server, so the path would be: `<RLI_HOME>/vds_server/logs/`

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/logging-and-troubleshooting-guide/03-radiantone-universal-directory/#adap-access-log>

# Question/Answer Pair 46

Question: Where are logs for SCIM access to RadiantOne v7.4 located?

Answer: The SCIM log file is `<RLI_HOME>/<instance_name>/logs/scim.log`. The default instance name is vds_server, so the path would be `<RLI_HOME>/vds_server/logs/scim.log`.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/logging-and-troubleshooting-guide/03-radiantone-universal-directory/#scim-log> 

# Question/Answer Pair 47

Question: What is rli_router used for in RadiantOne?

Answer: The RadiantOne Access Router can be used in test environments where a hardware load balancer is not available. It was deprecated as of v7.3. In older versions of RadiantOne, it was used for load balancing or failover between multiple directories that contain the same structure. The directories could be virtual directories or any other LDAP-accessible server.
The access router works at the "packet" level, adding very little overhead to the system. It is an excellent way to aggregate throughput from many different servers, with the increase in throughput being linear up to about 10 LDAP servers. Any constraint in throughput is essentially linked to the processing and bandwidth of the machine where the router is running. Therefore, it is recommended to install the router on a machine where both bandwidth connectivity and processing can be dedicated to achieve the full benefits and performance.
All configuration information for the RadiantOne Access Router is stored in the `&lt;RLI_HOME&gt;/rlirouter/rli_router.conf` file, which is managed from the Router Administration Console.
The access router manages failover and load balancing at the level of the connection, not the operation. In a failover configuration, when a client establishes a connection, all operations are sent to the primary server. If an operation fails due to a loss of connection to the underlying LDAP server, the failover happens when the client re-opens the connection. The existing operation isn't automatically sent to the failover server. Only when the client re-connects will the connection be sent to the failover server.
During load balancing, all operations issued under the same connection are sent to the same underlying LDAP server. If a client application opens two connections, then one connection is sent to each underlying LDAP server.

# Question/Answer Pair 48

Question: How do I migrate configuration files from a development to production environment in RadiantOne v7.4?

Answer: v2.1 of the [Migration Utility](<https://developer.radiantlogic.com/idm/v7.4/migration-utility/01-introduction/>) can be used. The following commands in the vdsconfig utility can also be used: resource-traverse, resource-export, resource-import, import-datasource, and export-datasource.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/command-line-configuration-guide/16-migration-commands/> and <https://developer.radiantlogic.com/idm/v7.4/command-line-configuration-guide/05-data-source-commands/>

# Question/Answer Pair 49

Question: What is adequate memory size for RadiantOne v7.4?

Answer: Adequate memory size depends on the use case and volume of entries managed by RadiantOne.

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/hardware-sizing-guide/06-memory/>

# Question/Answer Pair 50

Question: What is the ideal memory map count, user limits and swap space for deploying RadiantOne v7.4 on Linux?

Answer: Recommended memory map count is 262144, file descriptors can be set to 65536, and Swap should be disabled if possible (/etc/fstab) or configured to prevent swapping under normal usage (set vm.swappiness to a value <=20 which is the percentage of RAM left before the system starts to swap). 

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/hardware-sizing-guide/04-linux-environments/>

# Question/Answer Pair 51

Question: How do I remap foreign security principals returned in groups from Active Directory in v7.4?

Answer: 1. Create an LDAP proxy view for the primary Active Directory domain and then use a "merge tree" to merge in the Active Directory domain where the foreign security principals are located.
2. Select the proxy view node associated with the main Active Directory and on the Objects tab click ADD.
3. Select the group object and click OK.
4. Click Save and click Yes to confirm
5. At the bottom of the Objects tab, click EDIT next to Define Computed Attributes.
6. Click ADD.
7. Enter member for the attribute name.
8. Click FUNCTION to indicate the value of the member attribute should be computed with a function.
9. Select remapDN(attr2remap,dataSourceID,externalBaseDN,scope,externalIdAttr) and 
click OK. This function remaps a member value when the RDN value matches 
ObjectSID for a user entry. 
10. Select the member attribute from the attr2remp drop-down list.
11. Select the “vds” data source for the data source ID.
12. Check the External Base DN option and point to the branch in the virtual view where the 
users are located. (the merged tree location where the second Active Directory is mounted in step 1).
13. Enter ObjectSID for the externalIdAttr.
14. Click OK.
15. Click Validate.
16. Click OK and OK again to exit the Computed Attribute Window.
17. Click Save. 

With this remapping, any query containing a filter to look for a specific group returns the entry with the member attribute containing the DNs 
for the foreign user DN (e.g. CN=S-1-5-21-4199197291-1226998611-1231062227-1104,CN=ForeignSecurityPrincipals,o=delegated admin) translated into the actual user DN represented by the foreign security principal value (e.g. CN=Sally Europe,CN=User,o=delegated admin).

# Question/Answer Pair 52

Question: How can client's query for a user's nested group memberships for entries stored in the RadiantOne directory v7.4?

Answer: Client's can search a RadiantOne directory for nested group members using LDAP_MATCHING_RULE_IN_CHAIN. The following example is used to describe the ability to search group membership for a user that is a member of a nested group.
User Ada Rule (identified with a DN of uid=Ada_Rule,ou=Administration,o=companydirectory) is a member of a group named WebUsers. The WebUsers group is a member of a group named Intern. The Intern group is a member of a group named AllUsers. Ada is implicitly a member of WebUsers, Intern and AllUsers. To query RadiantOne for a list of all groups Ada is a member of, the following filter leveraging the LDAP_MATCHING_RULE_IN_CHAIN OID can be used:
(uniquemember:1.2.840.113556.1.4.1941:=uid=Ada_Rule,ou=Administration,o=companydirectory)

For more details, see: <https://developer.radiantlogic.com/idm/v7.4/namespace-configuration-guide/05-radiantone-universal-directory/#searching-for-group-members-using-ldap_matching_rule_in_chain>

# Question/Answer Pair 53

Question: In RadiantOne version 7.4, where can I find the Task Scheduler?

Answer: 1. Open the Main Control Panel associated with the RadiantOne leader node and use the link in the upper right to switch to the Server Control Panel.
2. In the Server Control Panel, click on the **Tasks** tab.
3. In this section, you can start and stop the scheduler as well as manage defined tasks.
4. You will see a task list detailing the tasks that have been added to the scheduler and their statuses.
If you want to make changes or view details about specific tasks, you can click on the relevant task in the list to view or edit its configuration.
Here are some potentially helpful documentation links:
- https://github.com/radiantlogic-v8/documentation-new/blob/v7.4/documentation/logging-and-troubleshooting-guide/06-task-scheduler-and-tasks.md
- https://github.com/radiantlogic-v8/documentation-new/blob/v7.4/documentation/sys-admin-guide/01-introduction.md
- https://github.com/radiantlogic-v8/documentation-new/blob/v7.4/documentation/installation-guide/01-introduction.md

# Question/Answer Pair 54

Question: In RadiantOne version 7.4, How do I delete the default password policy?

Answer: The default password policy cannot be deleted. However, it can be updated to meet your needs, or you can create a custom password policy to override the default one.

To update the default password policy:
1. Navigate to Main Control Panel > Settings > Security > Password Policies.
2. Select *Default Policy* fron the list.
3. Customize the policy and click **SAVE**.

To create a custom password policy:
1. Navigate to Main Control Panel > Settings > Security > Password Policies.
2. Click **NEW** Next to *Choose a Password Policy*.
3. Customize the policy and click **SAVE**.
   
Here are some potentially helpful documentation links:
- https://github.com/radiantlogic-v8/documentation-new/blob/v7.4/documentation/logging-and-troubleshooting-guide/06-task-scheduler-and-tasks.md
- https://github.com/radiantlogic-v8/documentation-new/blob/v7.4/documentation/sys-admin-guide/01-introduction.md

# Question/Answer Pair 55

Question: Can RadiantOne extract schemas from custom data sources?

Answer: No, RadiantOne cannot extract schemas from custom data sources. The one exception is for SCIMv2 accessible ones, in which case, the schema can be extracted.  For all other custom data sources, manually define the objects and attributes. This can be done in v7.4 using Main Control Panel > Context Builder > Schema Manager, or in v8.1 using Control Panel > Setup > Data Catalog > Data Sources, Schema tab.

Here are some potentially helpful documentation links:
- <https://developer.radiantlogic.com/idm/v8.1/configuration/data-sources/schemas/#custom-backends>
- <https://developer.radiantlogic.com/idm/v7.4/context-builder-guide/schema-manager>

# Question/Answer Pair 56

Question: In RadiantOne v7.4, how can I verify if inter-cluster replication is enabled using command line?

Answer: The inter-cluster replication state is a property of the naming context. The command to see if this is enabled or not is the following: <br>
`C:\radiantone\vds\bin>vdsconfig.bat get-ctx-prop -namingcontext o=companydirectory -prop  multiMasterReplicatonOn`

A value of true for the multiMasterReplicatonOn property means it is enabled. A value of false means that it is disabled.

Inter-cluster replication leverages the replicationjournal LDAP data source. If you want to know what port the replication process is working on, you need to view the replicationjournal data source in the RadiantOne cluster that is playing the role of the replication journal. You can use this command to get the port property for that data source: <br>
`C:\radiantone\vds\bin>vdsconfig.bat get-datasource -datasourcename replicationjournal`

Here are some potentially helpful documentation links:
- <https://developer.radiantlogic.com/idm/v7.4/command-line-configuration-guide/05-data-source-commands/#get-datasource>
- <https://developer.radiantlogic.com/idm/v7.4/command-line-configuration-guide/10-naming-context-property-commands/#get-ctx-prop>
- <https://developer.radiantlogic.com/idm/v7.4/deployment-and-tuning-guide/07-deployment-architecture/#inter-cluster-replication-for-universal-directory-stores>
