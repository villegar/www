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

## Example (Last rendered on 2022-11-07 16:05)

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
## Reading (RDG) Station Board on 2022-11-07 16:05:44
## Time   From                                    Plat  Expected
## 15:46  London Paddington                       -     Delayed
## 15:50  Bristol Parkway                         -     Delayed
## 16:04  Exeter St Davids                        -     16:20
## 16:07  Didcot Parkway                          14    16:02
## 16:11  Abbey Wood                              14    On time
## 16:13  London Paddington                       -     On time
## 16:14  London Paddington                       -     Delayed
## 16:19  Cardiff Central                         -     Cancelled
## 16:19  London Paddington                       -     Delayed
## 16:24  Oxford                                  10    Delayed
## 16:26  Abbey Wood                              13    On time
## 16:29  London Paddington                       -     16:39
## 16:32  Cheltenham Spa                          -     Cancelled
## 16:33  Redhill                                 -     On time
## 16:38  Didcot Parkway                          -     On time
## 16:39  Abbey Wood                              14    On time
## 16:39  Bristol Temple Meads                    10    On time
## 16:42  Manchester Piccadilly                   7     On time
## 16:44  Basingstoke                             2     On time
## 16:46  Bristol Parkway                         10    Delayed
## 16:46  London Paddington                       9     On time
## 16:47  Swansea                                 -     16:49
## 16:52  London Paddington                       -     Cancelled
## 16:56  Abbey Wood                              13    On time
## 16:56  London Paddington                       9     On time
## 16:57  London Paddington                       -     On time
## 16:57  Worcester Foregate Street               -     On time
## 17:03  Gatwick Airport                         -     On time
## 17:06  Didcot Parkway                          15    On time
## 17:06  Exeter St Davids                        -     17:15
## 17:06  Southampton Central                     8     On time
## 17:13  London Paddington                       -     On time
## 17:14  Abbey Wood                              14    On time
## 17:16  London Paddington                       9     On time
## 17:21  Cardiff Central                         -     Cancelled
## 17:24  Oxford                                  10    On time
## 17:27  Abbey Wood                              13    On time
## 17:29  London Paddington                       -     On time
## 17:32  Cheltenham Spa                          -     Cancelled
## 17:35  Redhill                                 -     On time
## 17:36  London Paddington                       9     On time
## 17:38  Bristol Temple Meads                    10    On time
## 17:41  Abbey Wood                              14    On time
## 17:42  Didcot Parkway                          -     On time
## 17:49  Basingstoke                             12    On time
## 17:50  Swansea                                 -     On time
## 17:53  Bristol Parkway                         11    On time
## 17:55  London Paddington                       -     Cancelled
## 17:57  London Paddington                       -     On time
## 17:57  Oxford                                  10    On time
## 17:58  Exeter St Davids                        -     Cancelled
## 17:58  London Paddington                       9     On time
## 17:59  Abbey Wood                              13    On time
## 18:02  Gatwick Airport                         -     On time
## 18:03  Didcot Parkway                          15    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-07 16:05:49
## Time   To                                      Plat  Expected
## 15:48  Oxford                                  -     Delayed
## 15:55  London Paddington                       -     Delayed
## 16:01  Gatwick Airport                         4     Delayed
##        via Guildford                           
## 16:04  London Paddington                       -     16:20
## 16:07  London Paddington                       14    On time
## 16:13  Swansea                                 -     On time
## 16:14  Bristol Parkway                         -     Delayed
## 16:18  Abbey Wood                              13    On time
## 16:19  Great Malvern                           -     Delayed
## 16:20  Redhill                                 5     On time
## 16:21  London Paddington                       -     Cancelled
## 16:27  London Paddington                       10    Delayed
## 16:28  Abbey Wood                              14    On time
## 16:29  Exeter St Davids                        -     16:39
## 16:32  London Paddington                       -     Cancelled
## 16:33  Basingstoke                             2     On time
## 16:38  London Paddington                       -     On time
## 16:42  London Paddington                       10    On time
## 16:47  London Paddington                       -     16:49
## 16:48  Abbey Wood                              13    On time
## 16:48  London Paddington                       10    Delayed
## 16:48  Oxford                                  9     On time
## 16:50  Didcot Parkway                          15    On time
## 16:50  Gatwick Airport                         -     On time
##        via Guildford                           
## 16:52  Southampton Central                     7     On time
## 16:54  Cardiff Central                         -     Cancelled
## 16:57  Didcot Parkway                          -     On time
## 16:57  London Paddington                       -     On time
## 16:58  Abbey Wood                              14    On time
## 16:58  Bristol Temple Meads                    9     On time
## 17:06  London Paddington                       -     17:15
## 17:13  Swansea                                 -     On time
## 17:16  Bristol Parkway                         9     On time
## 17:18  Abbey Wood                              13    On time
## 17:22  London Paddington                       -     Cancelled
## 17:27  London Paddington                       10    On time
## 17:28  Abbey Wood                              14    On time
## 17:29  Exeter St Davids                        -     On time
## 17:31  Basingstoke                             2     On time
## 17:32  London Paddington                       -     Cancelled
## 17:38  Bristol Parkway                         9     On time
## 17:41  London Paddington                       10    On time
## 17:42  London Paddington                       -     On time
## 17:48  Abbey Wood                              13    On time
## 17:50  London Paddington                       -     On time
## 17:55  London Paddington                       11    On time
## 17:57  Bristol Temple Meads                    -     On time
## 17:57  Swindon                                 -     Cancelled
## 17:58  Abbey Wood                              14    On time
## 17:58  Didcot Parkway                          15    On time
## 17:58  London Paddington                       -     Cancelled
## 18:00  London Paddington                       10    On time
## 18:01  Oxford                                  9     On time
## 18:03  London Paddington                       15    On time
```
