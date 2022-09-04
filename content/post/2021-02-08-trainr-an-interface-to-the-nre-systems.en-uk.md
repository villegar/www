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

## Example (Last rendered on 2022-09-04 18:04)

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
## Reading (RDG) Station Board on 2022-09-04 18:04:06
## Time   From                                    Plat  Expected
## 18:33  Cheltenham Spa                          10A   On time
## 18:40  Bristol Temple Meads                    9     On time
## 18:45  Swansea                                 7     On time
## 18:53  London Paddington                       9     Delayed
## 18:56  Great Malvern                           10A   19:04
## 18:58  Penzance                                11    19:14
## 18:59  London Paddington                       7B    Delayed
## 19:01  London Paddington                       9     Delayed
## 19:05  Bournemouth                             8     19:08
## 19:09  London Paddington                       -     Cancelled
## 19:09  Taunton                                 10    19:15
## 19:12  London Paddington                       9     Delayed
## 19:13  Didcot Parkway                          15    Delayed
## 19:13  Slough                                  12    19:19
## 19:18  Ash                                     5     On time
## 19:19  Bedwyn                                  1     On time
## 19:23  London Paddington                       9     Delayed
## 19:25  Oxford                                  10    Delayed
## 19:26  London Paddington                       8     On time
## 19:32  Ascot                                   6     On time
## 19:34  Basingstoke                             2     19:40
## 19:39  London Paddington                       -     Cancelled
## 19:39  Manchester Piccadilly                   7B    On time
## 19:40  Paignton                                -     Cancelled
## 19:42  London Paddington                       9     On time
## 19:48  Carmarthen                              10    On time
## 19:53  London Paddington                       9     On time
## 19:56  Hereford                                10    On time
## 19:57  Penzance                                11    19:59
## 20:01  London Paddington                       8     On time
## 20:02  Ascot                                   4     On time
## 20:09  West Drayton                            14    On time
## 20:12  Exeter St Davids                        10    On time
## 20:12  London Paddington                       9     On time
## 20:13  Didcot Parkway                          15    On time
## 20:14  London Paddington                       13    On time
## 20:18  Ash                                     5     On time
## 20:20  Newbury                                 1     On time
## 20:25  Oxford                                  10    On time
## 20:27  London Paddington                       7     On time
## 20:32  Ascot                                   6     On time
## 20:33  Basingstoke                             2     On time
## 20:39  Manchester Piccadilly                   8     On time
## 20:40  London Paddington                       -     Cancelled
## 20:42  London Paddington                       7     On time
## 20:42  Plymouth                                11    On time
## 20:48  Swansea                                 10    On time
## 20:53  London Paddington                       9     On time
## 20:57  Great Malvern                           10    On time
## 20:58  Penzance                                11    On time
## 21:02  Ascot                                   4     On time
## 19:38  Heathrow Central Bus Stn                BUS   On time
## 20:30  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-09-04 18:04:10
## Time   To                                      Plat  Expected
## 18:43  London Paddington                       10A   Delayed
## 18:45  London Paddington                       9     Delayed
## 18:48  London Paddington                       7     Delayed
## 18:55  Weston-super-Mare                       9     Delayed
## 19:00  London Paddington                       11    19:15
## 19:01  Plymouth                                7B    Delayed
## 19:02  London Paddington                       10A   19:05
## 19:09  Swansea                                 9     Delayed
## 19:14  Hereford                                9     Delayed
## 19:14  London Paddington                       15    Delayed
## 19:15  London Paddington                       10    19:16
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:24  Ascot                                   4     On time
## 19:25  Bristol Temple Meads                    9     Delayed
## 19:25  Didcot Parkway                          12    On time
## 19:27  London Paddington                       10    Delayed
## 19:28  Plymouth                                8     On time
## 19:31  Ealing Broadway                         14    On time
## 19:38  Basingstoke                             2     On time
## 19:41  Ash                                     5     On time
## 19:43  Bedwyn                                  1     On time
## 19:43  London Paddington                       -     Cancelled
## 19:49  London Paddington                       10    On time
## 19:49  Oxford                                  9     On time
## 19:52  Bournemouth                             7B    On time
## 19:54  Ascot                                   6     On time
## 19:55  Bristol Temple Meads                    9     On time
## 20:00  London Paddington                       11    On time
## 20:01  Ealing Broadway                         14    On time
## 20:02  London Paddington                       10    On time
## 20:09  Swansea                                 8     On time
## 20:14  Great Malvern                           9     On time
## 20:14  London Paddington                       15    On time
## 20:15  London Paddington                       10    On time
## 20:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 20:25  Didcot Parkway                          13    On time
## 20:27  London Paddington                       10    On time
## 20:28  Plymouth                                7     On time
## 20:31  Ealing Broadway                         14    On time
## 20:38  Basingstoke                             2     On time
## 20:41  Ash                                     5     On time
## 20:43  Newbury                                 1     On time
## 20:44  London Paddington                       11    On time
## 20:49  London Paddington                       10    On time
## 20:49  Oxford                                  7     On time
## 20:52  Bournemouth                             8     On time
## 20:54  Ascot                                   6     On time
## 20:55  Weston-super-Mare                       9     On time
## 21:00  London Paddington                       11    On time
## 21:01  Ealing Broadway                         14    On time
## 21:02  London Paddington                       10    On time
## 20:00  Heathrow Central Bus Stn                BUS   On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
```
