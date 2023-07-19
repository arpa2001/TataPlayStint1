# IT Delivery

This is a representation of the delivery process for the design of custom crawlers.

## Legend

|Acronym|Full Form|Remarks|
|---|---|---|
|S360|[Simplify360](https://simplify360.com/)|[Tata Play][tataplay]'s backend manager|
|API|Application Programming Interface|Interface of handling backend data|

**Keywords**: _Tata Play, S360, Java, Json, Jsoup, Gson, [Quarkus][quarkus], [Maven][maven], API_

---

## Plan

For this custom crawler, the valid sites to crawl in _(for now)_ are as follows:  

- [consumercomplaints.in](https://www.consumercomplaints.in/)
- [dthhelp.net](https://www.dthhelp.net/)
- [dth.freeforums.net](https://dth.freeforums.net/)
- [broadbandforum.co](https://broadband.forum/)

### Diagrams

- Flow of Tata Play Social CRM (by [Mahesh K. Bhat](mailto:mahesh.bhatk@tataplay.com)):

  ![Tata Play Social CRM](https://raw.githubusercontent.com/arpa2001/TataPlayStint1/main/IT_Delivery/TataPlaySocialCRMPNG.png)

- Flow of IT Delivery for this version:

  ![IT Delivery flow](https://raw.githubusercontent.com/arpa2001/TataPlayStint1/main/IT_Delivery/IT_Delivery-WorkflowJPG.jpg)

### Code

- All the sites have specific common elements that contain the form content, and each element has at least an attribute that is unique to that very post.

- The sites have data distributed in pages for efficient listing. Therefore, the crawler has to fetch the element containing link to the next page and go through every required forum listed.

- There has to be a limiting factor, like date, year, etc. This is to ensure that the crawler doesn't run indefinitely and collect unnecessary content.

- This version will be using:
  - `org.jsoup` for fetching the HTML source code of the webpages.
  - `com.google.code.gson` for parsing the listed data structure as `.json` file.

- Use of [Quarkus][quarkus] framework to handle dependencies for `Gson` and `Jsoup` libraries.  

- Using [Maven][maven] under the [Quarkus][quarkus] framework for adding the dependencies.
  - Adding `com.google.code.gson` for `Gson` library.
  - Adding `org.jsoup` for `Jsoup` library.

- Entire feature will be pushed to company portal for company-wide access.  
  Deployment, Operations, and maintenance will be structured through this portal.

- During operations the API call to upload fields to Social CRM of S360 will be configured to run on a given period.
  - Process will be a ticket generation that flows through the Social CRM.
  - A section will be added to the [Tata Play][tataplay] Social CRM that outputs the crawled data.
  - The output will be fed to Social CRM for further data specific operations as per company requirements.

### Deploy

- Deploy environment is [Quarkus][quarkus] for this version.

- Feature will be deployed on `2b_planned`.
  - `2b_planned` details

[tataplay]: https://www.tataplay.com/
[quarkus]: https://quarkus.io/
[maven]: https://maven.apache.org/
