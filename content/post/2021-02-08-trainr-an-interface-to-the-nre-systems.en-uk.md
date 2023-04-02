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

## Example (Last rendered on 2023-04-02 12:03)

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
## Reading (RDG) Station Board on 2023-04-02 12:03:20
## Time   From                                    Plat  Expected
## 12:45  Swansea                                 15    13:11
## 12:53  Penzance                                14    13:05
## 12:59  London Paddington                       7     13:04
## 13:03  Didcot Parkway                          15    On time
## 13:06  Bournemouth                             13    13:12
## 13:06  London Paddington                       9     Delayed
## 13:10  Didcot Parkway                          15    13:15
## 13:13  London Paddington                       8     On time
## 13:14  Weston-super-Mare                       14    13:35
## 13:17  Bedwyn                                  1     13:24
## 13:19  London Paddington                       9     On time
## 13:22  Swindon                                 15    Delayed
## 13:26  London Paddington                       7     On time
## 13:27  Paignton                                14    13:37
## 13:32  Basingstoke                             2     On time
## 13:39  Didcot Parkway                          7     On time
## 13:42  Bristol Temple Meads                    14    14:06
## 13:45  Swansea                                 15    13:48
## 13:53  London Paddington                       9     On time
## 13:58  Penzance                                14    14:15
## 14:03  Didcot Parkway                          15    On time
## 14:07  London Paddington                       9     On time
## 14:10  Didcot Parkway                          15    On time
## 14:14  Bristol Temple Meads                    14A   14:18
## 14:14  London Paddington                       8     On time
## 14:19  London Paddington                       9     On time
## 14:19  Newbury                                 1     On time
## 14:26  London Paddington                       7     On time
## 14:32  Basingstoke                             2     On time
## 14:39  Didcot Parkway                          13    On time
## 14:39  London Paddington                       9     On time
## 14:45  Carmarthen                              15A   15:17
## 14:53  London Paddington                       9     On time
## 14:57  Penzance                                14    15:03
## 14:59  London Paddington                       7     On time
## 13:03  Bracknell                               BUS   On time
## 13:04  Heathrow Central Bus Stn                BUS   On time
## 13:19  Bracknell                               BUS   On time
## 13:27  North Camp                              BUS   On time
## 13:33  Bracknell                               BUS   On time
## 13:34  Heathrow Central Bus Stn                BUS   On time
## 13:49  Bracknell                               BUS   On time
## 14:03  Bracknell                               -     Cancelled
## 14:04  Heathrow Central Bus Stn                BUS   On time
## 14:12  North Camp                              BUS   On time
## 14:19  Bracknell                               BUS   On time
## 14:32  North Camp                              BUS   On time
## 14:33  Bracknell                               BUS   On time
## 14:34  Heathrow Central Bus Stn                BUS   On time
## 14:49  Bracknell                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-02 12:03:26
## Time   To                                      Plat  Expected
## 12:46  London Paddington                       15    13:12
## 12:55  London Paddington                       14    13:06
## 13:01  Paignton                                7     13:05
## 13:05  London Paddington                       15    On time
## 13:09  Swansea                                 9     Delayed
## 13:14  Ealing Broadway                         15    13:16
## 13:15  Didcot Parkway                          13    On time
## 13:18  London Paddington                       14    13:36
## 13:22  Didcot Parkway                          9     On time
## 13:25  London Paddington                       15    Delayed
## 13:28  Didcot Parkway                          8     On time
## 13:28  Plymouth                                7     On time
## 13:29  London Paddington                       14    13:38
## 13:37  Basingstoke                             2     On time
## 13:43  Bedwyn                                  1     On time
## 13:44  London Paddington                       14    14:07
## 13:47  London Paddington                       15    13:49
## 13:52  Bournemouth                             7     On time
## 13:55  Bristol Temple Meads                    9     On time
## 14:00  London Paddington                       14    14:16
## 14:05  London Paddington                       15    On time
## 14:09  Carmarthen                              9     On time
## 14:14  Ealing Broadway                         15    On time
## 14:15  Didcot Parkway                          12    On time
## 14:18  London Paddington                       14A   On time
## 14:22  Didcot Parkway                          9     On time
## 14:28  Didcot Parkway                          8     On time
## 14:28  Penzance                                7     On time
## 14:37  Basingstoke                             2     On time
## 14:40  Cardiff Central                         9     On time
## 14:43  Newbury                                 1     On time
## 14:46  London Paddington                       15A   15:18
## 14:55  Taunton                                 9     On time
## 15:00  London Paddington                       14    15:04
## 15:01  Exeter St Davids                        7     On time
## 13:05  Bracknell                               -     Cancelled
## 13:21  Bracknell                               BUS   On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:30  North Camp                              BUS   On time
## 13:35  Bracknell                               BUS   On time
## 13:45  North Camp                              BUS   On time
## 13:51  Bracknell                               BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
## 14:05  Bracknell                               BUS   On time
## 14:21  Bracknell                               -     Cancelled
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:35  Bracknell                               BUS   On time
## 14:35  North Camp                              BUS   On time
## 14:51  Bracknell                               BUS   On time
## 15:00  Heathrow Airport T3 (Bus)               BUS   On time
```
