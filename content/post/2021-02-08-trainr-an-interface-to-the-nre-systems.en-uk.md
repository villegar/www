---
title: 'trainR: An Interface to the National Rail Enquiries Systems'
author: Roberto Villegas-Diaz
date: '2021-02-08'
slug: trainR-an-interface-to-the-nre-systems
tags:
  - uk-railway
  - nre
Categories:
  - Development
  - R
Description: ''
Tags:
  - Development
  - R
---

<img src="https://raw.githubusercontent.com/villegar/trainR/main/inst/images/logo.png" alt="logo" align="right" height=200px/>

The goal of `trainR` is to provide a simple interface to the 
National Rail Enquiries (NRE) systems. There are few data feeds 
available, the simplest of them is Darwin, which provides real-time 
arrival and departure predictions, platform numbers, delay estimates, 
schedule changes and cancellations. Other data feeds provide historical 
data, Historic Service Performance (HSP), and much more. `trainR` 
simplifies the data retrieval, so that the users can focus on their 
analyses. For more details visit 
https://www.nationalrail.co.uk/46391.aspx.

## Installation

You can install the released version of trainR from [CRAN](https://CRAN.R-project.org) with:

``` r
install.packages("trainR")
```

And the development version from [GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("villegar/trainR", "dev")
```

## Setup
Before starting to retrieve data from the NRE data feeds, you must obtain an access token. 
Visit the following website for details: http://realtime.nationalrail.co.uk/OpenLDBWSRegistration/

Once you have received your access token, you have to store it in the `.Renviron` file; this can be 
done by executing the following command:


```r
trainR::set_token()
```

This will open a text file, `.Renviron`, add a new line at the end (as follows):

```bash
NRE="<token>"
```

`<token>` should be replaced by the access token obtained from the NRE. Save the changes and restart 
your R session.

You only need to perform this configuration once.

## Example (Last rendered on 2024-04-06 11:05)

Load `trainR` to your working environment:

```r
library(trainR)
```

### Arrivals board at Reading Station (RDG)


```r
rdg_arr <- trainR::GetArrBoardRequest("RDG")
print(rdg_arr)
```

```
## Reading (RDG) Station Board on 2024-04-06 11:05:52.589305
## Time   From                                    Plat  Expected
## 12:05  Oxford                                  12B   12:07
## 12:07  Southampton Central                     13B   On time
## 12:10  Abbey Wood                              14    On time
## 12:13  Weybridge                               -     Cancelled
## 12:19  Basingstoke                             2     On time
## 12:40  Abbey Wood                              14    On time
## 12:40  Manchester Piccadilly                   7B    On time
## 12:45  Virginia Water                          6     On time
## 13:05  Oxford                                  15    On time
## 13:06  Southampton Central                     13B   On time
## 13:10  Abbey Wood                              14    On time
## 13:13  Weybridge                               -     Cancelled
## 13:19  Basingstoke                             2     On time
## 13:40  Abbey Wood                              14    On time
## 13:41  Manchester Piccadilly                   7B    On time
## 13:48  Virginia Water                          6     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-04-06 11:05:54.720667
## Time   To                                      Plat  Expected
## 12:07  Basingstoke                             2     On time
## 12:09  Virginia Water                          6     On time
## 12:14  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 12:29  Abbey Wood                              14    On time
## 12:39  Weybridge                               -     Cancelled
## 12:52  Southampton Central                     7B    On time
## 12:53  Oxford                                  12B   On time
## 12:59  Abbey Wood                              14    On time
## 13:07  Basingstoke                             2     On time
## 13:09  Virginia Water                          6     On time
## 13:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 13:29  Abbey Wood                              14    On time
## 13:39  Weybridge                               -     Cancelled
## 13:52  Oxford                                  15B   On time
## 13:52  Southampton Central                     7B    On time
## 13:59  Abbey Wood                              14    On time
```
