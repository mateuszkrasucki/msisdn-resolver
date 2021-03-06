msisdn-resolver
=============

MsisdnResolver package for PHP.

A simple PHP package for interpreting MSISDN numbers. 

To use, first install dependencies using composer. 

Features
==
1. First-tier validation. 
Both MSISDN started with + and without it are accepted. Whitespaces are ignored.
2. Country code, ISO 3166-1 alpha-2 country symbol and national number identification. 
Bundled with verification, numbers starting with proper country code but with incorrect length are treated as not valid. For countries with shared country code (e.g. North America or Kazakhstan and Russia) mobile number patterns are checked.
3. Mobile network operator identification. 
Identifcation patterns data available for Poland, Slovenia, Colombia, Algeria, South Africa, Kazakhstan and Philipines. Number portability is ignored.

Usage
==
    $msisdn = new Msisdn('48729000000');
    $msisdn->getCountryCode(); // returns country dialing code string or null if not detrmined
    $msisdn->getCountryCodeString(); // returns country dialing code string or 'Unknown' if not detrmined
    $msisdn->getCountryId(); // returns ISO 3166-1 alpha-2 country symbol string or null if not determined
    $msisdn->getCountryIdString(); // returns ISO 3166-1 alpha-2 country symbol string or 'Unknown' if not detrmined
    $msisdn->getNationalNumber(); // returns national number string or null if not determined
    $msisdn->getNationalNumberString(); // returns national number string or 'Unknown' if not detrmined  
    $msisdn->getMno(); // returns mobile network operator string or null if not determined
    $msisdn->getMnoString(); // returns mobile network operator string or 'Unknown' if not detrmined    
    $msisdn->getFullString(); // returns full identifcation string in format "MNO, Country Code, National Number, Country ID"
    
Adding countries
==
MNO patterns data for countries are stored as JSON files in /src/resources. Name of the file is just country's ISO 3166-1 alpha-2 symbol.
To add MNO patterns for new countries you just have to create JSON file with the same structure and put it into 'resources' directory.    