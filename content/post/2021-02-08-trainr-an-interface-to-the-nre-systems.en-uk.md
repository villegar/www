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

## Example (Last rendered on 2021-10-31 14:08)

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
## Reading (RDG) Station Board on 2021-10-31 14:08:08
## Time   From                                    Plat  Expected
## 13:09  Weston-super-Mare                       10A   14:06
## 13:20  Swansea                                 10    14:13
## 13:53  London Paddington                       9     14:10
## 13:56  Great Malvern                           10A   14:20
## 13:58  Penzance                                11    14:10
## 14:01  London Paddington                       9     14:22
## 14:09  Bristol Temple Meads                    10    14:28
## 14:10  Didcot Parkway                          14A   14:14
## 14:12  London Paddington                       9     14:15
## 14:12  Reigate                                 15    On time
## 14:13  London Paddington                       13    14:16
## 14:17  Swansea                                 11    14:33
## 14:19  Newbury                                 1     14:24
## 14:24  London Paddington                       12B   On time
## 14:28  London Paddington                       7     On time
## 14:35  Ascot                                   4     On time
## 14:38  Shalford                                5     On time
## 14:41  Manchester Piccadilly                   13    14:52
## 14:44  London Paddington                       14    On time
## 14:53  London Paddington                       9     On time
## 14:55  Bournemouth                             13    On time
## 14:57  Hereford                                10A   On time
## 14:57  Penzance                                11    15:01
## 14:59  London Paddington                       -     Cancelled
## 15:01  London Paddington                       9     On time
## 15:05  Ascot                                   4     On time
## 15:09  Weston-super-Mare                       11    On time
## 15:11  Guildford                               6     On time
## 15:12  London Paddington                       9     On time
## 15:13  Didcot Parkway                          15    On time
## 15:13  London Paddington                       14    On time
## 15:19  Bedwyn                                  3     On time
## 15:21  Swansea                                 10    On time
## 15:23  London Paddington                       12B   On time
## 15:26  London Paddington                       7     On time
## 15:35  Ascot                                   4     On time
## 15:38  Redhill                                 -     Cancelled
## 15:39  Manchester Piccadilly                   13    15:43
## 15:40  Bristol Temple Meads                    10    On time
## 15:44  London Paddington                       14    On time
## 15:53  London Paddington                       9     On time
## 15:55  Hereford                                10    On time
## 15:58  Exeter St Davids                        11    On time
## 16:05  Ascot                                   4     On time
## 14:18  Basingstoke                             BUS   On time
## 14:21  Heathrow Central Bus Stn                BUS   On time
## 15:00  Basingstoke                             BUS   On time
## 15:18  Basingstoke                             BUS   On time
## 15:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-10-31 14:08:11
## Time   To                                      Plat  Expected
## 13:15  London Paddington                       10A   14:08
## 13:25  London Paddington                       10    14:14
## 13:29  Plymouth                                7     14:08
## 13:55  Bristol Temple Meads                    9     14:11
## 14:00  London Paddington                       11    14:11
## 14:02  London Paddington                       10A   14:21
## 14:09  Carmarthen                              9     14:23
## 14:12  Ealing Broadway                         14A   14:15
## 14:14  Hereford                                9     14:16
## 14:15  London Paddington                       10    14:29
## 14:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 14:18  Redhill                                 5     On time
## 14:21  Ascot                                   4     On time
## 14:25  London Paddington                       11    14:34
## 14:28  Didcot Parkway                          12B   On time
## 14:29  Penzance                                7     On time
## 14:31  Ealing Broadway                         13    On time
## 14:38  Redhill                                 15    Delayed
## 14:44  Newbury                                 1     On time
## 14:46  Bournemouth                             13    14:53
## 14:51  Ascot                                   4     On time
## 14:55  Bristol Temple Meads                    9     On time
## 15:00  London Paddington                       11    15:02
## 15:01  Ealing Broadway                         14    On time
## 15:02  London Paddington                       10A   On time
## 15:03  Exeter St Davids                        -     Cancelled
## 15:09  Swansea                                 9     On time
## 15:14  Ealing Broadway                         15    On time
## 15:14  Great Malvern                           9     On time
## 15:15  London Paddington                       11    On time
## 15:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 15:18  Redhill                                 5     On time
## 15:21  Ascot                                   4     On time
## 15:25  Didcot Parkway                          12B   On time
## 15:25  London Paddington                       10    On time
## 15:27  Plymouth                                7     On time
## 15:31  Ealing Broadway                         14    On time
## 15:41  Redhill                                 6     On time
## 15:44  Bedwyn                                  3     On time
## 15:45  London Paddington                       10    On time
## 15:51  Ascot                                   4     On time
## 15:55  Bristol Temple Meads                    9     On time
## 16:00  Ealing Broadway                         14    On time
## 16:00  London Paddington                       11    On time
## 16:02  London Paddington                       10    On time
## 14:38  Basingstoke                             BUS   On time
## 15:00  Heathrow Central Bus Stn                BUS   On time
## 15:38  Basingstoke                             BUS   On time
## 15:52  Basingstoke                             BUS   On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
```
