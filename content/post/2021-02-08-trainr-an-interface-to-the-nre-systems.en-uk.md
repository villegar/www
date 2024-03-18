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

## Example (Last rendered on 2024-03-18 17:06)

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
## Reading (RDG) Station Board on 2024-03-18 17:06:05.733637
## Time   From                                    Plat  Expected
## 15:35  Didcot Parkway                          -     16:47
## 16:31  Cheltenham Spa                          -     17:06
## 16:39  Bristol Temple Meads                    -     17:01
## 16:45  Swansea                                 -     17:12
## 16:57  Worcester Foregate Street               -     17:16
## 16:58  London Paddington                       -     17:04
## 17:02  Totnes                                  -     17:08
## 17:04  Didcot Parkway                          -     Cancelled
## 17:06  Bournemouth                             -     On time
## 17:09  Weston-super-Mare                       -     17:24
## 17:11  Abbey Wood                              -     On time
## 17:11  London Paddington                       -     On time
## 17:16  London Waterloo                         -     On time
## 17:17  Cardiff Central                         -     17:24
## 17:22  Didcot Parkway                          -     On time
## 17:23  London Paddington                       -     Delayed
## 17:23  London Paddington                       -     Cancelled
## 17:26  Basingstoke                             -     Cancelled
## 17:26  London Paddington                       -     On time
## 17:29  Gatwick Airport                         -     On time
## 17:30  Cheltenham Spa                          -     On time
## 17:32  Didcot Parkway                          -     On time
## 17:33  London Paddington                       -     On time
## 17:34  Abbey Wood                              -     On time
## 17:34  Newbury                                 -     On time
## 17:39  Bristol Temple Meads                    -     On time
## 17:40  Manchester Piccadilly                   -     On time
## 17:41  Abbey Wood                              -     On time
## 17:41  London Paddington                       -     On time
## 17:42  London Waterloo                         -     On time
## 17:46  Basingstoke                             -     On time
## 17:47  Carmarthen                              -     17:50
## 17:53  London Paddington                       -     On time
## 17:53  London Paddington                       -     On time
## 17:55  London Paddington                       -     On time
## 17:57  Hereford                                -     On time
## 17:57  Totnes                                  -     On time
## 17:58  London Paddington                       -     On time
## 18:02  Gatwick Airport                         -     On time
## 18:03  Didcot Parkway                          -     On time
## 18:04  Abbey Wood                              -     On time
## 18:07  Bournemouth                             -     18:11
## 18:10  Bristol Temple Meads                    -     Delayed
## 18:11  London Paddington                       -     On time
## 18:12  Abbey Wood                              -     On time
## 18:14  London Waterloo                         -     On time
## 18:20  Basingstoke                             -     On time
## 18:21  London Paddington                       -     On time
## 18:23  Oxford                                  -     On time
## 18:24  London Paddington                       -     On time
## 18:24  London Paddington                       -     On time
## 18:25  Newbury                                 -     On time
## 18:27  Cardiff Central                         -     On time
## 18:27  London Paddington                       -     On time
## 18:30  Gatwick Airport                         -     On time
## 18:31  Didcot Parkway                          -     On time
## 18:34  Abbey Wood                              -     On time
## 18:34  Gloucester                              -     On time
## 18:34  London Paddington                       -     On time
## 18:35  Newbury                                 -     On time
## 18:40  Bristol Temple Meads                    -     On time
## 18:40  Newbury                                 -     On time
## 18:41  Manchester Piccadilly                   -     On time
## 18:42  Abbey Wood                              -     On time
## 18:42  London Paddington                       -     On time
## 18:44  London Waterloo                         -     On time
## 18:48  London Paddington                       -     On time
## 18:48  Swansea                                 -     On time
## 18:49  Basingstoke                             -     On time
## 18:54  London Paddington                       -     On time
## 18:57  London Paddington                       -     On time
## 18:57  Totnes                                  -     On time
## 18:58  Great Malvern                           -     On time
## 18:59  London Paddington                       -     On time
## 19:04  Abbey Wood                              -     On time
## 19:04  Basingstoke                             -     On time
## 19:04  Gatwick Airport                         -     On time
## 17:18  Heathrow Airport T3 (Bus)               -     On time
## 17:48  Heathrow Airport T3 (Bus)               -     On time
## 18:18  Heathrow Airport T3 (Bus)               -     On time
## 18:48  Heathrow Airport T3 (Bus)               -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-03-18 17:06:08.361902
## Time   To                                      Plat  Expected
## 15:42  London Paddington                       -     Delayed
## 16:34  London Paddington                       -     17:07
## 16:41  London Paddington                       -     17:04
## 16:47  London Paddington                       -     17:12
## 17:01  Exeter St Davids                        -     17:06
## 17:02  London Paddington                       -     17:17
## 17:05  London Paddington                       -     17:09
## 17:09  London Waterloo                         -     On time
## 17:10  Newbury                                 -     On time
## 17:11  London Paddington                       -     On time
## 17:11  London Paddington                       -     17:25
## 17:13  Swansea                                 -     On time
## 17:15  Abbey Wood                              -     On time
## 17:15  Basingstoke                             -     On time
## 17:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 17:18  London Paddington                       -     17:25
## 17:20  Gatwick Airport                         -     On time
##        via Guildford                           
## 17:20  Great Malvern                           -     On time
## 17:25  London Paddington                       -     On time
## 17:27  Bristol Temple Meads                    -     17:31
## 17:27  Didcot Parkway                          -     On time
## 17:29  Totnes                                  -     On time
## 17:32  Abbey Wood                              -     On time
## 17:33  London Paddington                       -     On time
## 17:35  Newbury                                 -     On time
## 17:38  Basingstoke                             -     On time
## 17:39  London Waterloo                         -     On time
## 17:41  London Paddington                       -     On time
## 17:42  London Paddington                       -     On time
## 17:43  Swansea                                 -     On time
## 17:46  Abbey Wood                              -     On time
## 17:48  Gatwick Airport                         -     On time
##        via Guildford                           
## 17:50  London Paddington                       -     17:50
## 17:52  Bournemouth                             -     On time
## 17:55  Taunton                                 -     On time
## 17:57  Basingstoke                             -     On time
## 17:58  Cheltenham Spa                          -     On time
## 17:58  Didcot Parkway                          -     On time
## 17:58  London Paddington                       -     On time
## 17:59  Abbey Wood                              -     On time
## 18:00  London Paddington                       -     On time
## 18:01  Hereford                                -     On time
## 18:03  Taunton                                 -     On time
## 18:06  Newbury                                 -     On time
## 18:08  London Paddington                       -     On time
## 18:09  London Waterloo                         -     On time
## 18:12  London Paddington                       -     Delayed
## 18:13  Carmarthen                              -     On time
## 18:15  Abbey Wood                              -     On time
## 18:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 18:19  Gatwick Airport                         -     On time
##        via Guildford                           
## 18:23  Worcester Foregate Street               -     On time
## 18:25  London Paddington                       -     On time
## 18:26  Bristol Temple Meads                    -     On time
## 18:27  London Paddington                       -     On time
## 18:28  Abbey Wood                              -     On time
## 18:29  Totnes                                  -     On time
## 18:30  London Paddington                       -     On time
## 18:31  Didcot Parkway                          -     On time
## 18:32  Basingstoke                             -     On time
## 18:33  London Paddington                       -     On time
## 18:36  London Paddington                       -     On time
## 18:37  Frome                                   -     On time
## 18:39  London Waterloo                         -     On time
## 18:43  London Paddington                       -     On time
## 18:43  Swansea                                 -     On time
## 18:45  Abbey Wood                              -     On time
## 18:45  London Paddington                       -     On time
## 18:49  London Paddington                       -     On time
## 18:50  Banbury                                 -     On time
## 18:52  Bournemouth                             -     On time
## 18:54  Gatwick Airport                         -     On time
##        via Guildford                           
## 18:55  Weston-super-Mare                       -     On time
## 18:58  London Paddington                       -     On time
## 18:59  Abbey Wood                              -     On time
## 18:59  Cheltenham Spa                          -     On time
## 19:00  Didcot Parkway                          -     On time
## 19:01  Taunton                                 -     On time
## 19:03  London Paddington                       -     On time
## 19:05  Basingstoke                             -     On time
## 17:30  Heathrow Airport T3 (Bus)               -     On time
## 18:00  Heathrow Airport T3 (Bus)               -     On time
## 18:30  Heathrow Airport T3 (Bus)               -     On time
## 19:00  Heathrow Airport T3 (Bus)               -     On time
```
