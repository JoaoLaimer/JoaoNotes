TheHive Project is a scalable, open-source and freely available Security Incident Response Platform, designed to assist security analysts and practitioners working in SOCs, CSIRTs and CERTs to track, investigate and act upon identified security incidents in a swift and collaborative manner.

Security Analysts can collaborate on investigations simultaneously, ensuring real-time information pertaining to new or existing cases, tasks, observables and IOCs are available to all team members.

More information about the project can be found on [https://thehive-project.org/](https://thehive-project.org/)[](https://thehive-project.org/) & their [GitHub Repo](https://github.com/TheHive-Project/TheHive).

TheHive allows analysts from one organisation to work together on the same case simultaneously. This is due to the platform's rich feature set and integrations that support analyst workflows. The features include:

- **Case/Task Management:** Every investigation is meant to correspond to a case that has been created. Each case can be broken down into one or more tasks for added granularity and even be turned into templates for easier management. Additionally, analysts can record their progress, attach pieces of evidence or noteworthy files, add tags and other archives to cases.
    
- **Alert Triage:** Cases can be imported from SIEM alerts, email reports and other security event sources. This feature allows an analyst to go through the imported alerts and decide whether or not they are to be escalated into investigations or incident response.
    
- **Observable Enrichment with Cortex:** One of the main feature integrations TheHive supports is Cortex, an observable analysis and active response engine. Cortex allows analysts to collect more information from threat indicators by performing correlation analysis and developing patterns from the cases. More information on [Cortex](https://github.com/TheHive-Project/Cortex/).
    
- **Active Response:** TheHive allows analysts to use Responders and run active actions to communicate, share information about incidents and prevent or contain a threat.
    
- **Custom Dashboards:** Statistics on cases, tasks, observables, metrics and more can be compiled and distributed on dashboards that can be used to generate useful KPIs within an organisation.
    
- **Built-in MISP Integration:** Another useful integration is with [MISP](https://www.misp-project.org/index.html), a threat intelligence platform for sharing, storing and correlating Indicators of Compromise of targeted attacks and other threats. This integration allows analysts to create cases from MISP events, import IOCs or export their own identified indicators to their MISP communities.
    

Other notable integrations that TheHive supports are [DigitalShadows2TH](https://github.com/TheHive-Project/DigitalShadows2TH) & [ZeroFox2TH](https://github.com/TheHive-Project/Zerofox2TH), free and open-source extensions of alert feeders from [DigitalShadows](https://www.digitalshadows.com/) and [ZeroFox](https://www.zerofox.com/) respectively. These integrations ensure that alerts can be added into TheHive and transformed into new cases using pre-defined incident response templates or by adding to existing cases.

The pre-configured user profiles are:  

- **admin:** full administrative permissions on the platform; can't manage any Cases or other data related to investigations;
- **org-admin:** manage users and all organisation-level configuration, can create and edit Cases, Tasks, Observables and run Analysers and Responders;
- **analyst:** can create and edit Cases, Tasks, Observables and run Analysers & Responders;
- **read-only:** Can only read, Cases, Tasks and Observables details;
The full list of permissions includes:

| Permission                           | Functions                                              |
| ------------------------------------ | ------------------------------------------------------ |
| **manageOrganisation (1)  <br>**     | Create & Update an organisation                        |
| **manageConfig (1)  <br>**           | Update Configuration                                   |
| **manageProfile (1)  <br>**          | Create, update & delete Profiles                       |
| **manageTag (1)  <br>**              | Create, update & Delete Tags                           |
| **manageCustomField (1)  <br>**      | Create, update & delete Custom Fields                  |
| **manageCase  <br>**                 | Create, update & delete Cases                          |
| **manageObservable  <br>**           | Create, update & delete Observables                    |
| **manageALert  <br>**                | Create, update & import Alerts                         |
| **manageUser  <br>**                 | Create, update & delete Users                          |
| **manageCaseTemplate  <br>**         | Create, update & delete Case templates                 |
| **manageTask  <br>**                 | Create, update & delete Tasks                          |
| **manageShare**                      | Share case, task & observable with other organisations |
| **manageAnalyse (2)  <br>**          | Execute Analyse                                        |
| **manageAction (2)  <br>**           | Execute Actions                                        |
| **manageAnalyserTemplate (2)  <br>** | Create, update & delete Analyser Templates             |