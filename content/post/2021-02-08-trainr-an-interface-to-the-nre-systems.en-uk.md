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

## Example (Last rendered on 2022-06-21 16:04)

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
## Reading (RDG) Station Board on 2022-06-21 16:04:43
## Time   From                                    Plat  Expected
## 16:46  Bristol Parkway                         10    17:01
## 16:56  London Paddington                       9     17:05
## 17:06  Didcot Parkway                          15    17:01
## 17:06  Southampton Central                     8     On time
## 17:09  London Paddington                       -     Cancelled
## 17:16  Castle Cary                             10    On time
## 17:16  London Paddington                       9     17:21
## 17:21  Cardiff Central                         11    17:30
## 17:24  Oxford                                  10    On time
## 17:36  London Paddington                       9     Delayed
## 17:38  Plymouth                                10    On time
## 17:39  London Paddington                       14    On time
## 17:46  Exeter St Davids                        11    On time
## 17:49  Basingstoke                             13    On time
## 17:53  Bristol Parkway                         11    On time
## 17:55  London Paddington                       8     On time
## 17:57  Oxford                                  10    Delayed
## 17:58  London Paddington                       9     On time
## 18:03  Didcot Parkway                          15    On time
## 18:09  London Paddington                       -     Cancelled
## 18:14  London Paddington                       12    On time
## 18:23  Cardiff Central                         7     On time
## 18:25  Oxford                                  13    Delayed
## 18:29  Plymouth                                8     On time
## 18:30  Basingstoke                             2     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-06-21 16:04:45
## Time   To                                      Plat  Expected
## 16:48  London Paddington                       10    17:04
## 16:52  Southampton Central                     -     17:12
## 16:58  Bristol Temple Meads                    9     17:06
## 17:16  Bristol Parkway                         9     17:22
## 17:18  London Paddington                       10    On time
## 17:22  London Paddington                       11    17:31
## 17:27  Ealing Broadway                         14    On time
## 17:27  London Paddington                       10    On time
## 17:30  Oxford                                  -     On time
## 17:31  Basingstoke                             2     On time
## 17:38  Bristol Parkway                         9     Delayed
## 17:41  London Paddington                       10    On time
## 17:46  London Paddington                       11    On time
## 17:55  London Paddington                       11    On time
## 17:57  Swindon                                 8     On time
## 17:58  Didcot Parkway                          15    On time
## 18:00  London Paddington                       10    Delayed
## 18:01  Oxford                                  9     On time
```
