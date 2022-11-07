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

## Example (Last rendered on 2022-11-07 22:04)

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
## Reading (RDG) Station Board on 2022-11-07 22:04:40
## Time   From                                    Plat  Expected
## 21:56  Great Malvern                           10A   22:02
## 22:05  Exeter St Davids                        11    On time
## 22:07  London Paddington                       14    On time
## 22:08  Didcot Parkway                          14    22:01
## 22:10  Bristol Temple Meads                    10    On time
## 22:12  Abbey Wood                              14    On time
## 22:13  London Paddington                       9     On time
## 22:18  London Paddington                       -     22:38
## 22:18  London Paddington                       12    On time
## 22:27  London Paddington                       9     On time
## 22:34  Shalford                                14    On time
## 22:42  Abbey Wood                              14    On time
## 22:46  London Paddington                       12    On time
## 22:46  Swansea                                 10    22:49
## 23:00  Worcester Foregate Street               -     Cancelled
## 23:03  Basingstoke                             2     On time
## 23:09  Abbey Wood                              13    On time
## 23:13  Exeter St Davids                        10    On time
## 23:16  Gatwick Airport                         14    23:19
## 23:18  London Paddington                       -     On time
## 23:20  Didcot Parkway                          15    On time
## 23:27  Basingstoke                             2     On time
## 23:36  Oxford                                  15    On time
## 23:39  Abbey Wood                              14    On time
## 00:02  Redhill                                 14    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-07 22:04:44
## Time   To                                      Plat  Expected
## 21:56  London Paddington                       10A   22:04
## 22:05  Basingstoke                             3     On time
## 22:05  London Paddington                       11    On time
## 22:08  London Paddington                       14    On time
## 22:10  London Paddington                       10    On time
## 22:13  Swansea                                 9     On time
## 22:18  Didcot Parkway                          12    On time
## 22:18  Worcester Shrub Hill                    -     22:38
## 22:27  Abbey Wood                              14    On time
## 22:27  Bristol Temple Meads                    9     On time
## 22:29  Basingstoke                             2     On time
## 22:46  Didcot Parkway                          12    On time
## 22:46  London Paddington                       10    22:49
## 22:57  Abbey Wood                              14    On time
## 23:00  London Paddington                       -     Cancelled
## 23:13  London Paddington                       10    On time
## 23:16  Ealing Broadway                         13    On time
## 23:18  Swansea                                 -     On time
## 23:20  London Paddington                       15    On time
## 23:34  Basingstoke                             2     On time
## 23:38  London Paddington                       15    On time
```
