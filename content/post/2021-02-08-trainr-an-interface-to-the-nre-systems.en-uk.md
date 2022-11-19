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

## Example (Last rendered on 2022-11-19 18:03)

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
## Reading (RDG) Station Board on 2022-11-19 18:04:00
## Time   From                                    Plat  Expected
## 17:36  London Paddington                       9     18:01
## 17:47  London Paddington                       8B    18:14
## 17:51  Swansea                                 10    18:02
## 17:54  Hereford                                10    18:08
## 17:55  London Paddington                       8     18:13
## 18:01  Plymouth                                11    On time
## 18:03  Didcot Parkway                          14    On time
## 18:03  London Paddington                       14    18:08
## 18:10  Bristol Temple Meads                    10    18:14
## 18:16  London Waterloo                         5     On time
## 18:22  Bristol Parkway                         15    On time
## 18:26  London Paddington                       9     On time
## 18:30  Redhill                                 4     On time
## 18:34  Basingstoke                             13    On time
## 18:41  Manchester Piccadilly                   -     Cancelled
## 19:06  Bournemouth                             -     Cancelled
## 19:07  Swansea                                 -     19:25
## 19:40  Manchester Piccadilly                   -     Cancelled
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:40  Banbury                                 BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-19 18:04:04
## Time   To                                      Plat  Expected
## 17:38  Bristol Parkway                         9     18:04
## 17:50  Oxford                                  8B    Delayed
## 17:52  London Paddington                       10    18:04
## 17:56  London Paddington                       10    18:09
## 17:58  Didcot Parkway                          15A   Delayed
## 17:59  Swindon                                 8     18:15
## 18:05  London Paddington                       11    On time
## 18:09  London Waterloo                         6     On time
## 18:12  London Paddington                       10    18:16
## 18:15  Manchester Piccadilly                   -     Cancelled
##        via Coventry & Stoke-on-Trent           
## 18:24  Redhill                                 14    On time
## 18:52  Bournemouth                             -     Cancelled
## 19:15  Manchester Piccadilly                   -     Cancelled
##        via Coventry & Stoke-on-Trent           
## 18:15  Banbury                                 BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:15  Banbury                                 BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
```
