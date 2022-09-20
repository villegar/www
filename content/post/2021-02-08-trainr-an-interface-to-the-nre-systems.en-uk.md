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

## Example (Last rendered on 2022-09-20 16:03)

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
## Reading (RDG) Station Board on 2022-09-20 16:03:53
## Time   From                                    Plat  Expected
## 16:41  London Paddington                       9     17:06
## 16:45  Swansea                                 10A   17:23
## 16:56  London Paddington                       9     17:23
## 16:59  London Paddington                       7     17:24
## 17:01  Penzance                                10    17:09
## 17:03  Gatwick Airport                         5     On time
## 17:06  Bournemouth                             8     On time
## 17:09  Bristol Temple Meads                    11A   17:25
## 17:11  London Paddington                       9B    Delayed
## 17:14  London Paddington                       -     Cancelled
## 17:16  London Waterloo                         6     On time
## 17:17  Cardiff Central                         -     Cancelled
## 17:22  London Paddington                       -     Cancelled
## 17:22  Newbury                                 -     Cancelled
## 17:24  Oxford                                  10A   17:27
## 17:25  London Paddington                       8B    Delayed
## 17:26  Basingstoke                             2     On time
## 17:27  London Paddington                       7     Delayed
## 17:27  London Paddington                       13    On time
## 17:29  Cheltenham Spa                          10A   On time
## 17:34  Newbury                                 1     On time
## 17:35  Didcot Parkway                          -     Cancelled
## 17:35  London Paddington                       -     Cancelled
## 17:35  Redhill                                 5     On time
## 17:38  Bristol Temple Meads                    10    On time
## 17:41  London Paddington                       9     Delayed
## 17:41  London Paddington                       -     Cancelled
## 17:41  Manchester Piccadilly                   8     17:43
## 17:42  Exeter St Davids                        11    On time
## 17:42  London Waterloo                         4     On time
## 17:46  Basingstoke                             2     On time
## 17:47  Swansea                                 10    18:15
## 17:54  London Paddington                       -     Cancelled
## 17:55  London Paddington                       8     Delayed
## 17:56  Hereford                                10A   On time
## 17:57  Plymouth                                -     Cancelled
## 17:58  London Paddington                       9     Delayed
## 17:59  London Paddington                       13    On time
## 18:01  London Paddington                       7     Delayed
## 18:02  Gatwick Airport                         6     On time
## 18:03  Didcot Parkway                          15    On time
## 18:05  Bournemouth                             12    On time
## 18:09  Bristol Temple Meads                    11    On time
## 18:11  London Paddington                       -     Cancelled
## 18:11  London Paddington                       9     Delayed
## 18:12  London Waterloo                         5     On time
## 18:17  Cardiff Central                         -     Cancelled
## 18:20  Basingstoke                             2     On time
## 18:25  Newbury                                 -     Cancelled
## 18:26  London Paddington                       8     Delayed
## 18:26  London Paddington                       13    On time
## 18:26  Oxford                                  10    Delayed
## 18:27  London Paddington                       7     Delayed
## 18:29  Didcot Parkway                          15    On time
## 18:30  Gloucester                              11    18:37
## 18:30  London Paddington                       -     Cancelled
## 18:33  Redhill                                 4     On time
## 18:34  London Paddington                       7     Delayed
## 18:35  Newbury                                 1     On time
## 18:40  Bristol Temple Meads                    10    On time
## 18:41  London Paddington                       -     Cancelled
## 18:42  London Paddington                       9     Delayed
## 18:42  London Waterloo                         6     On time
## 18:43  Manchester Piccadilly                   8     On time
## 18:44  London Paddington                       12    On time
## 18:47  Swansea                                 10    On time
## 18:50  Basingstoke                             3     On time
## 18:53  London Paddington                       12B   Delayed
## 18:57  London Paddington                       9     Delayed
## 18:57  Penzance                                11    On time
## 18:57  Worcester Foregate Street               10    On time
## 18:58  London Paddington                       13    On time
## 18:59  London Paddington                       7     Delayed
## 17:16  Heathrow Central Bus Stn                BUS   On time
## 17:51  Heathrow Central Bus Stn                BUS   On time
## 18:26  Heathrow Central Bus Stn                BUS   On time
## 19:01  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-09-20 16:03:57
## Time   To                                      Plat  Expected
## 16:43  Swansea                                 9     17:07
## 16:47  London Paddington                       10A   17:24
## 16:58  Taunton                                 9     17:24
## 17:02  Plymouth                                7     17:25
## 17:05  London Paddington                       10    17:10
## 17:10  Newbury                                 1     On time
## 17:11  London Paddington                       11A   17:26
## 17:12  London Waterloo                         6     On time
## 17:13  Swansea                                 9B    Delayed
## 17:15  Basingstoke                             2     On time
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 17:18  Ealing Broadway                         13    On time
## 17:18  London Paddington                       -     Cancelled
## 17:20  Redhill                                 5     On time
## 17:24  London Paddington                       -     Cancelled
## 17:25  Didcot Parkway                          -     Cancelled
## 17:27  Bristol Temple Meads                    8B    Delayed
## 17:27  London Paddington                       10A   17:27
## 17:28  Ealing Broadway                         -     Cancelled
## 17:29  Penzance                                7     Delayed
## 17:32  London Paddington                       10A   On time
## 17:38  Basingstoke                             2     On time
## 17:41  London Paddington                       10    On time
## 17:41  Newbury                                 -     Cancelled
## 17:42  London Waterloo                         6     On time
## 17:43  London Paddington                       11    On time
## 17:43  Swansea                                 9     Delayed
## 17:48  Ealing Broadway                         13    On time
## 17:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:50  London Paddington                       10    18:16
## 17:52  Bournemouth                             8     On time
## 17:57  Basingstoke                             2     On time
## 17:57  Taunton                                 8     Delayed
## 17:58  Didcot Parkway                          -     Cancelled
## 17:58  Ealing Broadway                         14    On time
## 17:58  London Paddington                       -     Cancelled
## 18:00  Hereford                                9     Delayed
## 18:00  London Paddington                       10A   On time
## 18:03  Plymouth                                7     Delayed
## 18:07  Newbury                                 1     On time
## 18:12  London Paddington                       11    On time
## 18:12  London Waterloo                         4     On time
## 18:13  Carmarthen                              9     Delayed
## 18:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 18:17  Ealing Broadway                         13    On time
## 18:20  London Paddington                       -     Cancelled
## 18:20  Redhill                                 6     On time
## 18:26  London Paddington                       -     Cancelled
## 18:28  Bristol Temple Meads                    8     Delayed
## 18:28  Ealing Broadway                         14    On time
## 18:28  London Paddington                       10    Delayed
## 18:29  Penzance                                7     Delayed
## 18:32  Basingstoke                             2     On time
## 18:32  Didcot Parkway                          -     Cancelled
## 18:32  London Paddington                       11    18:38
## 18:38  Frome                                   7     Delayed
## 18:42  London Waterloo                         5     On time
## 18:43  London Paddington                       10    On time
## 18:43  Swansea                                 9     Delayed
## 18:47  Ealing Broadway                         13    On time
## 18:49  London Paddington                       10    On time
## 18:57  Didcot Parkway                          12B   Delayed
## 18:58  Ealing Broadway                         14    On time
## 18:58  London Paddington                       11    On time
## 18:59  Weston-super-Mare                       9     Delayed
## 19:00  London Paddington                       10    On time
## 19:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 19:01  Plymouth                                7     Delayed
## 17:05  Heathrow Central Bus Stn                BUS   On time
## 17:40  Heathrow Central Bus Stn                BUS   On time
## 18:15  Heathrow Central Bus Stn                BUS   On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
```
