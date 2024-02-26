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

## Example (Last rendered on 2024-02-26 17:06)

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
## Reading (RDG) Station Board on 2024-02-26 17:06:38.221264
## Time   From                                    Plat  Expected
## 15:57  Gatwick Airport                         5     17:13
## 16:26  London Paddington                       -     Cancelled
## 16:41  London Paddington                       -     Cancelled
## 16:42  Paignton                                -     17:09
## 16:46  London Paddington                       -     Cancelled
## 16:53  London Paddington                       -     Cancelled
## 16:55  London Paddington                       -     Cancelled
## 16:57  Worcester Shrub Hill                    -     17:06
## 16:58  London Paddington                       -     Cancelled
## 17:02  Penzance                                -     17:09
## 17:04  Gatwick Airport                         4     17:24
## 17:06  Bournemouth                             8     On time
## 17:09  Bristol Temple Meads                    -     17:36
## 17:11  Abbey Wood                              -     Cancelled
## 17:11  London Paddington                       -     Cancelled
## 17:14  Newcastle                               15    On time
## 17:16  London Waterloo                         6     On time
## 17:17  Cardiff Central                         -     Cancelled
## 17:22  Oxford                                  -     Cancelled
## 17:23  London Paddington                       -     Cancelled
## 17:23  London Paddington                       -     Cancelled
## 17:26  Basingstoke                             2     On time
## 17:26  London Paddington                       -     Cancelled
## 17:29  Gatwick Airport                         5     17:35
## 17:30  Cheltenham Spa                          -     Cancelled
## 17:32  Didcot Parkway                          15A   On time
## 17:33  London Paddington                       7B    On time
## 17:34  Abbey Wood                              -     Cancelled
## 17:34  Newbury                                 3     On time
## 17:39  Bristol Temple Meads                    -     On time
## 17:40  Manchester Piccadilly                   7     17:44
## 17:41  Abbey Wood                              -     Cancelled
## 17:41  London Paddington                       -     On time
## 17:42  Exeter St Davids                        -     Cancelled
## 17:42  London Waterloo                         4     On time
## 17:46  Basingstoke                             2     On time
## 17:47  Carmarthen                              -     17:49
## 17:53  London Paddington                       -     Cancelled
## 17:53  London Paddington                       -     Cancelled
## 17:55  London Paddington                       -     On time
## 17:57  Hereford                                -     On time
## 17:57  Plymouth                                -     18:02
## 17:58  London Paddington                       -     On time
## 18:01  London Paddington                       -     On time
## 18:02  Gatwick Airport                         5     On time
## 18:03  Didcot Parkway                          14A   On time
## 18:04  Abbey Wood                              -     Cancelled
## 18:07  Bournemouth                             7     On time
## 18:10  Bristol Temple Meads                    -     Delayed
## 18:11  London Paddington                       9     On time
## 18:12  Abbey Wood                              -     Cancelled
## 18:14  London Waterloo                         6     Delayed
## 18:17  Cardiff Central                         -     Cancelled
## 18:20  Basingstoke                             -     Cancelled
## 18:21  London Paddington                       9     On time
## 18:23  Oxford                                  -     On time
## 18:24  London Paddington                       -     Cancelled
## 18:24  London Paddington                       -     On time
## 18:25  Newbury                                 -     On time
## 18:27  London Paddington                       -     On time
## 18:30  Gatwick Airport                         -     Cancelled
## 18:31  Didcot Parkway                          -     On time
## 18:34  Abbey Wood                              -     Cancelled
## 18:34  Cheltenham Spa                          -     Cancelled
## 18:34  London Paddington                       -     On time
## 18:35  Newbury                                 1     On time
## 18:40  Bristol Temple Meads                    -     On time
## 18:40  Newbury                                 -     On time
## 18:41  Manchester Piccadilly                   7     On time
## 18:42  Abbey Wood                              -     Cancelled
## 18:42  London Paddington                       -     On time
## 18:44  London Waterloo                         5     On time
## 18:48  London Paddington                       -     On time
## 18:48  Swansea                                 -     On time
## 18:49  Basingstoke                             3     On time
## 18:54  London Paddington                       -     Cancelled
## 18:57  London Paddington                       -     On time
## 18:57  Penzance                                -     On time
## 18:58  Great Malvern                           -     Cancelled
## 18:59  London Paddington                       -     On time
## 19:04  Abbey Wood                              -     Cancelled
## 19:04  Basingstoke                             -     On time
## 19:04  Gatwick Airport                         -     Cancelled
## 19:05  Didcot Parkway                          -     On time
## 17:18  Heathrow Airport T3 (Bus)               BUS   On time
## 17:48  Heathrow Airport T3 (Bus)               BUS   On time
## 18:18  Heathrow Airport T3 (Bus)               BUS   On time
## 18:48  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-02-26 17:06:40.448821
## Time   To                                      Plat  Expected
## 16:29  Penzance                                8     17:06
## 16:43  Swansea                                 9     Delayed
## 16:44  London Paddington                       -     17:10
## 16:49  Oxford                                  -     Delayed
## 16:55  Taunton                                 11    Delayed
## 16:58  Cheltenham Spa                          -     Delayed
## 17:01  Plymouth                                -     17:07
## 17:02  London Paddington                       -     17:07
## 17:05  London Paddington                       -     17:10
## 17:09  London Waterloo                         6     On time
## 17:10  Newbury                                 1     On time
## 17:11  London Paddington                       -     17:37
## 17:13  Swansea                                 7     On time
## 17:15  Abbey Wood                              -     Cancelled
## 17:15  Basingstoke                             -     Cancelled
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 17:18  London Paddington                       -     Cancelled
## 17:20  Gatwick Airport                         4     17:27
##        via Guildford                           
## 17:20  Great Malvern                           -     On time
## 17:25  London Paddington                       -     Cancelled
## 17:27  Bristol Temple Meads                    -     On time
## 17:27  Didcot Parkway                          12    On time
## 17:29  Plymouth                                7     On time
## 17:32  Abbey Wood                              -     Cancelled
## 17:33  London Paddington                       -     Cancelled
## 17:35  Newbury                                 7B    On time
## 17:38  Basingstoke                             2     On time
## 17:39  London Waterloo                         6     On time
## 17:41  London Paddington                       -     Cancelled
## 17:42  London Paddington                       -     On time
## 17:43  Swansea                                 -     On time
## 17:44  London Paddington                       -     Cancelled
## 17:44  Newcastle                               12B   On time
##        via Doncaster                           
## 17:46  Abbey Wood                              -     Cancelled
## 17:48  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:50  London Paddington                       -     On time
## 17:52  Bournemouth                             7     On time
## 17:55  Taunton                                 -     Cancelled
## 17:57  Basingstoke                             2     On time
## 17:58  Cheltenham Spa                          -     On time
## 17:58  Didcot Parkway                          -     On time
## 17:58  London Paddington                       -     18:07
## 17:59  Abbey Wood                              -     Cancelled
## 18:00  London Paddington                       -     On time
## 18:01  Hereford                                -     On time
## 18:03  Plymouth                                -     On time
## 18:06  Newbury                                 -     On time
## 18:08  London Paddington                       -     Cancelled
## 18:09  London Waterloo                         4     On time
## 18:12  London Paddington                       -     Delayed
## 18:13  Carmarthen                              9     On time
## 18:15  Abbey Wood                              -     Cancelled
## 18:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 18:19  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:20  London Paddington                       -     Cancelled
## 18:23  Worcester Foregate Street               9     On time
## 18:25  London Paddington                       -     On time
## 18:26  Bristol Temple Meads                    -     On time
## 18:27  London Paddington                       -     On time
## 18:28  Abbey Wood                              -     Cancelled
## 18:29  Penzance                                -     On time
## 18:31  Didcot Parkway                          -     On time
## 18:32  Basingstoke                             2     On time
## 18:33  London Paddington                       -     Cancelled
## 18:36  London Paddington                       -     Cancelled
## 18:37  Frome                                   -     On time
## 18:39  London Waterloo                         6     On time
## 18:43  London Paddington                       -     On time
## 18:43  Swansea                                 -     On time
## 18:45  Abbey Wood                              -     Cancelled
## 18:45  London Paddington                       -     Cancelled
## 18:49  London Paddington                       -     On time
## 18:50  Banbury                                 -     On time
## 18:52  Bournemouth                             7     On time
## 18:54  Gatwick Airport                         4     On time
##        via Guildford                           
## 18:55  Weston-super-Mare                       -     On time
## 18:58  London Paddington                       -     On time
## 18:59  Abbey Wood                              -     Cancelled
## 18:59  Cheltenham Spa                          -     On time
## 19:00  Didcot Parkway                          -     On time
## 19:01  Plymouth                                -     On time
## 19:03  London Paddington                       -     Cancelled
## 19:05  Basingstoke                             -     On time
## 19:12  London Paddington                       -     Cancelled
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               -     On time
```
