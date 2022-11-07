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

## Example (Last rendered on 2022-11-07 08:05)

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
## Reading (RDG) Station Board on 2022-11-07 08:05:11
## Time   From                                    Plat  Expected
## 07:56  Hereford                                -     Delayed
## 08:06  Basingstoke                             -     08:11
## 08:07  Didcot Parkway                          15    Delayed
## 08:09  Oxford                                  10    08:14
## 08:13  London Paddington                       -     On time
## 08:14  Abbey Wood                              14    On time
## 08:14  London Paddington                       9     Delayed
## 08:16  Redhill                                 -     Delayed
## 08:19  London Paddington                       -     08:29
## 08:20  Swansea                                 -     On time
## 08:23  Bristol Parkway                         10    Delayed
## 08:26  London Paddington                       -     08:46
## 08:29  Cheltenham Spa                          -     08:32
## 08:29  London Paddington                       7     On time
## 08:31  Abbey Wood                              14    On time
## 08:34  Guildford                               -     Delayed
## 08:36  London Paddington                       -     Cancelled
## 08:39  Bristol Temple Meads                    11    On time
## 08:40  London Paddington                       8     On time
## 08:42  Basingstoke                             2     On time
## 08:43  London Paddington                       9     On time
## 08:45  Abbey Wood                              12    On time
## 08:48  Swindon                                 10    On time
## 08:53  London Paddington                       -     On time
## 08:56  Abbey Wood                              13    On time
## 08:56  Exeter St Davids                        -     On time
## 08:56  London Paddington                       -     Delayed
## 09:01  Didcot Parkway                          15    On time
## 09:04  Redhill                                 -     09:08
## 09:05  Southampton Central                     8     On time
## 09:13  Abbey Wood                              14    On time
## 09:13  Bristol Parkway                         -     On time
## 09:13  Hereford                                -     On time
## 09:13  London Paddington                       -     On time
## 09:15  Cardiff Central                         10    On time
## 09:18  London Paddington                       9     On time
## 09:18  London Paddington                       -     On time
## 09:24  Oxford                                  10    On time
## 09:25  Gatwick Airport                         -     09:28
## 09:26  Abbey Wood                              13    On time
## 09:26  London Paddington                       -     Cancelled
## 09:29  London Paddington                       -     On time
## 09:32  Exeter St Davids                        -     On time
## 09:35  Worcester Shrub Hill                    -     Delayed
## 09:38  Abbey Wood                              14    On time
## 09:46  Basingstoke                             2     On time
## 09:46  London Paddington                       9     On time
## 09:47  Swansea                                 -     On time
## 09:50  Bristol Temple Meads                    11    On time
## 09:54  London Paddington                       -     On time
## 09:56  London Paddington                       9     On time
## 09:57  London Paddington                       -     On time
## 09:58  Bristol Parkway                         10    On time
## 10:01  Didcot Parkway                          15    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-07 08:05:15
## Time   To                                      Plat  Expected
## 07:38  Cardiff Central                         -     Delayed
## 07:49  Oxford                                  -     Delayed
## 07:52  Didcot Parkway                          13B   Delayed
## 07:56  London Paddington                       -     Delayed
## 08:10  Abbey Wood                              13B   On time
## 08:13  Swansea                                 -     On time
## 08:14  Bristol Parkway                         9     Delayed
## 08:14  London Paddington                       10    08:15
## 08:19  Great Malvern                           -     08:29
## 08:20  London Paddington                       -     On time
## 08:23  Basingstoke                             7     On time
## 08:25  London Paddington                       10    Delayed
## 08:26  Didcot Parkway                          -     08:46
## 08:27  Abbey Wood                              14    On time
## 08:29  Exeter St Davids                        7     On time
## 08:29  London Paddington                       -     08:32
## 08:36  Redhill                                 -     On time
## 08:38  Cardiff Central                         -     Cancelled
## 08:41  London Paddington                       11    On time
## 08:42  Abbey Wood                              14    On time
## 08:42  Bristol Temple Meads                    8     On time
## 08:46  Oxford                                  9     On time
## 08:49  London Paddington                       10    On time
## 08:53  Cheltenham Spa                          -     On time
## 08:53  Didcot Parkway                          15    On time
## 08:56  Didcot Parkway                          -     Delayed
## 08:56  London Paddington                       -     On time
## 08:57  Abbey Wood                              12    On time
## 09:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 09:10  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:13  London Paddington                       -     On time
## 09:13  London Paddington                       -     On time
## 09:13  Swansea                                 -     On time
## 09:17  London Paddington                       10    On time
## 09:18  Abbey Wood                              13    On time
## 09:18  Great Malvern                           -     On time
## 09:19  Bristol Parkway                         9     On time
## 09:20  Redhill                                 -     On time
## 09:26  London Paddington                       10    On time
## 09:27  Abbey Wood                              14    On time
## 09:28  Cardiff Central                         -     Cancelled
## 09:29  Exeter St Davids                        -     On time
## 09:32  Basingstoke                             2     On time
## 09:32  London Paddington                       -     On time
## 09:35  London Paddington                       -     Delayed
## 09:47  London Paddington                       -     On time
## 09:48  Abbey Wood                              13    On time
## 09:48  Oxford                                  9     On time
## 09:54  Cheltenham Spa                          -     On time
## 09:55  Didcot Parkway                          15    On time
## 09:55  London Paddington                       11    On time
## 09:57  Abbey Wood                              14    On time
## 09:57  Didcot Parkway                          -     On time
## 09:58  Bristol Temple Meads                    9     On time
## 09:59  London Paddington                       10    On time
## 10:04  Gatwick Airport                         -     On time
##        via Guildford
```
