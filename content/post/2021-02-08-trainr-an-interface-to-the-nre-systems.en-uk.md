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

## Example (Last rendered on 2022-11-08 10:06)

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
## Reading (RDG) Station Board on 2022-11-08 10:07:01
## Time   From                                    Plat  Expected
## 10:06  Swansea                                 10    10:15
## 10:07  Abbey Wood                              14    On time
## 10:08  Didcot Parkway                          12    On time
## 10:11  London Paddington                       9     On time
## 10:14  Staines                                 5     10:54
## 10:18  London Paddington                       9B    10:29
## 10:27  London Paddington                       7     On time
## 10:36  Didcot Parkway                          13    On time
## 10:39  Abbey Wood                              14    On time
## 10:40  Bristol Temple Meads                    10    On time
## 10:41  London Paddington                       9     On time
## 10:43  London Waterloo                         6     10:55
## 10:43  Newbury                                 1     On time
## 10:44  Birmingham New Street                   7     On time
## 10:45  Redhill                                 5     10:49
## 10:45  Swansea                                 11    On time
## 10:54  Great Malvern                           10    On time
## 10:55  London Paddington                       8B    On time
## 10:56  Basingstoke                             2     On time
## 10:58  Didcot Parkway                          13    On time
## 10:58  Plymouth                                11    11:00
## 11:05  Bournemouth                             8     On time
## 11:11  London Paddington                       9     On time
## 11:12  Abbey Wood                              14    On time
## 11:14  London Waterloo                         4     On time
## 11:16  London Paddington                       9B    On time
## 11:18  Bristol Parkway                         10A   On time
## 11:27  London Paddington                       8     On time
## 11:32  Didcot Parkway                          13    On time
## 11:33  Redhill                                 5     On time
## 11:36  Newbury                                 3     On time
## 11:38  Plymouth                                11    On time
## 11:40  Abbey Wood                              14    On time
## 11:40  Bristol Temple Meads                    10    On time
## 11:41  London Paddington                       9B    On time
## 11:41  Manchester Piccadilly                   8     On time
## 11:44  London Waterloo                         6     On time
## 11:45  Swansea                                 11    On time
## 11:50  Basingstoke                             2     On time
## 11:55  London Paddington                       9     On time
## 11:59  Didcot Parkway                          15    On time
## 12:01  Plymouth                                11    On time
## 10:34  Heathrow Central Bus Stn                BUS   On time
## 11:04  Heathrow Central Bus Stn                BUS   On time
## 11:34  Heathrow Central Bus Stn                BUS   On time
## 12:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-08 10:07:07
## Time   To                                      Plat  Expected
## 10:08  London Paddington                       10    10:16
## 10:09  London Waterloo                         6     On time
## 10:12  Newbury                                 1     On time
## 10:13  Swansea                                 9     On time
## 10:15  Manchester Piccadilly                   7B    Delayed
##        via Coventry & Stoke-on-Trent           
## 10:19  Hereford                                9B    10:30
## 10:20  Redhill                                 15    On time
## 10:23  Didcot Parkway                          12B   On time
## 10:27  Abbey Wood                              14    On time
## 10:29  Penzance                                7     On time
## 10:32  Basingstoke                             2     On time
## 10:39  London Waterloo                         5     10:57
## 10:42  London Paddington                       10    On time
## 10:43  Cardiff Central                         9     On time
## 10:48  London Paddington                       11    On time
## 10:52  Bournemouth                             7     On time
## 10:53  Didcot Parkway                          13    On time
## 10:57  Abbey Wood                              14    On time
## 10:57  London Paddington                       10    On time
## 10:58  Bristol Temple Meads                    8B    On time
## 11:04  London Paddington                       11    On time
## 11:09  London Waterloo                         6     On time
## 11:11  Newbury                                 2     On time
## 11:13  Swansea                                 9     On time
## 11:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 11:19  Worcester Shrub Hill                    9B    On time
## 11:20  London Paddington                       10A   On time
## 11:20  Redhill                                 5     On time
## 11:26  Didcot Parkway                          13    On time
## 11:27  Abbey Wood                              14    On time
## 11:29  Plymouth                                8     On time
## 11:32  Basingstoke                             2     On time
## 11:39  London Waterloo                         4     On time
## 11:40  London Paddington                       11    On time
## 11:42  London Paddington                       10    On time
## 11:43  Cardiff Central                         9B    On time
## 11:48  London Paddington                       11    On time
## 11:53  Didcot Parkway                          13    On time
## 11:57  Abbey Wood                              14    On time
## 11:57  Bristol Temple Meads                    9     On time
## 12:04  London Paddington                       11    On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
```
