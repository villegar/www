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

## Example (Last rendered on 2022-11-07 18:06)

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
## Reading (RDG) Station Board on 2022-11-07 18:06:36
## Time   From                                    Plat  Expected
## 17:53  Bristol Parkway                         11    Delayed
## 18:03  Didcot Parkway                          15    18:01
## 18:11  Abbey Wood                              14    On time
## 18:13  London Paddington                       -     On time
## 18:14  London Paddington                       -     Cancelled
## 18:20  Basingstoke                             -     On time
## 18:23  Cardiff Central                         9     Delayed
## 18:25  Abbey Wood                              13    On time
## 18:29  Bristol Temple Meads                    8     18:50
## 18:29  London Paddington                       -     On time
## 18:30  Basingstoke                             -     Cancelled
## 18:32  Cheltenham Spa                          -     Cancelled
## 18:32  London Paddington                       -     On time
## 18:33  Redhill                                 -     On time
## 18:37  Didcot Parkway                          -     On time
## 18:41  Abbey Wood                              14    On time
## 18:44  London Paddington                       -     On time
## 18:49  Swansea                                 -     18:59
## 18:57  London Paddington                       -     On time
## 18:58  Abbey Wood                              13    On time
## 18:58  Exeter St Davids                        -     On time
## 18:59  London Paddington                       -     On time
## 19:01  Oxford                                  -     On time
## 19:05  Gatwick Airport                         -     On time
## 19:10  Abbey Wood                              13    On time
## 19:12  Didcot Parkway                          -     On time
## 19:15  Abbey Wood                              14    On time
## 19:25  Oxford                                  -     On time
## 19:31  London Paddington                       -     On time
## 19:33  Redhill                                 -     On time
## 19:34  Cheltenham Spa                          -     Cancelled
## 19:34  London Paddington                       -     On time
## 19:37  Didcot Parkway                          -     On time
## 19:41  Abbey Wood                              13    On time
## 19:41  Bristol Temple Meads                    -     On time
## 19:45  Abbey Wood                              14    On time
## 19:49  Swansea                                 -     19:52
## 19:55  Exeter St Davids                        -     On time
## 19:58  London Paddington                       -     On time
## 20:04  Gatwick Airport                         -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-07 18:06:39
## Time   To                                      Plat  Expected
## 17:55  London Paddington                       11    Delayed
## 17:58  Didcot Parkway                          -     Delayed
## 18:03  London Paddington                       15    18:06
## 18:13  Swansea                                 -     On time
## 18:17  Abbey Wood                              13    On time
## 18:20  Redhill                                 4     On time
## 18:28  Abbey Wood                              14    On time
## 18:29  Exeter St Davids                        -     On time
## 18:32  Didcot Parkway                          -     On time
## 18:32  London Paddington                       -     Cancelled
## 18:37  London Paddington                       -     On time
## 18:47  Abbey Wood                              13    On time
## 18:49  London Paddington                       -     18:59
## 18:57  Didcot Parkway                          -     On time
## 18:58  Abbey Wood                              14    On time
## 18:58  London Paddington                       -     On time
## 18:59  Bristol Temple Meads                    -     On time
## 19:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 19:01  London Paddington                       -     On time
## 19:12  London Paddington                       -     On time
## 19:20  Redhill                                 -     On time
## 19:27  Abbey Wood                              14    On time
## 19:27  London Paddington                       -     On time
## 19:31  Exeter St Davids                        -     On time
## 19:34  Didcot Parkway                          -     On time
## 19:34  London Paddington                       -     Cancelled
## 19:37  London Paddington                       -     On time
## 19:41  London Paddington                       -     On time
## 19:49  London Paddington                       -     19:52
## 19:55  London Paddington                       -     On time
## 19:57  Abbey Wood                              13    On time
## 19:58  Bristol Temple Meads                    -     On time
```
