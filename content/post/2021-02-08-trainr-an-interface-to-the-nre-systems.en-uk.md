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

## Example (Last rendered on 2022-11-08 18:04)

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
## Reading (RDG) Station Board on 2022-11-08 18:04:28
## Time   From                                    Plat  Expected
## 17:01  Penzance                                -     18:51
## 17:57  Plymouth                                10    18:01
## 18:03  Didcot Parkway                          12    On time
## 18:05  Bournemouth                             3     18:11
## 18:09  Bristol Temple Meads                    11    18:11
## 18:11  Abbey Wood                              14    On time
## 18:11  London Paddington                       9     18:13
## 18:15  London Waterloo                         6     18:19
## 18:17  Cardiff Central                         11A   On time
## 18:20  London Paddington                       9     18:30
## 18:25  Abbey Wood                              13    On time
## 18:28  Didcot Parkway                          15    On time
## 18:33  Redhill                                 4     On time
## 18:35  Newbury                                 1     On time
## 18:40  Bristol Temple Meads                    10    On time
## 18:41  Abbey Wood                              14    On time
## 18:43  Manchester Piccadilly                   8     On time
## 18:44  London Paddington                       12    On time
## 18:45  London Waterloo                         6     On time
## 18:47  Swansea                                 10    On time
## 18:50  Basingstoke                             2     On time
## 18:53  London Paddington                       12B   On time
## 18:57  Great Malvern                           10A   On time
## 18:57  London Paddington                       9     On time
## 18:57  Penzance                                11    19:41
## 18:58  Abbey Wood                              13    On time
## 19:05  Didcot Parkway                          15    On time
## 19:10  Abbey Wood                              13    On time
## 19:11  London Paddington                       9     On time
## 19:15  Abbey Wood                              14    On time
## 19:15  Newbury                                 1     On time
## 19:16  Cardiff Central                         10    On time
## 19:17  London Waterloo                         5     On time
## 19:20  London Paddington                       -     Cancelled
## 19:28  Didcot Parkway                          15    On time
## 19:29  London Paddington                       7     On time
## 19:33  Redhill                                 -     Cancelled
## 19:34  Basingstoke                             2     On time
## 19:39  Bristol Temple Meads                    10    On time
## 19:41  Abbey Wood                              13    On time
## 19:41  Manchester Piccadilly                   7     On time
## 19:45  Abbey Wood                              14    On time
## 19:46  London Waterloo                         6     On time
## 19:46  Swansea                                 10    On time
## 19:54  Plymouth                                11    On time
## 19:54  Worcester Foregate Street               10A   On time
## 19:56  London Paddington                       9     On time
## 20:01  Didcot Parkway                          13    On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-08 18:04:32
## Time   To                                      Plat  Expected
## 17:58  London Paddington                       10    18:04
## 18:07  Newbury                                 1     On time
## 18:10  London Waterloo                         4     On time
## 18:12  London Paddington                       11    On time
## 18:13  Swansea                                 9     On time
## 18:15  Manchester Piccadilly                   3     On time
##        via Coventry & Stoke-on-Trent           
## 18:17  Abbey Wood                              13    On time
## 18:20  London Paddington                       11A   On time
## 18:20  Redhill                                 5     On time
## 18:23  Didcot Parkway                          12A   On time
## 18:28  Abbey Wood                              14    On time
## 18:29  Penzance                                8     19:09
## 18:32  Basingstoke                             2     On time
## 18:39  London Waterloo                         6     On time
## 18:43  London Paddington                       10    On time
## 18:47  Abbey Wood                              13    On time
## 18:49  London Paddington                       10    On time
## 18:57  Didcot Parkway                          12B   On time
## 18:58  Abbey Wood                              14    On time
## 18:58  London Paddington                       11    19:42
## 18:59  Bristol Temple Meads                    9     On time
## 19:00  London Paddington                       10A   On time
## 19:09  London Waterloo                         6     On time
## 19:10  Newbury                                 1     On time
## 19:13  Swansea                                 9     On time
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:18  London Paddington                       10    On time
## 19:20  Redhill                                 4     On time
## 19:20  Hereford                                -     Cancelled
## 19:23  Didcot Parkway                          15    On time
## 19:25  Basingstoke                             2     On time
## 19:27  Abbey Wood                              14    On time
## 19:31  Plymouth                                7     On time
## 19:39  London Waterloo                         5     On time
## 19:41  London Paddington                       10    On time
## 19:49  London Paddington                       10    On time
## 19:50  Bournemouth                             7     On time
## 19:55  London Paddington                       11    On time
## 19:57  Abbey Wood                              13    On time
## 19:57  Didcot Parkway                          15    On time
## 19:58  London Paddington                       10A   On time
## 19:58  Weston-super-Mare                       9     On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
```
