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

## Example (Last rendered on 2022-07-24 12:04)

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
## Reading (RDG) Station Board on 2022-07-24 12:04:14
## Time   From                                    Plat  Expected
## 12:55  Penzance                                11    13:02
## 12:59  Charlbury                               13A   On time
## 12:59  London Paddington                       7B    13:01
## 13:05  Bournemouth                             8     13:07
## 13:06  London Paddington                       9     13:23
## 13:08  Redhill                                 6     On time
## 13:10  Weston-super-Mare                       10    On time
## 13:12  Didcot Parkway                          15    On time
## 13:12  London Paddington                       9     On time
## 13:13  London Paddington                       13    On time
## 13:17  Bedwyn                                  1     13:24
## 13:21  Bristol Parkway                         10    13:41
## 13:26  London Paddington                       7     On time
## 13:26  Oxford                                  10A   On time
## 13:26  Paignton                                11    On time
## 13:32  London Waterloo                         4     On time
## 13:33  Basingstoke                             2     13:36
## 13:33  London Paddington                       14    On time
## 13:38  Gatwick Airport                         5     On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:40  Bristol Temple Meads                    11A   13:42
## 13:44  Swansea                                 10    On time
## 13:45  London Paddington                       8     On time
## 13:47  Salisbury                               1     On time
## 13:53  London Paddington                       9     On time
## 13:58  Penzance                                11    On time
## 13:59  Charlbury                               10A   On time
## 14:03  London Paddington                       14    On time
## 14:05  London Waterloo                         4     On time
## 14:07  London Paddington                       9     On time
## 14:08  Redhill                                 15    On time
## 14:09  Bristol Temple Meads                    10    On time
## 14:12  Didcot Parkway                          13    On time
## 14:12  London Paddington                       9B    On time
## 14:19  London Paddington                       13    On time
## 14:19  Newbury                                 1     On time
## 14:25  Oxford                                  10A   On time
## 14:26  London Paddington                       7     On time
## 14:33  Basingstoke                             2     On time
## 14:33  London Paddington                       14    On time
## 14:33  London Waterloo                         4     On time
## 14:38  Gatwick Airport                         5     On time
## 14:39  London Paddington                       9     On time
## 14:41  Manchester Piccadilly                   13    On time
## 14:44  Carmarthen                              10    14:46
## 14:45  London Paddington                       9B    On time
## 14:49  Salisbury                               1     On time
## 14:53  London Paddington                       9     On time
## 14:57  Penzance                                11    On time
## 14:59  Charlbury                               10A   On time
## 14:59  London Paddington                       7     On time
## 15:02  London Waterloo                         4     On time
## 15:03  London Paddington                       14    On time
## 13:45  Heathrow Central Bus Stn                BUS   On time
## 14:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-07-24 12:04:18
## Time   To                                      Plat  Expected
## 12:57  London Paddington                       11    13:04
## 13:01  Paignton                                7B    13:03
## 13:02  London Paddington                       13A   On time
## 13:09  Swansea                                 9     13:26
## 13:12  London Paddington                       10    On time
## 13:12  Yeovil Pen Mill                         3     On time
## 13:14  Charlbury                               9     On time
## 13:14  Ealing Broadway                         15    On time
## 13:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 13:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 13:23  London Paddington                       10    13:42
## 13:24  Ealing Broadway                         14    On time
## 13:24  London Waterloo                         4     On time
## 13:26  Didcot Parkway                          13    On time
## 13:28  London Paddington                       11    On time
## 13:28  Plymouth                                7     On time
## 13:30  London Paddington                       10A   On time
## 13:38  Basingstoke                             2     On time
## 13:41  Redhill                                 6     On time
## 13:42  London Paddington                       11A   13:42
## 13:43  Bedwyn                                  1     On time
## 13:46  London Paddington                       10    On time
## 13:48  Oxford                                  8     On time
## 13:52  Bournemouth                             7     On time
## 13:54  Ealing Broadway                         14    On time
## 13:54  London Waterloo                         4     On time
## 13:55  Bristol Temple Meads                    9     On time
## 14:00  London Paddington                       11    On time
## 14:02  London Paddington                       10A   On time
## 14:09  Carmarthen                              9     On time
## 14:12  London Paddington                       10    On time
## 14:12  Salisbury                               1     On time
## 14:14  Charlbury                               9B    On time
## 14:14  Ealing Broadway                         13    On time
## 14:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 14:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 14:24  Ealing Broadway                         14    On time
## 14:24  London Waterloo                         4     On time
## 14:25  London Paddington                       10A   On time
## 14:27  Didcot Parkway                          13    On time
## 14:28  Penzance                                7     On time
## 14:38  Basingstoke                             2     On time
## 14:40  Bristol Parkway                         9     On time
## 14:41  Redhill                                 15    On time
## 14:43  Newbury                                 1     On time
## 14:45  London Paddington                       10    14:47
## 14:48  Oxford                                  9B    On time
## 14:54  Ealing Broadway                         14    On time
## 14:54  London Waterloo                         4     On time
## 14:54  Taunton                                 9     On time
## 14:59  London Paddington                       11    On time
## 15:01  Exeter St Davids                        7     On time
## 15:02  London Paddington                       10A   On time
## 14:00  Heathrow Central Bus Stn                BUS   On time
## 15:00  Heathrow Central Bus Stn                BUS   On time
```
