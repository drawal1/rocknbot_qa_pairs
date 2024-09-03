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

For more details, see: https://developer.radiantlogic.com/ia/version-1.5/run-ops/purge/![image](https://github.com/user-attachments/assets/c11a3fe0-e7fa-4be5-9b00-72f791bec259)

