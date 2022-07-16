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

## Example (Last rendered on 2022-07-16 12:07)

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
## Reading (RDG) Station Board on 2022-07-16 12:07:05
## Time   From                                    Plat  Expected
## 12:47  London Paddington                       9     13:16
## 12:51  London Paddington                       8     13:18
## 12:54  Charlbury                               10    13:13
## 12:55  London Paddington                       9     13:08
## 12:59  Penzance                                11    13:01
## 13:02  Didcot Parkway                          15    12:59
## 13:03  London Paddington                       14    13:05
## 13:05  Bournemouth                             13B   13:07
## 13:10  Bristol Temple Meads                    10    13:18
## 13:11  London Paddington                       8     13:26
## 13:13  London Paddington                       12    13:19
## 13:17  London Paddington                       9     13:29
## 13:22  Basingstoke                             2     On time
## 13:25  London Paddington                       9     Delayed
## 13:26  Oxford                                  10    On time
## 13:31  Newbury                                 11    On time
## 13:33  Cheltenham Spa                          10    On time
## 13:33  Didcot Parkway                          15    On time
## 13:33  London Paddington                       14    13:49
## 13:33  Redhill                                 5     On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:40  Taunton                                 10    On time
## 13:41  Newbury                                 13    On time
## 13:43  Paignton                                11    13:48
## 13:46  Swansea                                 10    On time
## 13:47  London Paddington                       9     On time
## 13:51  Gatwick Airport                         4     13:53
## 13:51  London Paddington                       8     On time
## 13:53  Basingstoke                             2     On time
## 13:54  Charlbury                               10    13:56
## 13:55  London Paddington                       9     On time
## 13:59  Penzance                                11    On time
## 14:04  Didcot Parkway                          15    On time
## 14:06  London Paddington                       14    On time
## 14:10  Bristol Temple Meads                    10    On time
## 14:11  London Paddington                       9     On time
## 14:17  London Paddington                       9     On time
## 14:20  Basingstoke                             2     On time
## 14:25  London Paddington                       9     On time
## 14:25  Oxford                                  10    On time
## 14:30  Newbury                                 11    On time
## 14:31  Didcot Parkway                          15    On time
## 14:33  Cheltenham Spa                          10    On time
## 14:33  London Paddington                       7     On time
## 14:33  London Paddington                       14    On time
## 14:33  Redhill                                 4     On time
## 14:40  Manchester Piccadilly                   7     On time
## 14:40  Weston-super-Mare                       10    Delayed
## 14:42  Newbury                                 11    On time
## 14:43  London Paddington                       12    On time
## 14:46  Carmarthen                              10    On time
## 14:47  London Paddington                       9     On time
## 14:51  Gatwick Airport                         5     On time
## 14:51  London Paddington                       8     On time
## 14:52  Basingstoke                             2     On time
## 14:53  Charlbury                               10    On time
## 14:55  London Paddington                       9     On time
## 15:00  Penzance                                10    On time
## 15:03  London Paddington                       14    On time
## 13:32  Staines                                 BUS   On time
## 13:33  Staines                                 BUS   On time
## 13:45  Heathrow Central Bus Stn                BUS   On time
## 14:02  Staines                                 BUS   On time
## 14:03  Staines                                 BUS   On time
## 14:32  Staines                                 BUS   On time
## 14:33  Staines                                 BUS   On time
## 14:45  Heathrow Central Bus Stn                BUS   On time
## 15:02  Staines                                 BUS   On time
## 15:03  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-07-16 12:07:08
## Time   To                                      Plat  Expected
## 12:49  Oxford                                  9     13:17
## 12:53  Cheltenham Spa                          8     13:19
## 12:57  London Paddington                       10    13:14
## 12:57  Weston-super-Mare                       9     13:09
## 13:05  Basingstoke                             2     On time
## 13:05  London Paddington                       11    On time
## 13:09  Newbury                                 12    On time
## 13:12  London Paddington                       10    13:19
## 13:13  Swansea                                 8     13:27
## 13:15  Ealing Broadway                         15    On time
## 13:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 13:19  Charlbury                               9     13:30
## 13:20  Gatwick Airport                         5     On time
##        via Guildford                           
## 13:23  Didcot Parkway                          12    On time
## 13:24  Ealing Broadway                         14    On time
## 13:27  Bristol Temple Meads                    9     Delayed
## 13:28  London Paddington                       10    On time
## 13:30  Penzance                                7     Delayed
## 13:32  London Paddington                       11    On time
## 13:34  Newbury                                 8     On time
## 13:34  Redhill                                 13A   On time
## 13:35  London Paddington                       10    On time
## 13:38  Basingstoke                             2     On time
## 13:42  London Paddington                       10    On time
## 13:45  Ealing Broadway                         15    On time
## 13:45  London Paddington                       11    13:49
## 13:48  London Paddington                       10    On time
## 13:49  Oxford                                  9     On time
## 13:53  Cheltenham Spa                          8     On time
## 13:53  Didcot Parkway                          -     Cancelled
## 13:54  Ealing Broadway                         14    On time
## 13:56  London Paddington                       10    On time
## 13:57  Weston-super-Mare                       9     On time
## 14:05  London Paddington                       11    On time
## 14:07  Basingstoke                             2     On time
## 14:11  Newbury                                 13    On time
## 14:12  London Paddington                       10    On time
## 14:13  Swansea                                 9     On time
## 14:15  Ealing Broadway                         15    On time
## 14:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 14:19  Charlbury                               9     On time
## 14:20  Redhill                                 4     On time
## 14:24  Didcot Parkway                          12    On time
## 14:24  Ealing Broadway                         14    On time
## 14:27  Bristol Temple Meads                    9     On time
## 14:27  London Paddington                       10    On time
## 14:29  Penzance                                7     On time
## 14:31  London Paddington                       11    On time
## 14:34  Newbury                                 7     On time
## 14:35  London Paddington                       10    On time
## 14:37  Basingstoke                             2     On time
## 14:42  London Paddington                       10    Delayed
## 14:45  Ealing Broadway                         15    On time
## 14:48  London Paddington                       10    On time
## 14:49  Oxford                                  9     On time
## 14:53  Bournemouth                             7     On time
## 14:53  Cheltenham Spa                          8     On time
## 14:53  Didcot Parkway                          12    On time
## 14:54  Ealing Broadway                         14    On time
## 14:56  London Paddington                       10    On time
## 14:57  Weston-super-Mare                       9     On time
## 15:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 15:01  Plymouth                                7     On time
## 15:05  London Paddington                       10    On time
## 13:12  Staines                                 BUS   On time
## 13:13  Staines                                 BUS   On time
## 13:42  Staines                                 -     Cancelled
## 13:43  Staines                                 BUS   On time
## 14:00  Heathrow Central Bus Stn                BUS   On time
## 14:12  Staines                                 BUS   On time
## 14:13  Staines                                 BUS   On time
## 14:42  Staines                                 BUS   On time
## 14:43  Staines                                 BUS   On time
## 15:00  Heathrow Central Bus Stn                BUS   On time
```
