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

## Example (Last rendered on 2022-11-07 12:10)

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
## Reading (RDG) Station Board on 2022-11-07 12:10:35
## Time   From                                    Plat  Expected
## 11:46  London Paddington                       -     Delayed
## 11:51  Bristol Parkway                         -     Delayed
## 11:51  Gatwick Airport                         14    Delayed
## 11:55  London Paddington                       9     12:07
## 11:57  London Paddington                       -     12:15
## 12:13  London Paddington                       -     12:25
## 12:14  London Paddington                       -     Delayed
## 12:15  Cardiff Central                         -     Cancelled
## 12:18  London Paddington                       -     12:34
## 12:24  Oxford                                  10    Delayed
## 12:27  London Paddington                       -     On time
## 12:29  London Paddington                       -     On time
## 12:33  Guildford                               -     On time
## 12:34  Cheltenham Spa                          -     On time
## 12:37  London Paddington                       -     Cancelled
## 12:40  Abbey Wood                              14    On time
## 12:40  Bristol Temple Meads                    10    On time
## 12:42  Manchester Piccadilly                   7     On time
## 12:46  London Paddington                       9     On time
## 12:47  Swansea                                 -     On time
## 12:50  Bristol Parkway                         -     Delayed
## 12:51  Basingstoke                             2     On time
## 12:51  Gatwick Airport                         -     On time
## 12:53  London Paddington                       -     Cancelled
## 12:54  London Paddington                       9     On time
## 12:57  Great Malvern                           -     13:00
## 12:57  London Paddington                       -     On time
## 13:01  Didcot Parkway                          15    On time
## 13:04  Exeter St Davids                        -     13:06
## 13:05  Southampton Central                     8     On time
## 13:12  Abbey Wood                              14    On time
## 13:13  London Paddington                       -     On time
## 13:14  London Paddington                       9     On time
## 13:17  Cardiff Central                         -     Cancelled
## 13:18  London Paddington                       -     On time
## 13:24  Oxford                                  10    On time
## 13:27  London Paddington                       -     On time
## 13:29  London Paddington                       -     On time
## 13:33  Redhill                                 -     Delayed
## 13:34  Cheltenham Spa                          -     On time
## 13:37  London Paddington                       -     Cancelled
## 13:39  Bristol Temple Meads                    10    On time
## 13:42  Abbey Wood                              14    On time
## 13:42  Manchester Piccadilly                   7     On time
## 13:46  London Paddington                       9     On time
## 13:48  Swansea                                 -     On time
## 13:50  Bristol Parkway                         10    On time
## 13:51  Gatwick Airport                         -     On time
## 13:56  London Paddington                       9     On time
## 13:58  Basingstoke                             2     On time
## 13:58  Great Malvern                           -     14:04
## 14:03  Didcot Parkway                          15    On time
## 14:04  Exeter St Davids                        -     On time
## 14:09  Abbey Wood                              14    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-07 12:10:40
## Time   To                                      Plat  Expected
## 11:49  Oxford                                  -     Delayed
## 11:53  Didcot Parkway                          -     Delayed
## 11:55  London Paddington                       -     Delayed
## 11:57  Bristol Temple Meads                    9     12:09
## 12:07  Manchester Piccadilly                   8     12:10
##        via Coventry & Stoke-on-Trent           
## 12:13  Swansea                                 -     12:25
## 12:14  Bristol Parkway                         -     Delayed
## 12:17  London Paddington                       -     Cancelled
## 12:18  Hereford                                -     12:34
## 12:20  Redhill                                 4     On time
## 12:26  London Paddington                       10    Delayed
## 12:27  Abbey Wood                              14    On time
## 12:27  Didcot Parkway                          -     On time
## 12:29  Exeter St Davids                        -     On time
## 12:32  Basingstoke                             2     On time
## 12:34  London Paddington                       -     On time
## 12:39  Cardiff Central                         -     Cancelled
## 12:42  London Paddington                       10    On time
## 12:47  London Paddington                       -     On time
## 12:49  Oxford                                  9     On time
## 12:52  London Paddington                       -     Delayed
## 12:52  Southampton Central                     7     On time
## 12:53  Cheltenham Spa                          -     Cancelled
## 12:57  Abbey Wood                              14    On time
## 12:57  Bristol Temple Meads                    9     On time
## 12:57  Didcot Parkway                          15    On time
## 12:57  Didcot Parkway                          -     On time
## 12:57  London Paddington                       -     13:00
## 13:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 13:04  London Paddington                       -     13:06
## 13:13  Swansea                                 -     On time
## 13:14  Bristol Parkway                         9     On time
## 13:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 13:18  Worcester Foregate Street               -     On time
## 13:20  London Paddington                       -     Cancelled
## 13:26  London Paddington                       10    On time
## 13:27  Abbey Wood                              14    On time
## 13:27  Basingstoke                             2     On time
## 13:27  Didcot Parkway                          -     On time
## 13:29  Exeter St Davids                        -     On time
## 13:34  London Paddington                       -     On time
## 13:39  Cardiff Central                         -     Cancelled
## 13:42  London Paddington                       10    On time
## 13:48  London Paddington                       -     On time
## 13:48  Oxford                                  9     On time
## 13:55  Didcot Parkway                          15    On time
## 13:55  London Paddington                       10    On time
## 13:57  Abbey Wood                              14    On time
## 13:58  Bristol Temple Meads                    9     On time
## 13:58  London Paddington                       -     14:04
## 14:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 14:04  London Paddington                       -     On time
```
