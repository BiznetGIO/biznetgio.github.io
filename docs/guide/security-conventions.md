This section provide instructions to comply with the standard convention how to secure code in development.

## For Code: 
### 1. Validate input. 
Validate input from all untrusted data sources. Proper input validation can eliminate the vast majority of software vulnerabilities. Be suspicious of most external data sources, including command line arguments, network interfaces, environmental variables, and user controlled files. 
### 2. Architect and design for security policies. 
Create a software architecture and design your software to implement and enforce security policies. For example, if your system requires different privileges at different times, consider dividing the system into distinct intercommunicating subsystems, each with an appropriate privilege set. 
### 3. Keep it simple. 
Keep the design as simple and small as possible. Complex designs increase the likelihood that errors will be made in their implementation, configuration, and use. Additionally, the effort required to achieve an appropriate level of assurance increases dramatically as security mechanisms become more complex. 
### 4. Default deny. 
Base access decisions on permission rather than exclusion. This means that, by default, access is denied and the protection scheme identifies conditions under which access is permitted. Adhere to the principle of least privilege. Every process should execute with the the least set of privileges necessary to complete the job. Any elevated permission should only be accessed for the least amount of time required to complete the privileged task. This approach reduces the opportunities an attacker has to execute arbitrary code with elevated privileges. 
### 5. Sanitize data sent to other systems. 
Sanitize all data passed to complex subsystems such as command shells, relational databases, and commercial off-the-shelf (COTS) components. Attackers may be able to invoke unused functionality in these components through the use of SQL, command, or other injection attacks. This is not necessarily an input validation problem because the complex subsystem being invoked does not understand the context in which the call is made. Because the calling process understands the context, it is responsible for sanitizing the data before invoking the subsystem. 
### 6. Practice defense in depth.
Manage risk with multiple defensive strategies, so that if one layer of defense turns out to be inadequate, another layer of defense can prevent a security flaw from becoming an exploitable vulnerability and/or limit the consequences of a successful exploit. For example, combining secure programming techniques with secure runtime environments should reduce the likelihood that vulnerabilities remaining in the code at deployment time can be exploited in the operational environment. 
### 7. Use effective quality assurance techniques. 
Good quality assurance techniques can be effective in identifying and eliminating vulnerabilities. Fuzz testing, penetration testing, and source code audits should all be incorporated as part of an effective quality assurance program. Independent security reviews can lead to more secure systems. External reviewers bring an independent perspective; for example, in identifying and correcting invalid assumptions. 


## For Databases: 
1. As for SQL, generate your SQL as close to the database - and as far from the user - as possible. UX-side apps should use data-requesting APIs to backend apps that generate SQL, and they should never generate SQL anywhere where a front-end user can see any part of it. If they even have direct connections to the database, you're probably exposed. 
2. Never generate SQL in front-end code running on a browser. You're providing a nice interface with already-authenticated connections to hackers that goes directly to your database. 
3. To avoid SQL injection attacks, it is best to use prepared statements versus direct execution at your SQL layer, even for queries that run once. 