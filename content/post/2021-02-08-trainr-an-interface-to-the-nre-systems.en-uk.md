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

## Example (Last rendered on 2023-02-18 22:03)

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
## Reading (RDG) Station Board on 2023-02-18 22:03:26
## Time   From                                    Plat  Expected
## 21:49  Swansea                                 10    22:01
## 22:09  Taunton                                 10    22:19
## 22:10  London Paddington                       12    On time
## 22:13  London Waterloo                         4     On time
## 22:17  London Paddington                       -     Cancelled
## 22:19  Basingstoke                             2     On time
## 22:23  Theale                                  11    On time
## 22:25  London Paddington                       9     On time
## 22:26  Gatwick Airport                         13    On time
## 22:27  Didcot Parkway                          15    On time
## 22:29  Oxford                                  10    On time
## 22:33  Abbey Wood                              14    On time
## 22:36  Cheltenham Spa                          9A    On time
## 22:39  Manchester Piccadilly                   7     On time
## 22:40  London Paddington                       13    On time
## 22:43  London Waterloo                         5     On time
## 22:50  Basingstoke                             12    On time
## 22:51  London Paddington                       10    On time
## 22:54  London Paddington                       9     On time
## 23:03  Abbey Wood                              14    On time
## 23:04  Redhill                                 15    On time
## 23:05  Hereford                                -     Cancelled
## 23:11  London Paddington                       13    On time
## 23:11  Penzance                                15    On time
## 23:13  London Waterloo                         6     On time
## 23:14  Theale                                  12    On time
## 23:24  Basingstoke                             12    On time
## 23:26  Didcot Parkway                          14    On time
## 23:28  London Paddington                       13    On time
## 23:34  Abbey Wood                              14    On time
## 23:41  London Waterloo                         6     On time
## 23:46  London Paddington                       12    On time
## 23:52  Taunton                                 15    On time
## 23:55  Basingstoke                             14B   On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
## 23:18  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-18 22:03:31
## Time   To                                      Plat  Expected
## 21:51  London Paddington                       10    22:03
## 22:05  Basingstoke                             2     On time
## 22:09  London Waterloo                         5     On time
## 22:10  Theale                                  1     On time
## 22:15  London Paddington                       10    22:20
## 22:16  Ealing Broadway                         13    On time
## 22:19  Worcester Shrub Hill                    -     Cancelled
## 22:22  Abbey Wood                              14    On time
## 22:27  Bristol Parkway                         9     On time
## 22:30  Didcot Parkway                          12    On time
## 22:34  London Paddington                       10    On time
## 22:35  Basingstoke                             2     On time
## 22:39  London Paddington                       9A    On time
## 22:39  London Waterloo                         4     On time
## 22:52  Abbey Wood                              14    On time
## 22:52  Eastleigh                               7     On time
## 22:56  Bristol Temple Meads                    9     On time
## 23:01  Didcot Parkway                          13    On time
## 23:05  Basingstoke                             12    On time
## 23:06  London Paddington                       -     Cancelled
## 23:09  London Waterloo                         5     On time
## 23:10  Theale                                  12B   On time
## 23:13  London Paddington                       15    On time
## 23:17  Ealing Broadway                         15    On time
## 23:22  Ealing Broadway                         14    On time
## 23:34  Redhill                                 6     On time
## 23:48  Didcot Parkway                          12    On time
## 23:52  Virginia Water                          6     On time
## 23:56  London Paddington                       15    On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
```
