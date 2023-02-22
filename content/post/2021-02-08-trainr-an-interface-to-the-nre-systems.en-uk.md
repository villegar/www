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

## Example (Last rendered on 2023-02-22 08:03)

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
## Reading (RDG) Station Board on 2023-02-22 08:03:21
## Time   From                                    Plat  Expected
## 07:34  London Paddington                       -     Delayed
## 08:02  Plymouth                                11    07:59
## 08:06  Basingstoke                             -     On time
## 08:09  Bournemouth                             -     On time
## 08:09  Oxford                                  -     On time
## 08:10  Didcot Parkway                          -     On time
## 08:11  London Paddington                       -     On time
## 08:11  London Waterloo                         -     On time
## 08:13  Abbey Wood                              -     On time
## 08:13  Theale                                  -     On time
## 08:14  Worcester Shrub Hill                    -     On time
## 08:16  London Paddington                       -     On time
## 08:16  London Paddington                       -     On time
## 08:16  Redhill                                 -     On time
## 08:18  Swansea                                 10    On time
## 08:25  London Paddington                       -     On time
## 08:26  Cheltenham Spa                          -     On time
## 08:28  Abbey Wood                              -     On time
## 08:34  Gatwick Airport                         -     08:41
## 08:35  London Paddington                       -     On time
## 08:39  Weston-super-Mare                       -     On time
## 08:41  London Paddington                       -     On time
## 08:42  Basingstoke                             -     On time
## 08:43  London Paddington                       -     On time
## 08:43  London Waterloo                         -     On time
## 08:44  Didcot Parkway                          -     On time
## 08:45  Abbey Wood                              -     On time
## 08:46  Manchester Piccadilly                   -     On time
## 08:49  London Paddington                       -     On time
## 08:51  London Paddington                       -     On time
## 08:55  London Paddington                       -     On time
## 08:56  Abbey Wood                              -     On time
## 09:00  Plymouth                                -     On time
## 09:01  Didcot Parkway                          -     On time
## 09:04  Basingstoke                             -     On time
## 09:04  Redhill                                 -     On time
## 09:07  Bournemouth                             -     On time
## 09:10  Theale                                  -     On time
## 09:11  London Paddington                       -     On time
## 09:12  Hereford                                -     On time
## 09:13  Abbey Wood                              -     On time
## 09:16  London Paddington                       -     On time
## 09:16  London Waterloo                         -     On time
## 09:17  London Paddington                       -     On time
## 09:19  Swansea                                 -     On time
## 09:21  London Paddington                       -     On time
## 09:24  Oxford                                  -     On time
## 09:25  Gatwick Airport                         -     On time
## 09:25  London Paddington                       -     On time
## 09:26  Abbey Wood                              -     On time
## 09:32  Worcester Shrub Hill                    -     On time
## 09:34  London Paddington                       -     On time
## 09:37  Didcot Parkway                          -     On time
## 09:38  Abbey Wood                              -     On time
## 09:39  Plymouth                                -     On time
## 09:40  Nottingham                              -     09:48
## 09:41  London Paddington                       -     On time
## 09:43  London Waterloo                         -     On time
## 09:45  London Paddington                       -     On time
## 09:45  Swansea                                 -     On time
## 09:46  Basingstoke                             -     On time
## 09:46  London Paddington                       -     On time
## 09:52  London Paddington                       -     On time
## 09:53  Banbury                                 -     On time
## 09:55  Worcester Shrub Hill                    -     On time
## 09:56  London Paddington                       -     On time
## 08:27  Heathrow Central Bus Stn                -     On time
## 09:04  Heathrow Central Bus Stn                -     On time
## 09:34  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-22 08:03:26
## Time   To                                      Plat  Expected
## 07:34  Theale                                  -     Delayed
## 08:00  Basingstoke                             -     On time
## 08:08  London Waterloo                         -     On time
## 08:08  London Waterloo                         -     On time
## 08:10  Abbey Wood                              -     On time
## 08:10  London Paddington                       11    On time
## 08:13  Swansea                                 -     On time
## 08:14  London Paddington                       -     On time
## 08:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 08:17  London Paddington                       -     On time
## 08:17  London Paddington                       -     On time
## 08:19  Great Malvern                           -     On time
## 08:20  Guildford                               -     On time
## 08:20  London Paddington                       10    On time
## 08:23  Basingstoke                             -     On time
## 08:25  Abbey Wood                              -     On time
## 08:26  Didcot Parkway                          -     On time
## 08:27  Bristol Temple Meads                    -     On time
## 08:29  London Paddington                       -     On time
## 08:31  London Paddington                       -     On time
## 08:36  Redhill                                 -     On time
## 08:36  Theale                                  -     On time
## 08:39  London Waterloo                         -     On time
## 08:41  London Paddington                       -     On time
## 08:42  Abbey Wood                              -     On time
## 08:43  Cardiff Central                         -     On time
## 08:46  Oxford                                  -     On time
## 08:47  London Paddington                       -     On time
## 08:52  Bournemouth                             -     On time
## 08:53  Cheltenham Spa                          -     On time
## 08:53  Didcot Parkway                          -     On time
## 08:57  Plymouth                                -     On time
##        via Bristol                             
## 08:59  Abbey Wood                              -     On time
## 08:59  Basingstoke                             -     On time
## 09:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 09:05  London Paddington                       -     On time
## 09:07  London Paddington                       -     On time
## 09:07  London Waterloo                         -     On time
## 09:11  London Paddington                       -     On time
## 09:13  Swansea                                 -     On time
## 09:15  London Paddington                       -     On time
## 09:16  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 09:18  Abbey Wood                              -     On time
## 09:18  Redhill                                 -     On time
## 09:19  Great Malvern                           -     On time
## 09:20  London Paddington                       -     On time
## 09:23  Didcot Parkway                          -     On time
## 09:23  Paignton                                -     On time
## 09:26  London Paddington                       -     On time
## 09:27  Abbey Wood                              -     On time
## 09:27  Bristol Temple Meads                    -     On time
## 09:32  Basingstoke                             -     On time
## 09:35  London Paddington                       -     On time
## 09:36  Theale                                  -     On time
## 09:38  London Paddington                       -     On time
## 09:39  London Waterloo                         -     On time
## 09:42  London Paddington                       -     On time
## 09:43  Cardiff Central                         -     On time
## 09:47  London Paddington                       -     On time
## 09:48  Abbey Wood                              -     On time
## 09:48  Oxford                                  -     On time
## 09:54  Cheltenham Spa                          -     On time
## 09:55  Didcot Parkway                          -     On time
## 09:57  Abbey Wood                              -     On time
## 09:57  London Paddington                       -     On time
## 09:58  Bristol Temple Meads                    -     On time
## 08:30  Heathrow Airport T3 (Bus)               -     On time
## 09:00  Heathrow Airport T3 (Bus)               -     On time
## 09:30  Heathrow Airport T3 (Bus)               -     On time
## 10:00  Heathrow Airport T3 (Bus)               -     On time
```
