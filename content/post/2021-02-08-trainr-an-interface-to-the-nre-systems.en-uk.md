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

## Example (Last rendered on 2022-08-02 16:07)

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
## Reading (RDG) Station Board on 2022-08-02 16:07:14
## Time   From                                    Plat  Expected
## 16:59  London Paddington                       -     17:13
## 17:03  Didcot Parkway                          -     On time
## 17:06  Bournemouth                             -     17:02
## 17:09  Bristol Temple Meads                    -     17:32
## 17:11  London Paddington                       -     On time
## 17:14  London Paddington                       -     On time
## 17:16  London Waterloo                         -     On time
## 17:17  Cardiff Central                         -     17:24
## 17:22  London Paddington                       -     17:25
## 17:22  Newbury                                 -     On time
## 17:24  Oxford                                  -     On time
## 17:25  London Paddington                       -     17:34
## 17:26  Basingstoke                             -     On time
## 17:27  London Paddington                       -     17:36
## 17:27  London Paddington                       -     On time
## 17:29  Cheltenham Spa                          -     On time
## 17:34  Newbury                                 -     On time
## 17:35  Didcot Parkway                          -     On time
## 17:35  London Paddington                       -     On time
## 17:35  Redhill                                 -     On time
## 17:38  Bristol Temple Meads                    -     On time
## 17:41  London Paddington                       -     On time
## 17:41  London Paddington                       -     On time
## 17:41  Manchester Piccadilly                   -     17:43
## 17:42  Exeter St Davids                        -     On time
## 17:42  London Waterloo                         -     On time
## 17:46  Basingstoke                             -     On time
## 17:47  Swansea                                 -     On time
## 17:54  London Paddington                       -     On time
## 17:55  London Paddington                       -     On time
## 17:56  Hereford                                -     On time
## 17:57  Plymouth                                -     On time
## 17:58  London Paddington                       -     On time
## 17:59  London Paddington                       -     On time
## 18:01  London Paddington                       -     On time
## 18:02  Gatwick Airport                         -     On time
## 18:03  Didcot Parkway                          -     On time
## 18:05  Bournemouth                             -     On time
## 18:09  Bristol Temple Meads                    -     On time
## 18:11  London Paddington                       -     On time
## 18:11  London Paddington                       -     On time
## 18:12  London Waterloo                         -     On time
## 18:17  Cardiff Central                         -     18:19
## 18:20  Basingstoke                             -     On time
## 18:25  Newbury                                 -     On time
## 18:26  London Paddington                       -     On time
## 18:26  London Paddington                       -     On time
## 18:26  Oxford                                  -     On time
## 18:27  London Paddington                       -     On time
## 18:29  Didcot Parkway                          -     On time
## 18:30  Cheltenham Spa                          -     On time
## 18:30  London Paddington                       -     On time
## 18:33  Redhill                                 -     On time
## 18:34  London Paddington                       -     On time
## 18:35  Newbury                                 -     On time
## 18:40  Bristol Temple Meads                    -     On time
## 18:41  London Paddington                       -     On time
## 18:42  London Paddington                       -     On time
## 18:42  London Waterloo                         -     On time
## 18:43  Manchester Piccadilly                   -     On time
## 18:44  London Paddington                       -     On time
## 18:47  Swansea                                 -     On time
## 18:50  Basingstoke                             -     On time
## 18:53  London Paddington                       -     On time
## 18:57  Great Malvern                           -     On time
## 18:57  London Paddington                       -     On time
## 18:57  Penzance                                -     On time
## 18:58  London Paddington                       -     On time
## 18:59  London Paddington                       -     On time
## 19:04  Basingstoke                             -     On time
## 19:05  Gatwick Airport                         -     On time
## 17:16  Heathrow Central Bus Stn                -     On time
## 17:51  Heathrow Central Bus Stn                -     On time
## 18:26  Heathrow Central Bus Stn                -     On time
## 19:01  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-08-02 16:07:19
## Time   To                                      Plat  Expected
## 16:58  Taunton                                 -     Delayed
## 17:02  Plymouth                                -     17:14
## 17:10  Newbury                                 -     On time
## 17:11  Ealing Broadway                         -     On time
## 17:11  London Paddington                       -     17:33
## 17:12  London Waterloo                         -     On time
## 17:13  Swansea                                 -     On time
## 17:15  Basingstoke                             -     On time
## 17:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 17:18  Ealing Broadway                         -     On time
## 17:18  London Paddington                       -     17:25
## 17:20  Redhill                                 -     On time
## 17:24  London Paddington                       -     On time
## 17:25  Didcot Parkway                          -     17:25
## 17:27  Bristol Temple Meads                    -     17:35
## 17:27  London Paddington                       -     On time
## 17:28  Ealing Broadway                         -     On time
## 17:29  Penzance                                -     17:37
## 17:32  London Paddington                       -     On time
## 17:38  Basingstoke                             -     On time
## 17:41  London Paddington                       -     On time
## 17:41  Newbury                                 -     On time
## 17:42  Ealing Broadway                         -     On time
## 17:42  London Waterloo                         -     On time
## 17:43  London Paddington                       -     On time
## 17:43  Swansea                                 -     On time
## 17:48  Ealing Broadway                         -     On time
## 17:50  Gatwick Airport                         -     On time
##        via Guildford                           
## 17:50  London Paddington                       -     On time
## 17:52  Bournemouth                             -     On time
## 17:57  Basingstoke                             -     On time
## 17:57  Taunton                                 -     On time
## 17:58  Didcot Parkway                          -     On time
## 17:58  Ealing Broadway                         -     On time
## 17:58  London Paddington                       -     On time
## 18:00  Hereford                                -     On time
## 18:00  London Paddington                       -     On time
## 18:03  Plymouth                                -     On time
## 18:07  Newbury                                 -     On time
## 18:08  Ealing Broadway                         -     On time
## 18:12  London Paddington                       -     On time
## 18:12  London Waterloo                         -     On time
## 18:13  Carmarthen                              -     On time
## 18:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 18:17  Ealing Broadway                         -     On time
## 18:20  London Paddington                       -     On time
## 18:20  Redhill                                 -     On time
## 18:26  London Paddington                       -     On time
## 18:28  Bristol Temple Meads                    -     On time
## 18:28  Ealing Broadway                         -     On time
## 18:28  London Paddington                       -     On time
## 18:29  Penzance                                -     On time
## 18:32  Basingstoke                             -     On time
## 18:32  Didcot Parkway                          -     On time
## 18:32  London Paddington                       -     On time
## 18:37  Ealing Broadway                         -     On time
## 18:38  Frome                                   -     On time
## 18:42  London Waterloo                         -     On time
## 18:43  London Paddington                       -     On time
## 18:43  Swansea                                 -     On time
## 18:47  Ealing Broadway                         -     On time
## 18:49  London Paddington                       -     On time
## 18:57  Didcot Parkway                          -     On time
## 18:58  Ealing Broadway                         -     On time
## 18:58  London Paddington                       -     On time
## 18:59  Weston-super-Mare                       -     On time
## 19:00  London Paddington                       -     On time
## 19:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 19:01  Plymouth                                -     On time
## 19:05  Basingstoke                             -     On time
## 17:40  Heathrow Central Bus Stn                -     On time
## 18:15  Heathrow Central Bus Stn                -     On time
## 19:00  Heathrow Central Bus Stn                -     On time
```
