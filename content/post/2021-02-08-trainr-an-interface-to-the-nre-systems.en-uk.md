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

## Example (Last rendered on 2022-09-04 20:04)

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
## Reading (RDG) Station Board on 2022-09-04 20:04:48
## Time   From                                    Plat  Expected
## 19:26  London Paddington                       8     21:03
## 19:53  London Paddington                       9B    Delayed
## 20:27  London Paddington                       7     21:26
## 20:42  London Paddington                       7B    21:16
## 20:48  Swansea                                 10    21:15
## 20:53  London Paddington                       9     Delayed
## 20:57  Great Malvern                           10A   21:16
## 20:58  Penzance                                11    21:20
## 21:01  London Paddington                       9     Delayed
## 21:05  Bournemouth                             12    21:07
## 21:08  West Drayton                            14    On time
## 21:11  Taunton                                 10    On time
## 21:13  Didcot Parkway                          13    On time
## 21:18  Ash                                     -     Cancelled
## 21:19  Bedwyn                                  1     On time
## 21:26  London Paddington                       7     On time
## 21:32  Ascot                                   6     On time
## 21:33  Basingstoke                             2     21:47
## 21:39  London Paddington                       -     Cancelled
## 21:39  Manchester Piccadilly                   8     On time
## 21:46  London Paddington                       9     On time
## 21:48  Swansea                                 10    On time
## 21:53  London Paddington                       9     On time
## 21:55  Great Malvern                           10    On time
## 22:02  Ascot                                   6     On time
## 22:05  Newquay                                 11    On time
## 22:06  London Paddington                       9     On time
## 22:08  London Paddington                       14    On time
## 22:09  Weston-super-Mare                       -     Cancelled
## 22:12  London Paddington                       9     On time
## 22:13  Didcot Parkway                          13    On time
## 22:14  London Paddington                       12    On time
## 22:18  Ash                                     5     On time
## 22:23  London Paddington                       9     On time
## 22:24  Newbury                                 1     On time
## 22:33  Basingstoke                             13    On time
## 22:39  Manchester Piccadilly                   8     On time
## 22:40  London Paddington                       14    On time
## 22:49  Carmarthen                              10    On time
## 22:50  Penzance                                13    On time
## 22:54  Great Malvern                           10    On time
## 23:02  Ascot                                   6     On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
## 22:15  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-09-04 20:04:52
## Time   To                                      Plat  Expected
## 19:28  Plymouth                                8     21:04
## 19:55  Bristol Temple Meads                    9B    Delayed
## 20:28  Plymouth                                7     21:27
## 20:49  London Paddington                       10    21:16
## 20:49  Oxford                                  7B    21:17
## 20:55  Weston-super-Mare                       9     Delayed
## 21:00  London Paddington                       11    21:21
## 21:01  Ealing Broadway                         -     Cancelled
## 21:02  London Paddington                       10A   21:17
## 21:09  Swansea                                 9     Delayed
## 21:12  Birmingham New Street                   12    On time
##        via Coventry                            
## 21:14  Didcot Parkway                          12    On time
## 21:14  Ealing Broadway                         13    On time
## 21:15  London Paddington                       10    On time
## 21:15  Worcester Shrub Hill                    9     On time
## 21:24  Ealing Broadway                         14    On time
## 21:28  Exeter St Davids                        7     On time
## 21:38  Basingstoke                             3     On time
## 21:41  Ash                                     5     On time
## 21:43  Bedwyn                                  1     On time
## 21:48  Oxford                                  9     On time
## 21:50  London Paddington                       10    On time
## 21:52  Southampton Central                     8     On time
## 21:54  Ascot                                   6     On time
## 21:54  Ealing Broadway                         -     Cancelled
## 21:55  Bristol Temple Meads                    9     On time
## 21:57  London Paddington                       10    On time
## 22:09  Swansea                                 9     On time
## 22:10  London Paddington                       -     Cancelled
## 22:12  London Paddington                       11    On time
## 22:13  Worcester Shrub Hill                    9     On time
## 22:15  Didcot Parkway                          12    On time
## 22:24  Bristol Temple Meads                    9     On time
## 22:28  Ealing Broadway                         14    On time
## 22:41  Ash                                     5     On time
## 22:43  Newbury                                 1     On time
## 22:50  London Paddington                       10    On time
## 22:53  London Paddington                       13    On time
## 22:54  Ascot                                   6     On time
## 22:55  London Paddington                       10    On time
## 22:58  Ealing Broadway                         14    On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
