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

## Example (Last rendered on 2022-11-07 10:05)

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
## Reading (RDG) Station Board on 2022-11-07 10:05:12
## Time   From                                    Plat  Expected
## 09:35  Worcester Shrub Hill                    -     Delayed
## 09:46  London Paddington                       -     Delayed
## 09:57  Oxford                                  -     Delayed
## 09:58  Bristol Parkway                         -     Delayed
## 10:07  Abbey Wood                              14    On time
## 10:09  Cardiff Central                         -     Cancelled
## 10:13  London Paddington                       -     On time
## 10:14  London Paddington                       -     Delayed
## 10:18  Redhill                                 -     10:29
## 10:19  London Paddington                       -     10:26
## 10:23  Oxford                                  -     Cancelled
## 10:27  London Paddington                       -     Cancelled
## 10:29  London Paddington                       -     On time
## 10:34  Cheltenham Spa                          10    10:40
## 10:39  Abbey Wood                              14    On time
## 10:40  Bristol Temple Meads                    10    10:43
## 10:41  London Paddington                       -     Cancelled
## 10:44  Birmingham New Street                   7     On time
## 10:45  Redhill                                 -     10:49
## 10:46  London Paddington                       9     On time
## 10:48  Swansea                                 -     11:10
## 10:53  Bristol Parkway                         11    Delayed
## 10:53  Gatwick Airport                         -     On time
## 10:53  London Paddington                       -     On time
## 10:56  Basingstoke                             2     On time
## 10:57  Great Malvern                           -     On time
## 10:57  London Paddington                       -     On time
## 11:03  Didcot Parkway                          15    On time
## 11:04  Exeter St Davids                        -     11:10
## 11:05  Southampton Central                     7     On time
## 11:12  Abbey Wood                              14    On time
## 11:13  London Paddington                       -     On time
## 11:14  London Paddington                       9     On time
## 11:16  London Paddington                       8     On time
## 11:18  Cardiff Central                         -     Cancelled
## 11:19  London Paddington                       -     On time
## 11:24  Oxford                                  10    On time
## 11:27  London Paddington                       -     On time
## 11:29  London Paddington                       -     On time
## 11:33  Redhill                                 -     On time
## 11:34  Cheltenham Spa                          -     On time
## 11:37  London Paddington                       -     Cancelled
## 11:40  Abbey Wood                              14    On time
## 11:41  Bristol Temple Meads                    10    On time
## 11:46  London Paddington                       9     On time
## 11:47  Manchester Piccadilly                   8     On time
## 11:48  Swansea                                 -     On time
## 11:50  Basingstoke                             2     On time
## 11:51  Bristol Parkway                         10    On time
## 11:51  Gatwick Airport                         -     On time
## 11:53  London Paddington                       -     Cancelled
## 11:55  London Paddington                       9     On time
## 11:58  Worcester Shrub Hill                    -     On time
## 11:59  Didcot Parkway                          15    On time
## 12:04  Exeter St Davids                        -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-07 10:05:17
## Time   To                                      Plat  Expected
## 09:35  London Paddington                       -     Delayed
## 09:48  Oxford                                  -     Delayed
## 09:57  London Paddington                       -     Delayed
## 09:59  London Paddington                       -     Delayed
## 10:04  Gatwick Airport                         4     On time
##        via Guildford                           
## 10:11  London Paddington                       -     Cancelled
## 10:12  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 10:13  Swansea                                 -     On time
## 10:14  Bristol Parkway                         -     Delayed
## 10:19  Hereford                                -     10:26
## 10:20  Redhill                                 4     On time
## 10:26  London Paddington                       -     Cancelled
## 10:27  Abbey Wood                              14    On time
## 10:27  Didcot Parkway                          -     Cancelled
## 10:29  Exeter St Davids                        -     On time
## 10:32  Basingstoke                             2     On time
## 10:34  London Paddington                       10    10:40
## 10:42  Cardiff Central                         -     Cancelled
## 10:42  London Paddington                       10    10:44
## 10:48  London Paddington                       -     11:10
## 10:48  Oxford                                  9     On time
## 10:50  Didcot Parkway                          15    On time
## 10:52  Southampton Central                     7     On time
## 10:53  Cheltenham Spa                          -     On time
## 10:55  London Paddington                       11    Delayed
## 10:57  Abbey Wood                              14    On time
## 10:57  Didcot Parkway                          -     On time
## 10:57  London Paddington                       -     On time
## 11:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 11:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 11:04  London Paddington                       -     11:10
## 11:13  Swansea                                 -     On time
## 11:14  Bristol Parkway                         9     On time
## 11:16  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 11:19  Bristol Temple Meads                    8     On time
## 11:19  Worcester Shrub Hill                    -     On time
## 11:20  London Paddington                       -     Cancelled
## 11:20  Redhill                                 -     On time
## 11:26  London Paddington                       10    On time
## 11:27  Abbey Wood                              14    On time
## 11:27  Didcot Parkway                          -     On time
## 11:29  Exeter St Davids                        -     On time
## 11:32  Basingstoke                             2     On time
## 11:34  London Paddington                       -     On time
## 11:39  Cardiff Central                         -     Cancelled
## 11:43  London Paddington                       10    On time
## 11:48  London Paddington                       -     On time
## 11:49  Oxford                                  9     On time
## 11:53  Cheltenham Spa                          -     Cancelled
## 11:53  Didcot Parkway                          15    On time
## 11:55  London Paddington                       10    On time
## 11:57  Abbey Wood                              14    On time
## 11:57  Bristol Temple Meads                    9     On time
## 11:58  London Paddington                       -     On time
## 12:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 12:04  London Paddington                       -     On time
```
