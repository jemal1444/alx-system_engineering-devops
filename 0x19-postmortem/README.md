Postmortem Report
Error while accessing a given URL
Incident report for Site Outage

Issue Summary:
On October 10th, 2023 at morning the server access went down resulting in 504 error for anyone trying to access this web service. This web server was Apache server.
Duration of the outage: 25-min, from 8:00 AM to 8:25AM (UTC+3)
Impact: The service affected was our banking Core Banking System, which experienced totally disconnected, and all branches of the bank was encountered the page couldnot reached.
Root Cause: The root cause of the issue was a Apache server Catalina logfiles becomes out of alocated space, as a result overwhelming our web servers.
Timeline: 8:10AM (UTC+3): Issue detected when monitoring alerts signaled and our branches claiming service disruption.
Actions Taken: The sysadmin team investigated potential causes, by analyzing logfiles and status of the web services after knowing the root cause taking backup thos logfiles and then truncating Catalina logfiles.
Misleading Investigation: The initial focus on the branch side error led us to unnecessary optimization efforts.
Escalation: After an 10min of investigation, the incident was escalated to the space storage admin team.
-8:15 (UTC+3): The sysadmin team identified that the issue was not network-related and pointed to the web servers.
- Actions Taken: The web servers log files were analyzed, revealing a high number of incoming requests.
- 8:17 (UTC+3): The team truncated the Catalina log files and increased capacity to handle the increased traffic.
- 8:25 (UTC+3): The service was fully restored, and traffic returned to normal, as a result our branches becoming accessing the web server.
**Root Cause and Resolution:**
- Root Cause: Initially small space was allocated for web server Catalina logfile.
- Resolution: Increasing Catalina log space capacity helped handle the traffic, but long-term solutions were discussed.
**Corrective and Preventative Measures:**
- Improve server load balancing and clustering strategies for sudden traffic spikes.
- Implement automated load balancing to distribute traffic efficiently.
- Omit un-necessary log files from Catalina log setting.
- Update the incident response plan to involve development teams earlier in such incidents.
**Tasks to Address the Issue:**
1. Review and optimize our CBS server architecture strategies.
2. Implement automated load balancing for web servers.
3. Enhance monitoring with real-time traffic analysis.
4. Update incident response procedures to involve relevant teams promptly.

**Summary:**
This postmortem outlines the issue's impact, root cause, timeline of events, and corrective/preventative measures. It emphasizes the need for better scalability and automation in handling traffic spikes and more effective collaboration between teams during incidents.

