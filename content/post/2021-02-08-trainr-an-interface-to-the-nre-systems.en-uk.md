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

## Example (Last rendered on 2021-11-21 14:03)

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
## Reading (RDG) Station Board on 2021-11-21 14:03:49
## Time   From                                    Plat  Expected
## 13:54  Great Malvern                           10A   13:58
## 13:58  Penzance                                11    14:09
## 13:59  London Paddington                       8     14:19
## 14:08  Clapham Junction                        -     Cancelled
## 14:09  Ash                                     6     On time
## 14:09  Bristol Temple Meads                    11A   14:16
## 14:10  Didcot Parkway                          14    On time
## 14:12  London Paddington                       9     Delayed
## 14:13  London Paddington                       13    14:57
## 14:19  Newbury                                 1     On time
## 14:24  Slough                                  12    On time
## 14:27  London Paddington                       7     14:31
## 14:33  Basingstoke                             2     On time
## 14:35  Clapham Junction                        4     On time
## 14:41  Manchester Piccadilly                   13    On time
## 14:43  Swansea                                 11    14:46
## 14:44  London Paddington                       14    15:00
## 14:49  Salisbury                               1     On time
## 14:54  London Paddington                       8     On time
## 14:57  London Paddington                       7     On time
## 14:57  Penzance                                11    On time
## 14:58  Hereford                                10    On time
## 14:59  London Paddington                       9     On time
## 15:05  Clapham Junction                        4     On time
## 15:07  Eastleigh                               8     On time
## 15:09  Ash                                     6     On time
## 15:09  Weston-super-Mare                       11    On time
## 15:12  London Paddington                       9     On time
## 15:13  Didcot Parkway                          15    On time
## 15:13  London Paddington                       14    On time
## 15:19  Bedwyn                                  3     On time
## 15:23  Slough                                  12    On time
## 15:27  London Paddington                       7     On time
## 15:33  Basingstoke                             2     On time
## 15:35  Clapham Junction                        4     On time
## 15:39  Manchester Piccadilly                   7     On time
## 15:40  Bristol Temple Meads                    10    On time
## 15:43  Swansea                                 11    On time
## 15:44  London Paddington                       14    On time
## 15:47  Salisbury                               1     On time
## 15:54  London Paddington                       9     On time
## 14:21  Heathrow Central Bus Stn                BUS   On time
## 15:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-11-21 14:03:52
## Time   To                                      Plat  Expected
## 14:05  London Paddington                       11    14:10
## 14:06  Ealing Broadway                         14    On time
## 14:07  London Paddington                       10A   On time
## 14:09  Carmarthen                              8     14:30
## 14:12  Salisbury                               1     On time
## 14:14  Hereford                                9     Delayed
## 14:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 14:19  London Paddington                       11A   On time
## 14:21  Clapham Junction                        -     Cancelled
## 14:25  Slough                                  14    On time
## 14:28  Didcot Parkway                          12    On time
## 14:30  Penzance                                7     14:32
## 14:36  Ealing Broadway                         13    15:00
## 14:38  Basingstoke                             2     On time
## 14:41  Ash                                     6     On time
## 14:44  Newbury                                 1     On time
## 14:49  London Paddington                       11    On time
## 14:51  Clapham Junction                        4     On time
## 14:55  Bristol Temple Meads                    8     On time
## 15:03  Exeter St Davids                        7     On time
## 15:05  London Paddington                       11    On time
## 15:06  Ealing Broadway                         14    On time
## 15:07  London Paddington                       10    On time
## 15:09  Swansea                                 9     On time
## 15:12  Gillingham (Dorset)                     1     On time
## 15:14  Great Malvern                           9     On time
## 15:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 15:19  London Paddington                       11    On time
## 15:21  Clapham Junction                        4     On time
## 15:25  Didcot Parkway                          12    On time
## 15:25  Slough                                  15    On time
## 15:29  Plymouth                                7     On time
## 15:36  Ealing Broadway                         14    On time
## 15:38  Basingstoke                             2     On time
## 15:41  Ash                                     6     On time
## 15:44  Bedwyn                                  3     On time
## 15:45  London Paddington                       10    On time
## 15:49  London Paddington                       11    On time
## 15:51  Clapham Junction                        4     On time
## 15:52  Eastleigh                               7     On time
## 15:55  Taunton                                 9     On time
## 15:00  Heathrow Central Bus Stn                BUS   On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
```
