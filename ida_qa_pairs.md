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

# Question/Answer Pair 6

Question: Can you give me the list of the controls enforced by the solution?
Answer: Over 150 out-of-the-box controls are provided for identifying risky situations like dormant accounts or orphaned accounts. Here is an extract of the main controls:
1,Extreme sensitive permissions
2,Sensitive permissions
3,atypical access right (peer group analysis)
4,atypical new access right (peer group analysis)
5,atypical access right and owner organisation just changed (peer group analysis)
6,access to extreme sensitive folders
7,access to sensitive folders
8,atypical folder right (peer group analysis)
9,atypical folder new access right (peer group analysis)
10,atypical folder access right and owner organisation just changed (peer group analysis)
11,reactivated leaver account
12,reactivated tech account
13,Reactivated Orphaned Account
14,Active leaver account used after the account owner departure date (inactive user)
15,Active leaver account used after the account owner departure date (leave user)
16,Revoked leaver account used after the account owner departure date (inactive user)
17,Revoked leaver account used after the account owner departure date (leave user)
18,"User account, user do not have an organisation manager"
19,Reactivated user account with active identity
20,Reactivated user account with inactive identity
21,Dormant account
22,Orphaned Account
23,Active account for whom the owner has left the organization
24,User account with password never expires
25,Technical/Service account with password set to never expire
26,Orphaned account with never expiring password
27,User password is too old
28,Abnormal login attempts
29,Password not needed
30,User password can't be changed
31,Locked account
32,No user name in user or technical account
33,Username inconsistency
34,Group is empty
35,Group only contains deactivated accounts
36,group contains circular references
37,public group
38,group is almost public
39,High sensitivity group owner left
40,High sensitivity group without owner
41,Extreme sensitivity group owner left
42,Extreme sensitivity group without owner
43,High sensitivity group owner is contractor
44,Extreme sensitivity group owner is contractor
45,High sensitivity group and new accounts
46,Extreme sensitivity group and new accounts
47,High sensitive group without description
48,Critical sensitive group without description
49,no group description
50,No group sensitivity level
51,public group grant access to high sensitive permissions
52,public group grant access to extreme sensitive permissions
53,public group grant access to high sensitive folder
54,public group grant access to extreme sensitive folder
55,almost public group grant access to high sensitive permissions
56,almost public group grant access to extreme sensitive permissions
57,almost public group grant access to high sensitive folders
58,almost public group grant access to extreme sensitive folders
59,huge group members increase
60,Server local group with direct domain user account
61,Server local Users group contains public access
62,Server local Remote Desktop User group contains public access
63,Server local Remote Management Users group contains public access
64,Server local Administrator group contains public access
65,Server local Power Users group contains public access
66,identity without employee number
67,identity without email address
68,ressource owner without email address
69,organization manager without email address
70,team leader without email address
71,Active identity with only inactive or dormant accounts
72,Phantom identity
73,contractors without ending date
74,Active contractors with past ending date and no active account
75,Contractor with past ending date and active accounts
76,employee without manager
77,contractor without manager
78,employee whom manager left
79,contractor whom manager left
80,employee with contractor as manager
81,Identity is its own line manager
82,Contractor leaves within 30 days
83,Several identities with the same name
84,Several identities with the same email address
85,Identities with multiple accounts in the same repositories
86,Identities with multiple accounts in the same application
87,Tech account without manager
88,Account not used since its creation
89,high sensitive permission and new rights
90,extreme sensitive permission and new rights
91,high sensitivity and new folder rights
92,extreme sensitivity and new folder rights
93,high sensitive permission without owner
94,extreme sensitive permission without owner
95,high sensitive folders without owner
96,extreme sensitive folders without owner
97,high sensitive permission without description
98,extreme sensitive permission without description
99,high sensitive folders without description
100,extreme sensitive folders without description
101,huge folder rights increase
102,huge access rights increase
103,Local share with AD domain account ACLs
104,local share with AD domain accounts ACLs
105,application without owner
106,organization without owner
107,application owner left
108,organization owner left
109,sensitive application owner is a contractor
110,organization owner is a contractor
111,orphan organization
112,empty organization
113,application without description
114,share without description
115,no sensitivity level set for the application
116,no sensitivity level set for the share
117,no sensitivity level set for the permission
118,no sensitivity level set for the folder
119,No permission description
120,No folder description
121,no sensitivity level set for the server
122,no sensitivity level set for resources
123,remediation ticket closed and account not revoked
124,remediation ticket closed and access right not removed
125,remediation ticket closed and folder right not removed
126,remediation ticket closed and identity not revoked 
127,account not reviewed in the last 365 days
128,access rights not reviewed in the last 365 days
129,folder rights not reviewed in the last 365 days
130,application not reviewed in the last 365 days
131,share not reviewed in the last 365 days
132,identities not reviewed in the last 365 days
133,organization not reviewed in the last 365 days
134,permission not reviewed in the last 365 days
135,folder not reviewed in the last 365 days
136,group not reviewed in the last 365 days
137,group membership not reviewed in the last 365 days
138,high sensitive access rights not reviewed in the last 90 days
139,high sensitive folder rights not reviewed in the last 90 days
140,extreme sensitive access rights not reviewed in the last 90 days
141,extreme sensitive folder rights not reviewed in the last 30 days

For more details, see: [Identity Analytics: Control Browse](https://developer.radiantlogic.com/ia/iap-3.2/controls-browser/controls-browser/)

