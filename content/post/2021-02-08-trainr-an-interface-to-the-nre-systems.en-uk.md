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

## Example (Last rendered on 2023-03-29 08:03)

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
## Reading (RDG) Station Board on 2023-03-29 08:03:51
## Time   From                                    Plat  Expected
## 08:14  Worcester Shrub Hill                    -     08:34
## 08:26  Cheltenham Spa                          -     09:26
## 08:30  Plymouth                                -     09:15
## 08:35  London Paddington                       -     Delayed
## 08:39  Weston-super-Mare                       -     Delayed
## 08:41  London Paddington                       -     Delayed
## 08:44  Didcot Parkway                          -     Delayed
## 08:49  London Paddington                       -     Delayed
## 08:50  Swansea                                 -     Delayed
## 08:51  London Paddington                       -     Delayed
## 08:57  Plymouth                                -     09:42
## 09:00  Bristol Temple Meads                    10    10:07
## 09:01  Didcot Parkway                          -     Delayed
## 09:03  Taunton                                 -     09:24
## 09:04  Basingstoke                             1     09:06
## 09:04  Redhill                                 5     On time
## 09:07  Bournemouth                             8     On time
## 09:10  Newbury                                 -     Delayed
## 09:11  London Paddington                       -     Cancelled
## 09:12  Hereford                                10A   On time
## 09:13  Abbey Wood                              -     Cancelled
## 09:16  London Paddington                       -     Cancelled
## 09:16  London Waterloo                         4     On time
## 09:17  London Paddington                       -     Delayed
## 09:19  Swansea                                 -     Delayed
## 09:24  Oxford                                  -     On time
## 09:25  Gatwick Airport                         5     On time
## 09:25  London Paddington                       -     On time
## 09:26  Abbey Wood                              -     Cancelled
## 09:27  London Paddington                       -     On time
## 09:30  Liskeard                                -     Delayed
## 09:32  Worcester Shrub Hill                    -     Delayed
## 09:34  London Paddington                       -     On time
## 09:37  Didcot Parkway                          -     On time
## 09:38  Abbey Wood                              -     Cancelled
## 09:39  Taunton                                 -     Delayed
## 09:40  Nottingham                              7     09:42
## 09:41  London Paddington                       -     On time
## 09:41  Newbury                                 -     Cancelled
## 09:43  London Waterloo                         6     On time
## 09:45  London Paddington                       -     Delayed
## 09:45  Swansea                                 -     Delayed
## 09:46  Basingstoke                             2     On time
## 09:46  London Paddington                       -     On time
## 09:52  London Paddington                       -     On time
## 09:53  Banbury                                 13    On time
## 09:55  Newbury                                 -     Cancelled
## 09:55  Worcester Shrub Hill                    -     On time
## 09:56  London Paddington                       -     On time
## 10:00  London Paddington                       -     On time
## 10:02  Plymouth                                -     10:04
## 10:03  Guildford                               -     On time
## 10:06  Swansea                                 -     Delayed
## 10:07  Abbey Wood                              -     Cancelled
## 10:08  Didcot Parkway                          -     On time
## 10:11  London Paddington                       -     On time
## 10:11  Newbury                                 -     Cancelled
## 10:12  London Waterloo                         5     On time
## 10:14  Bristol Temple Meads                    -     Delayed
## 10:14  London Paddington                       -     Cancelled
## 10:18  Gatwick Airport                         6     On time
## 10:18  London Paddington                       -     On time
## 10:19  Basingstoke                             2     On time
## 10:23  Oxford                                  -     On time
## 10:25  London Paddington                       -     On time
## 10:27  London Paddington                       -     On time
## 10:28  Cheltenham Spa                          10    On time
## 10:33  London Paddington                       -     On time
## 10:36  Didcot Parkway                          -     On time
## 10:38  Newbury                                 -     On time
## 10:39  Abbey Wood                              -     On time
## 10:41  Bristol Temple Meads                    -     On time
## 10:41  London Paddington                       -     On time
## 10:43  London Waterloo                         -     On time
## 10:44  Manchester Piccadilly                   -     On time
## 10:45  Carmarthen                              -     11:00
## 10:45  Redhill                                 -     On time
## 10:46  London Paddington                       -     On time
## 10:49  London Paddington                       -     On time
## 10:51  Newbury                                 -     On time
## 10:52  London Paddington                       -     On time
## 10:53  Gatwick Airport                         -     On time
## 10:54  Great Malvern                           -     On time
## 10:55  Basingstoke                             -     On time
## 10:55  London Paddington                       -     On time
## 10:59  London Paddington                       -     On time
## 09:04  Heathrow Central Bus Stn                BUS   On time
## 09:34  Heathrow Central Bus Stn                BUS   On time
## 10:04  Heathrow Central Bus Stn                BUS   On time
## 10:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-29 08:03:56
## Time   To                                      Plat  Expected
## 08:17  London Paddington                       -     Delayed
## 08:29  London Paddington                       -     Cancelled
## 08:32  London Paddington                       -     Cancelled
## 08:36  Newbury                                 -     Delayed
## 08:36  Redhill                                 -     Delayed
## 08:41  London Paddington                       -     Cancelled
## 08:43  Cardiff Central                         -     Delayed
## 08:47  London Paddington                       -     Cancelled
## 08:53  Cheltenham Spa                          -     Delayed
## 08:53  Didcot Parkway                          -     Delayed
## 08:55  Newbury                                 -     Delayed
## 08:59  Abbey Wood                              -     09:03
## 09:00  London Paddington                       -     Cancelled
## 09:01  Gatwick Airport                         -     09:03
##        via Guildford                           
## 09:05  London Paddington                       -     Cancelled
## 09:07  Ealing Broadway                         -     Cancelled
## 09:07  London Waterloo                         4     On time
## 09:11  London Paddington                       -     Cancelled
## 09:13  Newbury                                 -     On time
## 09:13  Swansea                                 -     On time
## 09:15  London Paddington                       -     Cancelled
## 09:16  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:18  Abbey Wood                              -     On time
## 09:18  Redhill                                 -     On time
## 09:19  Great Malvern                           -     Cancelled
## 09:20  London Paddington                       -     Delayed
## 09:23  Didcot Parkway                          -     Delayed
## 09:26  London Paddington                       -     On time
## 09:27  Abbey Wood                              -     On time
## 09:27  Bristol Temple Meads                    -     On time
## 09:29  Plymouth                                -     On time
## 09:32  Basingstoke                             -     On time
## 09:32  London Paddington                       -     Delayed
## 09:35  London Paddington                       -     Delayed
## 09:36  Newbury                                 -     On time
## 09:38  Ealing Broadway                         -     On time
## 09:39  London Waterloo                         4     On time
## 09:42  London Paddington                       -     Delayed
## 09:43  Cardiff Central                         -     On time
## 09:44  London Paddington                       -     Cancelled
## 09:47  London Paddington                       -     Delayed
## 09:48  Abbey Wood                              -     On time
## 09:48  Oxford                                  -     On time
## 09:54  Cheltenham Spa                          -     On time
## 09:55  Didcot Parkway                          -     Delayed
## 09:57  Abbey Wood                              -     On time
## 09:57  London Paddington                       -     On time
## 09:58  Bristol Temple Meads                    -     On time
## 10:02  Paignton                                -     On time
## 10:04  Gatwick Airport                         -     On time
##        via Guildford                           
## 10:04  London Paddington                       -     10:04
## 10:07  Basingstoke                             -     On time
## 10:08  London Paddington                       -     Delayed
## 10:09  Ealing Broadway                         -     On time
## 10:09  London Waterloo                         6     On time
## 10:12  London Paddington                       -     On time
## 10:12  Newbury                                 -     On time
## 10:13  Swansea                                 -     On time
## 10:16  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 10:17  London Paddington                       -     Delayed
## 10:19  Hereford                                -     On time
## 10:20  Redhill                                 -     On time
## 10:23  Didcot Parkway                          -     Cancelled
## 10:26  London Paddington                       -     On time
## 10:27  Abbey Wood                              -     On time
## 10:27  Bristol Temple Meads                    -     On time
## 10:29  Plymouth                                -     On time
## 10:32  Basingstoke                             -     On time
## 10:34  London Paddington                       10    On time
## 10:37  Ealing Broadway                         -     On time
## 10:39  London Waterloo                         5     On time
## 10:39  Newbury                                 -     On time
## 10:43  Cardiff Central                         -     On time
## 10:43  London Paddington                       -     On time
## 10:48  London Paddington                       -     11:01
## 10:48  Oxford                                  -     On time
## 10:52  Bournemouth                             -     On time
## 10:53  Cheltenham Spa                          -     On time
## 10:53  Didcot Parkway                          -     On time
## 10:54  London Paddington                       -     On time
## 10:57  Abbey Wood                              -     On time
## 10:57  London Paddington                       -     On time
## 10:58  Bristol Temple Meads                    -     On time
## 11:01  Exeter St Davids                        -     On time
## 11:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               -     On time
```
