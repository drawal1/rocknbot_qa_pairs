# Question/Answer Pair 1

Question: can you tell me how to configure TLS mode?
Answer: To configure TLS mode, follow these steps:
1. Go to the Main Control Panel and click on the Settings Tab.
2. Locate the Security section and then the SSL sub-section.
3. Check the Enable SSL option.
4. Also check the Enable Start TLS option to allow clients to request a secure channel.
5. Save the changes made.
6. Restart the RadiantOne service to apply the new configuration.
Remember, if you are using Start TLS, ensure you have a valid certificate that matches your server's hostname. Also, when connecting to any backend server, you will need to use the correct SSL port and ensure any necessary certificates are in the client truststore if they are not recognized.
For more detailed information, you can refer to the SSL/TLS Settings documentation.