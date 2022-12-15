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

## Example (Last rendered on 2022-12-15 12:10)

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
## Reading (RDG) Station Board on 2022-12-15 12:10:09
## Time   From                                    Plat  Expected
## 11:18  Cardiff Central                         10    Delayed
## 11:45  Swansea                                 11    12:45
## 12:01  Plymouth                                11    12:20
## 12:10  London Paddington                       14    On time
## 12:11  London Paddington                       9B    On time
## 12:11  London Waterloo                         4     12:25
## 12:14  Cardiff Central                         11    Delayed
## 12:16  London Paddington                       9     Delayed
## 12:27  London Paddington                       7     Delayed
## 12:33  Didcot Parkway                          13    On time
## 12:33  Redhill                                 5     On time
## 12:40  Bristol Temple Meads                    10    12:52
## 12:40  London Paddington                       14    12:56
## 12:41  London Paddington                       -     Cancelled
## 12:41  Manchester Piccadilly                   7     On time
## 12:42  London Waterloo                         6     12:48
## 12:42  Newbury                                 1     On time
## 12:45  Swansea                                 10    13:04
## 12:49  Basingstoke                             2     On time
## 12:54  Great Malvern                           10A   13:14
## 12:54  London Paddington                       9     On time
## 13:00  Penzance                                11    13:10
## 13:03  Didcot Parkway                          15    On time
## 13:05  Bournemouth                             8B    On time
## 13:11  London Waterloo                         4     On time
## 13:12  Abbey Wood                              14    On time
## 13:14  Cardiff Central                         -     Cancelled
## 13:16  London Paddington                       9     On time
## 13:27  London Paddington                       8     On time
## 13:31  Didcot Parkway                          13    On time
## 13:33  Redhill                                 5     On time
## 13:39  Bristol Temple Meads                    10    On time
## 13:40  Birmingham New Street                   8     On time
## 13:41  London Paddington                       -     Cancelled
## 13:42  Abbey Wood                              14    On time
## 13:42  London Waterloo                         6     On time
## 13:43  Newbury                                 1     On time
## 13:45  Swansea                                 10    Delayed
## 13:55  Basingstoke                             2     On time
## 13:55  Great Malvern                           10A   On time
## 13:56  London Paddington                       9     On time
## 14:02  Penzance                                11    On time
## 14:03  Didcot Parkway                          13    On time
## 14:09  Abbey Wood                              14    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-15 12:10:13
## Time   To                                      Plat  Expected
## 11:20  London Paddington                       10    Delayed
## 11:48  London Paddington                       11    12:46
## 12:04  London Paddington                       11    12:22
## 12:12  London Waterloo                         6     On time
## 12:12  Newbury                                 2     On time
## 12:13  Swansea                                 9B    On time
## 12:16  London Paddington                       11    Delayed
## 12:16  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 12:18  Hereford                                9     Delayed
## 12:20  Redhill                                 5     On time
## 12:23  Didcot Parkway                          13    On time
## 12:27  Abbey Wood                              14    On time
## 12:29  Penzance                                7     Delayed
## 12:32  Basingstoke                             2     On time
## 12:42  London Paddington                       10    12:53
## 12:42  London Waterloo                         4     On time
## 12:43  Cardiff Central                         -     Cancelled
## 12:47  London Paddington                       10    13:05
## 12:52  Bournemouth                             7     On time
## 12:53  Didcot Parkway                          13    On time
## 12:57  Abbey Wood                              14    12:59
## 12:57  Bristol Temple Meads                    9     On time
## 12:57  London Paddington                       10A   13:15
## 13:04  London Paddington                       11    13:11
## 13:12  London Waterloo                         6     On time
## 13:12  Newbury                                 1     On time
## 13:13  Swansea                                 9     On time
## 13:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 13:17  London Paddington                       -     Cancelled
## 13:18  Worcester Foregate Street               9     On time
## 13:20  Redhill                                 5     On time
## 13:23  Didcot Parkway                          15    On time
## 13:27  Abbey Wood                              14    On time
## 13:29  Plymouth                                8     On time
## 13:32  Basingstoke                             2     On time
## 13:41  London Paddington                       10    On time
## 13:42  London Waterloo                         4     On time
## 13:43  Cardiff Central                         -     Cancelled
## 13:48  London Paddington                       10    Delayed
## 13:55  Didcot Parkway                          13    On time
## 13:57  Abbey Wood                              14    On time
## 13:58  Bristol Temple Meads                    9     On time
## 13:58  London Paddington                       10A   On time
## 14:04  London Paddington                       11    On time
```
