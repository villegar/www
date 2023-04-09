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

## Example (Last rendered on 2023-04-09 12:04)

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
## Reading (RDG) Station Board on 2023-04-09 12:04:17
## Time   From                                    Plat  Expected
## 12:52  Bournemouth                             13    12:59
## 13:02  Weybridge                               4     13:04
## 13:06  London Paddington                       7     On time
## 13:09  Bristol Temple Meads                    10    13:12
## 13:10  Didcot Parkway                          14    On time
## 13:10  Redhill                                 6     13:12
## 13:13  London Paddington                       12    On time
## 13:21  Bristol Parkway                         11    On time
## 13:25  Penzance                                11    13:29
## 13:28  Didcot Parkway                          10    On time
## 13:28  London Paddington                       14    On time
## 13:32  Virginia Water                          4     On time
## 13:38  Gatwick Airport                         5     On time
## 13:44  Swansea                                 10    On time
## 13:47  London Paddington                       8     On time
## 13:53  London Paddington                       8     On time
## 13:58  London Paddington                       14    On time
## 14:02  Weybridge                               -     Cancelled
## 14:07  London Paddington                       8     On time
## 14:09  Bristol Temple Meads                    10    On time
## 14:10  Didcot Parkway                          13    On time
## 14:10  Redhill                                 6     On time
## 14:14  Penzance                                11    On time
## 14:19  London Paddington                       13    On time
## 14:25  Didcot Parkway                          10    On time
## 14:28  London Paddington                       14    On time
## 14:32  Virginia Water                          4     On time
## 14:38  Gatwick Airport                         5     On time
## 14:39  London Paddington                       8     On time
## 14:40  Didcot Parkway                          13    On time
## 14:44  Carmarthen                              10    On time
## 14:47  London Paddington                       8     On time
## 14:53  London Paddington                       8     On time
## 14:58  London Paddington                       14    On time
## 15:02  Weybridge                               4     On time
## 13:04  Heathrow Central Bus Stn                BUS   On time
## 13:23  Bramley (Hampshire)                     BUS   On time
## 13:34  Andover                                 BUS   On time
## 13:34  Heathrow Central Bus Stn                BUS   On time
## 14:04  Heathrow Central Bus Stn                BUS   On time
## 14:05  Bedwyn                                  BUS   On time
## 14:23  Basingstoke                             BUS   On time
## 14:34  Andover                                 BUS   On time
## 14:34  Heathrow Central Bus Stn                BUS   On time
## 14:51  Newbury                                 BUS   On time
## 15:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-09 12:04:22
## Time   To                                      Plat  Expected
## 13:03  Plymouth                                8     On time
## 13:10  Swansea                                 7     On time
## 13:11  London Paddington                       10    13:13
## 13:14  Ealing Broadway                         14    On time
## 13:15  Didcot Parkway                          13    On time
## 13:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 13:23  Ealing Broadway                         10    On time
## 13:23  London Paddington                       11    On time
## 13:24  Virginia Water                          4     On time
## 13:26  Didcot Parkway                          12    On time
## 13:28  London Paddington                       11    13:30
## 13:30  London Paddington                       10    On time
## 13:41  Redhill                                 6     On time
## 13:46  London Paddington                       10    On time
## 13:49  Didcot Parkway                          8     On time
## 13:53  Ealing Broadway                         14    On time
## 13:54  Weybridge                               4     On time
## 13:55  Bristol Temple Meads                    8     On time
## 14:03  Penzance                                8     On time
## 14:10  Carmarthen                              8     On time
## 14:11  London Paddington                       10    On time
## 14:14  Ealing Broadway                         13    On time
## 14:16  London Paddington                       11    On time
## 14:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 14:23  Ealing Broadway                         14    On time
## 14:24  Virginia Water                          4     On time
## 14:25  Didcot Parkway                          13    On time
## 14:26  London Paddington                       10    On time
## 14:40  Cardiff Central                         8     On time
## 14:41  Redhill                                 6     On time
## 14:46  Bournemouth                             13    On time
## 14:46  London Paddington                       10    On time
## 14:49  Didcot Parkway                          8     On time
## 14:53  Ealing Broadway                         14    On time
## 14:54  Weybridge                               4     On time
## 14:55  Bristol Temple Meads                    8     On time
## 15:03  Plymouth                                9     On time
## 13:30  Andover                                 -     Cancelled
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:38  Bramley (Hampshire)                     BUS   On time
## 13:43  Bedwyn                                  BUS   On time
## 13:52  Winchester                              BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
## 14:30  Andover                                 BUS   On time
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:38  Basingstoke                             BUS   On time
## 14:43  Newbury                                 BUS   On time
## 15:00  Heathrow Airport T3 (Bus)               BUS   On time
```
