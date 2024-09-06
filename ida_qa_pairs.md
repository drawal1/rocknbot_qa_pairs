# Question/Answer Pair 1

Question: can I automate the use of an API to query the Identity Analytics (IDA) database in a program using tokens?
Answer: You can utilize an API to read data from the IDA database for your project. To do so, you need to use a personal account, therefore, you cannot tokens and automate the use of the API in a program.

# Question/Answer Pair 2

Question: How does the clustering feature work in the AIDA-assisted user access review?
Answer: The automatic identification of clusters when using AIDA in a permission matrix works this way: 
1. **Data Examination**: During the Similarities step, AIDA examines the access rights of various users and identifies patterns in the data.
2. **Cluster Detection**: AIDA automatically detects clusters, based on a "frequent closed itemsets mining" algorithm that have been especially enhanced for user access review. The detected clusters are groups of identities that display similar access rights based on permissions-application. This helps highlight entries that likely require similar treatment during the review.
3. **Clustering Algorithm**: A dedicated algorithm sorts the detected clusters by size, and select the first seven biggest clusters. AIDA guides the reviewer through the largest clusters first, making it easier to tackle the most significant groups of similar entries. 

When using the clustering button in a cross-table (without AIDA):
The data is sorted to group users by similar permission sets. Biggest blocks are displayed to the top left of the cross-table, making easier to tackle the most significant groups of similar entries and to identify the outliers at the right and bottom.

# Question/Answer Pair 3

Question: How can I purge timeslots when using Identity Analytics in SaaS?
Answer: In the SaaS the behavior regarding timeslots purge is the same as in the Self-managed. So you have to hide the timeslots in the web portal, and when the next data upload will be launched (scheduled), the related timeslots will be removed.
Note that if you are uploading data manually (through the batch) and not scheduling the data upload, the timeslots will remain hidden, but this has no incidence on the reporting, those timeslots will be totally ignore.

For more details, see: [Purging Timeslots](https://developer.radiantlogic.com/ia/version-1.5/run-ops/purge/)

# Question/Answer Pair 4

Question: How can I upload data when using Identity Analytics in SaaS?
Answer: RadiantLogic is providing for Identity Analytics in SaaS and Self-Managed deployments a powershell extraction script that allows to extract the data, zipped the data, encryt it and send it to your Identity Analytics instance in the cloud through HTTPS. Here is a summary of the extraction methodology to follow:
1. Identify Sources for Extraction:
Determine which directories (e.g., Active Directory) are referenced in the applications to extract users and groups.
Locate data sources containing organizational information about employees and contractors.
2. Account Selection for Extraction:
Decide which account will be used to perform the extraction (personal or service account).
The credentials required for extractions and zip file uploads need to be encrypted. Encryption depends on the account and machine used.
It's recommended to use a service account from the start to avoid issues with decryption if the script runs automatically under a different account.
3. Setup for Extraction:
Encrypt the necessary credentials.
Configure the extraction settings in the config.json file, including credentials for Active Directory and HR data sources.
4. Test Extraction:
Run the extraction script (bw_data_collector command) to generate a zip file and verify the extracted data.
5. Upload Data to Identity Analytics Platform:
Connect to the platform and upload the zip file to load data into the system for quality review.
6. Automate Uploads:
Authorize automated zip file uploads to the platform in the config.json file and on the platform itself.
7. Schedule Weekly Execution:
Automate the extraction process by scheduling the bw_data_collector command using tools like Windows Task Scheduler.
This process ensures smooth data extraction, encryption, and automated upload to the Identity Analytics platform.

For cloud applications/repositories, you can also leverage the available connectors directly from your SaaS instance like for Entra ID (ex Azure) and Identity Data Management.

For more details, see: [Powershell Extraction Configuration](https://developer.radiantlogic.com/ia/version-1.5/configuration/powershell-extraction/), [Azure Connector Configuration](https://developer.radiantlogic.com/ia/version-1.5/connectors/azure-connector/), [Identity Data Management Integration](https://developer.radiantlogic.com/ia/version-1.5/integrations/iddm/)

# Question/Answer Pair 5

Question: Could you provide me with the compatibility matrix between the versions of IAP and the core product versions of IDA?
Answer: The compatibility matrix shows which versions of the Identity Analytics Platform (IAP) work with different core product versions of Identity Analytics (IDA). Here’s a summary based on the versions you might be looking for:
1. For IAP versions 1.0 to 1.2:
- Curie R1: Compatible
- Curie R2: Compatible
- Curie R3 SP4: Compatible
- Descartes R2: Compatible
- Descartes R4: Compatible
2. For IAP versions 1.3 to 1.7:
- Curie R1: Not Compatible
- Curie R2: Compatible
- Curie R3 SP4: Compatible
- Descartes R2: Compatible
- Descartes R4: Compatible
3. For IAP version 1.8:
- Curie R1: Not Compatible
- Curie R2: Not Compatible
- Curie R3 SP4: Compatible
- Descartes R2: Compatible
- Descartes R4: Compatible
4. For IAP versions 2.0 to 2.2:
- Curie R1: Not Compatible
- Curie R2: Not Compatible
- Curie R3 SP4: Not Compatible
- Descartes R2: Compatible
- Descartes R4: Compatible
5. For IAP version 3.0:
- Curie R1: Not Compatible
- Curie R2: Not Compatible
- Curie R3 SP4: Not Compatible
- Descartes R2: Not Compatible
- Descartes R4: Compatible
This should give you a clear idea of which versions are compatible with each other.

For more details, see: [Identity Analytics Portal Realease Overview](https://developer.radiantlogic.com/ia/iap-3.0/identity-analytics/iap-release/01-iap-release-overview/)
