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

## Example (Last rendered on 2024-03-20 11:06)

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
## Reading (RDG) Station Board on 2024-03-20 11:06:33.794708
## Time   From                                    Plat  Expected
## 10:58  Didcot Parkway                          -     On time
## 11:05  Gatwick Airport                         5     On time
## 11:05  Weston-super-Mare                       10    On time
## 11:06  Bournemouth                             -     On time
## 11:07  Birmingham New Street                   -     On time
## 11:10  Abbey Wood                              -     On time
## 11:11  London Paddington                       -     On time
## 11:14  London Waterloo                         -     On time
## 11:15  London Paddington                       -     On time
## 11:17  London Paddington                       -     On time
## 11:18  Cardiff Central                         -     On time
## 11:19  Basingstoke                             -     On time
## 11:22  Oxford                                  -     On time
## 11:23  London Paddington                       -     On time
## 11:28  Gatwick Airport                         -     On time
## 11:30  Didcot Parkway                          -     On time
## 11:31  Cheltenham Spa                          -     On time
## 11:33  London Paddington                       -     On time
## 11:36  Newbury                                 -     On time
## 11:38  Taunton                                 -     On time
## 11:39  London Paddington                       -     On time
## 11:40  Abbey Wood                              -     On time
## 11:40  Bristol Temple Meads                    -     On time
## 11:40  Manchester Piccadilly                   -     On time
## 11:43  London Waterloo                         -     On time
## 11:45  Swansea                                 -     On time
## 11:47  London Paddington                       -     On time
## 11:49  Basingstoke                             -     On time
## 11:50  London Paddington                       -     On time
## 11:53  London Paddington                       -     On time
## 11:55  London Paddington                       -     On time
## 11:57  Gatwick Airport                         -     On time
## 11:57  Great Malvern                           -     On time
## 11:59  Didcot Parkway                          -     On time
## 12:02  Totnes                                  -     On time
## 12:05  Bristol Temple Meads                    -     Cancelled
## 12:06  Bournemouth                             -     On time
## 12:10  Abbey Wood                              -     On time
## 12:11  London Paddington                       -     On time
## 12:11  London Waterloo                         -     On time
## 12:14  London Paddington                       -     On time
## 12:16  Cardiff Central                         -     Cancelled
## 12:16  London Paddington                       -     On time
## 12:18  Basingstoke                             -     On time
## 12:22  Newbury                                 -     On time
## 12:22  Oxford                                  -     On time
## 12:23  London Paddington                       -     On time
## 12:26  London Paddington                       -     On time
## 12:28  Gatwick Airport                         -     On time
## 12:31  Cheltenham Spa                          -     On time
## 12:32  London Paddington                       -     On time
## 12:35  Didcot Parkway                          -     On time
## 12:38  London Paddington                       -     On time
## 12:39  Manchester Piccadilly                   -     On time
## 12:40  Abbey Wood                              -     On time
## 12:40  Bristol Temple Meads                    -     On time
## 12:42  Newbury                                 -     On time
## 12:43  London Waterloo                         -     On time
## 12:44  Carmarthen                              -     On time
## 12:44  London Paddington                       -     On time
## 12:46  London Paddington                       -     On time
## 12:49  Basingstoke                             -     On time
## 12:49  Newbury                                 -     On time
## 12:53  London Paddington                       -     On time
## 12:55  London Paddington                       -     On time
## 12:57  Gatwick Airport                         -     On time
## 12:58  Great Malvern                           -     On time
## 12:58  London Paddington                       -     On time
## 11:15  Heathrow Airport T3 (Bus)               -     On time
## 11:45  Heathrow Airport T3 (Bus)               -     On time
## 12:15  Heathrow Airport T3 (Bus)               -     On time
## 12:45  Heathrow Airport T3 (Bus)               -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-03-20 11:06:36.105681
## Time   To                                      Plat  Expected
## 11:07  Basingstoke                             -     On time
## 11:07  London Paddington                       10    On time
## 11:09  London Waterloo                         -     On time
## 11:12  London Paddington                       -     On time
## 11:12  Newbury                                 -     On time
## 11:13  Swansea                                 -     On time
## 11:14  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 11:19  Worcester Shrub Hill                    -     On time
## 11:20  London Paddington                       -     On time
## 11:24  Gatwick Airport                         -     On time
##        via Guildford                           
## 11:25  Bristol Temple Meads                    -     On time
## 11:25  Didcot Parkway                          -     On time
## 11:27  London Paddington                       -     On time
## 11:29  Abbey Wood                              -     On time
## 11:32  Basingstoke                             -     On time
## 11:34  London Paddington                       -     On time
## 11:37  Newbury                                 -     On time
## 11:39  London Waterloo                         -     On time
## 11:41  Cardiff Central                         -     On time
## 11:41  London Paddington                       -     On time
## 11:41  London Paddington                       -     On time
## 11:43  London Paddington                       -     On time
## 11:45  Birmingham New Street                   -     On time
## 11:47  London Paddington                       -     On time
## 11:48  Oxford                                  -     On time
## 11:51  Bournemouth                             -     On time
## 11:51  Didcot Parkway                          -     On time
## 11:54  Gatwick Airport                         -     On time
##        via Guildford                           
## 11:55  Bristol Temple Meads                    -     On time
## 11:58  Cheltenham Spa                          -     On time
## 11:59  Abbey Wood                              -     On time
## 12:00  London Paddington                       -     On time
## 12:04  London Paddington                       -     On time
## 12:07  Basingstoke                             -     On time
## 12:07  London Paddington                       -     Cancelled
## 12:09  London Waterloo                         -     On time
## 12:12  London Paddington                       -     On time
## 12:12  Newbury                                 -     On time
## 12:13  Carmarthen                              -     On time
## 12:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 12:18  Hereford                                -     On time
## 12:18  London Paddington                       -     Cancelled
## 12:22  Didcot Parkway                          -     On time
## 12:24  Gatwick Airport                         -     On time
##        via Guildford                           
## 12:24  London Paddington                       -     On time
## 12:25  Bristol Temple Meads                    -     On time
## 12:26  London Paddington                       -     On time
## 12:29  Abbey Wood                              -     On time
## 12:29  Totnes                                  -     On time
## 12:32  Basingstoke                             -     On time
## 12:34  London Paddington                       -     On time
## 12:37  Newbury                                 -     On time
## 12:39  London Waterloo                         -     On time
## 12:40  Cardiff Central                         -     On time
## 12:42  London Paddington                       -     On time
## 12:42  London Paddington                       -     On time
## 12:47  London Paddington                       -     On time
## 12:48  Oxford                                  -     On time
## 12:51  Bournemouth                             -     On time
## 12:52  London Paddington                       -     On time
## 12:53  Didcot Parkway                          -     On time
## 12:54  Gatwick Airport                         -     On time
##        via Guildford                           
## 12:55  Weston-super-Mare                       -     On time
## 12:58  Cheltenham Spa                          -     On time
## 12:59  Abbey Wood                              -     On time
## 13:01  London Paddington                       -     On time
## 13:01  Totnes                                  -     On time
## 11:30  Heathrow Airport T3 (Bus)               -     On time
## 12:00  Heathrow Airport T3 (Bus)               -     On time
## 12:30  Heathrow Airport T3 (Bus)               -     On time
## 13:00  Heathrow Airport T3 (Bus)               -     On time
```
