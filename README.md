# ssl-oauth-rproxy
Quick start SSL Termination and reverse proxy with nginx + oauth

## Introduction
There are many guides for SSL Termination, reverse proxy and authentication schemes. This guide aims to be a complete quick start guide for a narrow use case - building a web frontend box to do all of that for any number of webservices. nginx is selected as the ssl terminator and reverse proxy in this guide, as it excels performance-wise at both tasks and has a very simple yet versitile configuration. oauth2_proxy is selected as the authentication proxy as deployment is simple, and the resulting authentication interface is robust and easy to use. StartSSL is selected as the certificate authority simply because they are trusted in browser and cost-free.

Depending on level of experience, nginx can be switched for apache, authetication schemes can be swapped out... Most especially certificate authority can be changed for another favorite. A highly structured nginx configuration file hierarchy is presented, the recommendation is to stick with the presented hierarchy as the templates in the repository are most useful when the hierarchy is preserved.

## Use case
* Provide public facing web services
* Public side must be authenticated and authorized
  * Authentication uses google accounts (@gmail.com and @\<google apps domain\>)
  * Authorization by list of email addresses
  * Apps with built in authentication (ex GitLab) must bypass authentication proxy
* Public side must be secure
  * SSL with high qualsys score
  * Certificate must be trusted
  
## Assumptions
* Dedicated centos 7 machine or VM available to act as web frontend
* DNS records already in place
* For StartSSL, must be able to receive email at hostmaster@\<domain\> (or the email listed in the WHOIS record for the domain)

