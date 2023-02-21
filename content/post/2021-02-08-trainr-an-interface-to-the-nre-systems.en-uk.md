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

## Example (Last rendered on 2023-02-21 16:03)

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
## Reading (RDG) Station Board on 2023-02-21 16:03:40
## Time   From                                    Plat  Expected
## 14:47  London Paddington                       8B    15:41
## 15:11  London Paddington                       9     16:04
## 15:17  London Paddington                       12    16:03
## 15:25  London Paddington                       9     16:03
## 15:39  Bristol Temple Meads                    11    16:14
## 15:41  London Paddington                       9     16:05
## 15:43  London Paddington                       12    Delayed
## 15:46  London Paddington                       9     Delayed
## 15:51  London Paddington                       9B    16:09
## 15:56  London Paddington                       9     16:24
## 16:00  London Paddington                       7     16:04
## 16:02  Taunton                                 11    16:21
## 16:07  Didcot Parkway                          15    Delayed
## 16:09  Bristol Temple Meads                    10    16:27
## 16:11  Abbey Wood                              -     Cancelled
## 16:11  London Paddington                       9     16:17
## 16:11  London Waterloo                         4     On time
## 16:16  Cardiff Central                         11A   On time
## 16:17  Basingstoke                             2     On time
## 16:21  London Paddington                       12    Delayed
## 16:22  Theale                                  11    On time
## 16:24  Oxford                                  10    16:28
## 16:25  Abbey Wood                              -     Cancelled
## 16:25  London Paddington                       9     Delayed
## 16:29  Cheltenham Spa                          11A   On time
## 16:31  Didcot Parkway                          15    On time
## 16:33  London Paddington                       7     Delayed
## 16:33  Redhill                                 5     16:35
## 16:38  Abbey Wood                              14    On time
## 16:39  Manchester Piccadilly                   8     16:50
## 16:39  Plymouth                                10    On time
## 16:41  London Paddington                       9     Delayed
## 16:42  London Paddington                       12    Delayed
## 16:42  London Waterloo                         6     On time
## 16:45  Swansea                                 10    On time
## 16:46  London Paddington                       9     Delayed
## 16:50  Basingstoke                             2     On time
## 16:53  Worcester Foregate Street               -     Cancelled
## 16:55  Abbey Wood                              13    On time
## 16:56  London Paddington                       8     Delayed
## 16:59  London Paddington                       9     Delayed
## 17:03  Didcot Parkway                          15    On time
## 17:03  Gatwick Airport                         5     On time
## 17:06  Bournemouth                             8     On time
## 17:09  Paignton                                11    On time
## 17:11  Abbey Wood                              14    On time
## 17:13  Theale                                  10    On time
## 17:16  London Waterloo                         6     On time
## 17:17  Cardiff Central                         11    On time
## 17:21  Penzance                                10    On time
## 17:22  London Paddington                       12    Delayed
## 17:24  Oxford                                  11    On time
## 17:25  London Paddington                       8     On time
## 17:26  Abbey Wood                              13    On time
## 17:26  Basingstoke                             2     On time
## 17:29  Cheltenham Spa                          10    On time
## 17:35  Didcot Parkway                          15    On time
## 17:35  London Paddington                       7     On time
## 17:35  Redhill                                 5     On time
## 17:38  Bristol Temple Meads                    10    On time
## 17:40  London Paddington                       14    On time
## 17:40  Manchester Piccadilly                   8     On time
## 17:41  London Paddington                       9     On time
## 17:42  London Waterloo                         4     On time
## 17:46  Basingstoke                             2     On time
## 17:47  Swansea                                 10    On time
## 17:54  London Paddington                       12B   On time
## 17:55  London Paddington                       8     On time
## 17:56  Hereford                                -     Cancelled
## 17:58  Abbey Wood                              13    On time
## 17:58  London Paddington                       9     On time
## 17:59  London Paddington                       8     On time
## 18:02  Gatwick Airport                         5     On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-21 16:03:45
## Time   To                                      Plat  Expected
## 14:55  Didcot Parkway                          8B    16:01
## 15:13  Swansea                                 9     16:05
## 15:23  Didcot Parkway                          12    16:04
## 15:27  Bristol Temple Meads                    9     16:07
## 15:43  Cardiff Central                         9     16:06
## 15:43  London Paddington                       11    16:15
## 15:48  Worcester Foregate Street               9     Delayed
## 15:51  Didcot Parkway                          12    Delayed
## 15:53  Cheltenham Spa                          9B    16:10
## 15:58  Weston-super-Mare                       9     16:25
## 16:02  Penzance                                7     16:05
##        via Bristol                             
## 16:04  London Paddington                       11    16:22
## 16:07  Basingstoke                             2     On time
## 16:09  London Waterloo                         6     On time
## 16:12  Ealing Broadway                         15    Delayed
## 16:12  London Paddington                       10    16:29
## 16:13  Swansea                                 9     16:18
## 16:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 16:18  Abbey Wood                              13    On time
## 16:18  London Paddington                       11A   On time
## 16:19  Great Malvern                           -     Cancelled
## 16:20  Redhill                                 5     On time
## 16:24  London Paddington                       11    On time
## 16:25  Didcot Parkway                          12    Delayed
## 16:26  London Paddington                       10    16:29
## 16:27  Bristol Temple Meads                    9     Delayed
## 16:28  Abbey Wood                              -     Cancelled
## 16:32  London Paddington                       11A   On time
## 16:33  Basingstoke                             2     On time
## 16:37  Theale                                  7     Delayed
## 16:38  Ealing Broadway                         15    On time
## 16:39  London Waterloo                         4     On time
## 16:42  London Paddington                       10    On time
## 16:43  Swansea                                 9     Delayed
## 16:47  London Paddington                       10    On time
## 16:48  Abbey Wood                              -     Cancelled
## 16:48  Oxford                                  9     Delayed
## 16:50  Didcot Parkway                          12    Delayed
## 16:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:52  Bournemouth                             8     On time
## 16:57  London Paddington                       -     Cancelled
## 16:58  Abbey Wood                              14    On time
## 16:58  Taunton                                 8     Delayed
## 17:02  Penzance                                9     Delayed
## 17:09  London Waterloo                         6     On time
## 17:11  Ealing Broadway                         15    On time
## 17:11  London Paddington                       11    On time
## 17:13  Swansea                                 9     On time
## 17:14  Swansea                                 -     On time
## 17:15  Basingstoke                             2     On time
## 17:15  Birmingham New Street                   8     On time
##        via Coventry                            
## 17:15  London Paddington                       10    On time
## 17:18  Abbey Wood                              13    On time
## 17:18  London Paddington                       11    On time
## 17:20  Redhill                                 5     On time
## 17:22  London Paddington                       10    On time
## 17:25  Didcot Parkway                          12    Delayed
## 17:27  Bristol Temple Meads                    8     On time
## 17:27  London Paddington                       11    On time
## 17:28  Abbey Wood                              14    On time
## 17:32  London Paddington                       10    On time
## 17:38  Basingstoke                             2     On time
## 17:39  London Waterloo                         6     On time
## 17:41  London Paddington                       10    On time
## 17:41  Theale                                  7     On time
## 17:42  Ealing Broadway                         15    On time
## 17:43  Swansea                                 9     On time
## 17:48  Abbey Wood                              13    On time
## 17:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:50  London Paddington                       10    On time
## 17:52  Bournemouth                             8     On time
## 17:57  Basingstoke                             2     On time
## 17:57  Taunton                                 8     On time
## 17:58  Abbey Wood                              14    On time
## 17:58  Didcot Parkway                          12B   On time
## 18:00  Hereford                                9     On time
## 18:00  London Paddington                       -     Cancelled
## 18:02  Penzance                                8     On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
```
