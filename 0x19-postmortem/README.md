ISSUE SUMMARY:
Time: 3rd June, 2024. 14:00 GMT – 16:00 GMT
Impact: 80% of users encounted a "500 Internal Server Error" message that rendered the web application inaccessible.
Root Cause: The newly deployed database connection string is incorrectly configured which blocks the connection from the application to the database.
TIMELINE:
14:00 GMT: Monitoring alert suggested an application health check failure.
14:02 GMT: Engineers started the investigation and thought for a moment they had overloaded a server.
14:10 GMT: Had the full app down, not just slow
14:15 GMT - First, server metrics are read (no abnormal behaviour was found), We escalate to the on-call database administrator (DBA) team.
14:30 GMT: The DBA team confirmed that the database was operating without any difficulties.

 14:45 GMT: Initiated rollback of the most recent deployment; problem remained.

 15:00 GMT: A review of recent deployment updates revealed a change to the database connection string.

 15:15 GMT: Misconfiguration of the connection string was identified as the primary cause.

 15:30 GMT: I corrected the connection string and redeployed the program.

 16:00 GMT: Application is fully restored and working.




 ROOT CAUSE AND RESOLUTION:

 The outage was caused by a mistake in the database connection string established during the most recent deployment. This misconfiguration prohibited the program from connecting to the database, resulting in a total failure to serve user requests.
 To remedy the problem, the wrong connection string was updated in the configuration file. A new deployment with the corrected settings was carried out, and post-deployment testing revealed that the application could successfully connect to the database, restoring normal functionality.
CORRECTIVE AND PREVENTATIVE MEASURES.

 To avoid similar situations in the future, we will improve the deployment review process by requiring tougher checks on configuration modifications.
 • Use automated tests to ensure database connection after deployment.
 • Improve logging granularity to discover configuration issues.
 
TODO List: 

 • Implement Configuration Management: Use a tool to manage and validate configuration changes.
 • Automated Testing: Create and incorporate automated tests to ensure database connectivity during deployment.
 • Improved monitoring for database connection problems to prevent future incidents.
 • Improve Code Review Policy: Verify configuration files in detail.
 • Train the technical staff on effective issue response and escalation procedures.
 
In simple terms, our web application was down for two hours because of a mistake in the database connection string during a recent deployment. We repaired the mistake and redeployed the app. To avoid this happening again, we are refining our deployment review process, introducing automated tests for database connection, and increasing our monitoring and incident response methods.
 


