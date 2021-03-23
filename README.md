# JobAd Enrichments API 
 
        
<img src="https://github.com/JobtechSwe/docs/blob/master/img/jae_terms2.png?raw=true"
     alt="JobAd Enrichments" />      
     
 
## Getting Started 
 
***“What do employers actually want from a job seeker?”***  
JobAd Enrichments API extracts relevant labor market data from job ad texts, making it possible to automatically see what the employers need or request from the job seekers.   
This enables intelligent job matching, labor market analysis, and provides up-to-date job market terminology in a synonym dictionary   
  
 
## Table of Contents 

* [API Status and Implementation](#API-Status-and-Implementation) 
* [What the API does](#What-the-API-does) 
* [Example of use case when using the API](#Example-of-use-case-when-using-the-API) 
* [The main endpoints of the API](#The-main-endpoints-of-the-API) 
* [Start using the API (request your API key to get going today)](#Start-using-the-API) 
  
## API Status and Implementation
In order to assist in the development of our API’s we strive for early 
release in order to encourage early adoption. 
This gives us the opportunity to learn through feedback and experience. 
This is a new API and we think it is brilliant that you want to use it. 
We only ask that you contact us before implementation this API in online-systems. 
In this regards we will be able to guide and advise you as to its purpose, boundaries and limitations.  

In order to further assist in the understanding of the API, here are some general guidelines.  
- We have run successful performance tests on the API. The infrastructure for the API scales automatically.
- In the development of the API we have made certain assumptions with regards to 
skills, abilities, professional titles and geographical locations of workplaces. 
We can’t therefore guarantee a general representative definition of these 4 categories. 
The initial methodology for development was based on highlighting several positive examples 
that existed in the requested context. We then used theresult to find further examples of 
similar information types in their given context. We may therefore have missed certain 
skills, abilities, titles and geographical locations that do not follow this pattern. 
For the same reason certain fields may be positively identified that you as a user 
do not consider to be a skill, ability, title or geographical location.  
- In other words, we can’t guarantee 100% accuracy of the API at this time. 
The data-driven model we use may not always converge on all examples we consider to be positive. 
We are however proud of the ability of what this API is able to achieve and are confident 
that you as a user will find it of value.  
- We welcome feedback and insights that can help us improve the ability and performance of the API.  
  
## What the API does 
 
- Extracts found terms in a Swedish job ad text for competences, soft 
  skills, job titles and place of work and and has a prediction function 
  that tries to estimate if they are requested by the employer or not.  
  In other words, the API 
  makes it possible to extract important labor market data from raw and 
  unstructured job ad texts. 
- Returns the found job titles that the job seeker is expected to work 
  as    
- Returns the found competences/skills that the employer requests 
  from the job seeker    
- Returns the found soft skills/traits that the 
  employer requests from the job seeker    
- Returns the found places of work (city names, districts, country 
  names, names of subway stations and shuttle stations)              
- Handles singular, plural and misspelled terms       
- Handles extraction of compound words, for example ‘hälsovård’ in 
  ‘hälso- och sjukvård’ 
- Provides a synonym dictionary with job titles, competences, traits and places of work. The same synonym dictionary is used in the API for term extraction    and translation between synonyms. The dictionary is built with a bottom up approach, and only contains labor market terms that have been found in actual job ads. 
 
## Example of use case when using the API 
 
The API makes it possible to improve search results when it's used in a job search solution, since it targets the requested competences/skills/job titles and place of work from the job ad texts. In other words, the API makes it possible to filter out terms that are mentioned but which are not requested by the employer. When knowing if the terms are requested or not, low quality free text search results can be avoided. 
  
The functionality in the API has been used in [Platsbanken](https://arbetsformedlingen.se/platsbanken/) since May 2019 to improve the quality of the search results.   
   
***Example:***  
The job ads that are searchable in [Platsbanken](https://arbetsformedlingen.se/platsbanken/) are continuously enriched through the JobAd Enrichments API with concept terms, for example the concept term ‘sjuksköterska’ (‘nurse’) for job ads containing the job title in singular form or plural form or as a misspelled job title. 

The end user in [Platsbanken](https://arbetsformedlingen.se/platsbanken/) writes ‘sjuksköterskor’ (‘nurses’) as a search term, which with the help of the synonym dictionary, translates to the searchable concept term ‘sjuksköterska’ in the search query. 

Search results are returned for job ads where the employer seeks a ‘sjuksköterska’ (singular), ‘sjuksköterskor’ (plural) or ‘sjukssköterska’ (misspelled). 
 
 
## The main endpoints of the API 
 
Our API and documentation can be found at [Swagger-UI](https://jobad-enrichments-api.jobtechdev.se/)   

Brief description of the endpoints:   
 
**_/enrichtextdocuments_**  
Returns all identified terms in the ad and with a prediction for the term, a decimal between 0.0-1.0 how likely it is   
that the term is requested by the employer. The closer to 1.0 = Requested by the employer, the closer to 0.0 = Not requested by the employer.    
**_/enrichtextdocumentsbinary_**  
Returns only the requested terms when the prediction exceeds a certain classification threshold.   
If a job title or a geographical term (place of work) is mentioned in the job ad headline, the job ad will always be enriched with these terms regardless of the result of the automatic predictions.   
**_/synonymdictionary_**  
Returns data and terms for the synonym dictionary that is used in the API when extracting known labor market terms.    
Makes it possible to connect synonym terms found in the job ad text with synonym terms found in the user search input in a job ad search solution.   


## Start using the API
* To start using the API today, request your own free API key at [https://apirequest.jobtechdev.se/](https://apirequest.jobtechdev.se/)  
* When you have retrieved your API key, you can try it out in [Swagger-UI](https://jobad-enrichments-api.jobtechdev.se/)  
* For authentication, your API key must be sent as a http header parameter in every API request. See [Swagger-UI](https://jobad-enrichments-api.jobtechdev.se/) for an example request.
 
