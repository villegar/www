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

## Example (Last rendered on 2023-03-16 16:06)

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
## Reading (RDG) Station Board on 2023-03-16 16:06:55
## Time   From                                    Plat  Expected
## 15:05  Basingstoke                             8     16:10
## 15:41  Manchester Piccadilly                   8     16:04
## 16:07  Didcot Parkway                          12    16:00
## 16:11  Abbey Wood                              15    On time
## 16:19  Cardiff Central                         11A   On time
## 16:24  Oxford                                  10A   On time
## 16:25  Abbey Wood                              13    On time
## 16:38  Abbey Wood                              14    On time
## 16:39  Bristol Temple Meads                    10    On time
## 16:41  Manchester Piccadilly                   7     On time
## 16:44  Basingstoke                             2     On time
## 16:46  London Paddington                       9B    On time
## 16:52  London Paddington                       8     On time
## 16:55  Abbey Wood                              13    On time
## 16:56  London Paddington                       9     On time
## 17:06  Didcot Parkway                          12    On time
## 17:06  Southampton Central                     8     On time
## 17:11  Abbey Wood                              14    On time
## 17:21  Cardiff Central                         11    On time
## 17:24  Oxford                                  10    On time
## 17:26  Abbey Wood                              13    On time
## 17:36  London Paddington                       9     On time
## 17:38  Plymouth                                10    On time
## 17:40  Abbey Wood                              14    On time
## 17:51  Basingstoke                             13    On time
## 17:55  London Paddington                       8     On time
## 17:57  Oxford                                  10    On time
## 17:58  Abbey Wood                              13    On time
## 17:58  London Paddington                       9     On time
## 18:03  Didcot Parkway                          15    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-16 16:06:59
## Time   To                                      Plat  Expected
## 15:15  Birmingham New Street                   8     16:11
##        via Coventry                            
## 15:52  Southampton Central                     8     16:06
## 16:18  Abbey Wood                              13    On time
## 16:21  London Paddington                       11A   On time
## 16:27  London Paddington                       10A   On time
## 16:28  Abbey Wood                              15    On time
## 16:33  Basingstoke                             2     On time
## 16:42  London Paddington                       10    On time
## 16:45  London Paddington                       15    On time
## 16:48  Abbey Wood                              13    On time
## 16:48  Oxford                                  9B    On time
## 16:50  Didcot Parkway                          12    On time
## 16:52  Southampton Central                     7     On time
## 16:54  Cardiff Central                         8     On time
## 16:58  Abbey Wood                              15    On time
## 16:58  Bristol Temple Meads                    9     On time
## 17:18  Abbey Wood                              13    On time
## 17:22  London Paddington                       11    On time
## 17:27  London Paddington                       10    On time
## 17:28  Abbey Wood                              15A   On time
## 17:31  Basingstoke                             2     On time
## 17:38  Bristol Parkway                         9     On time
## 17:41  London Paddington                       10    On time
## 17:48  Abbey Wood                              13    On time
## 17:51  London Paddington                       13B   On time
## 17:57  Swindon                                 8     On time
## 17:58  Abbey Wood                              15    On time
## 17:58  Didcot Parkway                          12    On time
## 18:00  London Paddington                       10    On time
## 18:01  Oxford                                  9     On time
```
