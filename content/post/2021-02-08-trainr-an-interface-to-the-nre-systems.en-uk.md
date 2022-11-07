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

## Example (Last rendered on 2022-11-07 14:10)

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
## Reading (RDG) Station Board on 2022-11-07 14:11:01
## Time   From                                    Plat  Expected
## 13:46  London Paddington                       9     Delayed
## 13:50  Bristol Parkway                         -     Delayed
## 14:04  Exeter St Davids                        -     14:27
## 14:08  Didcot Parkway                          15    13:59
## 14:13  London Paddington                       9     14:10
## 14:14  London Paddington                       9     Delayed
## 14:18  London Paddington                       -     On time
## 14:20  Cardiff Central                         -     Cancelled
## 14:24  Oxford                                  10    Delayed
## 14:27  London Paddington                       -     14:29
## 14:29  London Paddington                       -     On time
## 14:33  Redhill                                 -     On time
## 14:35  Cheltenham Spa                          -     14:40
## 14:37  Didcot Parkway                          -     On time
## 14:37  London Paddington                       -     Cancelled
## 14:40  Abbey Wood                              14    On time
## 14:40  Bristol Temple Meads                    10    On time
## 14:41  Manchester Piccadilly                   7     14:44
## 14:46  London Paddington                       9     On time
## 14:48  Swansea                                 -     14:51
## 14:50  Bristol Parkway                         10    Delayed
## 14:51  Basingstoke                             2     On time
## 14:51  Gatwick Airport                         -     On time
## 14:55  London Paddington                       9     On time
## 14:57  London Paddington                       -     On time
## 14:59  Didcot Parkway                          15    On time
## 15:04  Exeter St Davids                        -     On time
## 15:05  Southampton Central                     8     On time
## 15:13  Abbey Wood                              14    On time
## 15:13  London Paddington                       -     On time
## 15:14  London Paddington                       9     On time
## 15:18  London Paddington                       -     On time
## 15:19  Cardiff Central                         -     Cancelled
## 15:25  Oxford                                  10    On time
## 15:27  London Paddington                       -     On time
## 15:29  London Paddington                       -     On time
## 15:33  Redhill                                 -     On time
## 15:34  Cheltenham Spa                          -     Cancelled
## 15:37  London Paddington                       -     Cancelled
## 15:39  Abbey Wood                              14    On time
## 15:39  Bristol Temple Meads                    11    On time
## 15:42  Didcot Parkway                          -     On time
## 15:42  Manchester Piccadilly                   7     On time
## 15:45  Swansea                                 -     On time
## 15:46  London Paddington                       9     On time
## 15:48  London Paddington                       -     On time
## 15:50  Bristol Parkway                         10    On time
## 15:51  Gatwick Airport                         -     On time
## 15:56  Hereford                                -     On time
## 15:56  London Paddington                       9     On time
## 15:57  Basingstoke                             2     On time
## 16:04  Exeter St Davids                        -     On time
## 16:07  Didcot Parkway                          15    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-07 14:11:05
## Time   To                                      Plat  Expected
## 13:48  Oxford                                  9     Delayed
## 13:55  London Paddington                       -     Delayed
## 14:01  Gatwick Airport                         13A   Delayed
##        via Guildford                           
## 14:04  London Paddington                       -     14:27
## 14:08  London Paddington                       15    14:10
## 14:13  Swansea                                 9     On time
## 14:14  Bristol Parkway                         9     Delayed
## 14:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 14:18  Great Malvern                           -     On time
## 14:20  Redhill                                 4     On time
## 14:23  Basingstoke                             2     On time
## 14:23  London Paddington                       -     Cancelled
## 14:27  Abbey Wood                              14    On time
## 14:27  Didcot Parkway                          -     14:29
## 14:27  London Paddington                       10    Delayed
## 14:29  Exeter St Davids                        -     On time
## 14:35  London Paddington                       -     14:40
## 14:37  London Paddington                       -     On time
## 14:39  Cardiff Central                         -     Cancelled
## 14:43  London Paddington                       10    On time
## 14:48  London Paddington                       -     14:51
## 14:49  Oxford                                  9     On time
## 14:52  London Paddington                       10    Delayed
## 14:52  Southampton Central                     7     On time
## 14:55  Didcot Parkway                          15    On time
## 14:57  Abbey Wood                              14    On time
## 14:57  Bristol Temple Meads                    9     On time
## 14:57  Didcot Parkway                          -     On time
## 15:04  London Paddington                       -     On time
## 15:13  Swansea                                 -     On time
## 15:14  Bristol Parkway                         9     On time
## 15:15  Birmingham New Street                   8     On time
##        via Coventry                            
## 15:18  Redhill                                 -     On time
## 15:18  Worcester Foregate Street               -     On time
## 15:22  London Paddington                       -     Cancelled
## 15:27  Abbey Wood                              14    On time
## 15:27  Didcot Parkway                          -     On time
## 15:27  London Paddington                       10    On time
## 15:29  Exeter St Davids                        -     On time
## 15:34  London Paddington                       -     Cancelled
## 15:35  Basingstoke                             2     On time
## 15:39  Cardiff Central                         -     Cancelled
## 15:42  London Paddington                       -     On time
## 15:43  London Paddington                       11    On time
## 15:45  London Paddington                       -     On time
## 15:48  Oxford                                  9     On time
## 15:48  Worcester Foregate Street               -     On time
## 15:51  Didcot Parkway                          15    On time
## 15:52  Southampton Central                     7     On time
## 15:55  London Paddington                       10    On time
## 15:56  London Paddington                       -     On time
## 15:58  Abbey Wood                              14    On time
## 15:58  Bristol Temple Meads                    9     On time
## 16:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 16:04  London Paddington                       -     On time
```
