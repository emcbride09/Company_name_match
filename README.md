## The Problem:
_"We frequently have to map informal company names to the official company name, which may differ significantly.
Demonstrate how you would carry this out mapping a British company to the data in companies house (available at https://www.gov.uk/government/publications/a-list-of-all-companies-registered-with-companies-house-to-date). You may consider the company name, location or any other information you consider relevant."_


### Defining the problem space  

Matching an informal company name to official company name. 

__Noteworthy matching issues for company names__
1. Phonetic variations: Kohl’s versus Coles
2. Typographical mistakes: Microsoft vs. Microsft
3. Contextual differences: Company vs. Organization
4. Reordered terms: Sam Hopkins vs. Hopkins Sam
5. Prefixes and suffixes: AJO Technology Company Limited vs. AJO tech Private Co., Ltd.
6. Abbreviations, nicknames, and initials: AJ Wilson vs. Alex Jane Wilson
9. Truncated letters and missing or extra spaces: Chu Kong Transport Company vs. ChuKong Transport Co. Ltd.


### Assumptions:
- The definition of an informal company name is missing. I am assuming what is meant as an example, is when someone would say:

_I work for Barclays_ rather than _I work for Barclays plc_

- The best option is to get the companies registration number, as each company in the UK is required to have one by law and it acts as a reliable unique identifier. Job done. However for the sake of the argument we need to get a non-matching name to an offical one using only the name. 
- I'm assuming the matching would need to come from a messy dataset that we need to reconfigure. 


## Solution 1 _string tokenisation and Fuzzy matching_
This won't be perfect, however it will be able to match quite a lot of similar words in orders and return a confidence score. The steps required for this project are: 

__Step 1: Data cleaning and preparation__ 
- data cleaning - removing punctuation marks that will interfer with the probability returned by the fuzzy matching
- string tokenisation - a string becomes an object to be assessed
- identify high frequency words that are unrelated to company names - make a stop words object to cleanse off
- remove company abbreviation information (Reg|Ltd|PLC|NV|LTD|LLC|INC|LLP|US) from both lists including the companies house list this will decrease the differences between the two groups while retaining all of the original information. 

__Step 2: Fuzzy matching__
- Matrix based on fuzzy match
- Assess match and longest word algorithm to return confidence score
- Assign matched name as true value

__Step 4 Assessing all Available information:__
Combine results in a table and match remaining details

## Solution 2 _API for company matching_
Considering this is a real Business problem I'm not surprised that there is an API that does it. We can develop one and use this to test against our results. Steps for using this solution are different within the business.
https://rapidapi.com/interzoid/api/company-matching-advanced

__Issues Encountered__ 
1. I can't find a list of bad company names so I'll have to make one up. There is an obvious risk for the marker, I could make my answers look really amazing by adjusing the list until the I get a positive result. I won't. I promise. 
