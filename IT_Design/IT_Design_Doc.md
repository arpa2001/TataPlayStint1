# IT Design

&nbsp;

## Concept of custom crawlers

Websites other than social media that have forums listed in one URL rather than separate links, require crawling through to retrieve the information and complaints (if any).  

Simplify360 cannot crawl through these websites as they are URIs and not URLs.  

The solution to this problem statement is creating custom crawlers that can fetch data from corresponding webpages.  

## Approach

- Using Jsoup to fetch HTML content from the webpage.
- Using Gson to convert fetched data to `.json` file.
- Calling API to upload data to backend.

## Workflow

- Following diagram shares the code flow:  

    ![Workflow](IT_Design-WorkflowJPG.jpg)

- Codes ready in `.java` format
- Codes create `.json` file in the following format:  

    |Parameter|Description|Type|
    |---|---|:---:|
    |name|Customer Name (or ID)|Str|
    |message|Review Description Text|Str|
    |title|Review Title|Str|
    |postId|Review ID|Str|
    |postLink|Review Link|Str|
    |createdOnGMTDate|Date of Creation|Date (ISO8601)|
    |updatedOnGMTDate|Date of update|Date (ISO8601)|
    |sourceId|`rv` (constant value)|Str|
    |s_sourceName|`variable value`|Str|

- Fields will be uploaded to Social CRM using Simplify360 API syntax.
