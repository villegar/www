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

## Example (Last rendered on 2022-05-29 10:03)

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
## Reading (RDG) Station Board on 2022-05-29 10:03:49
## Time   From                                    Plat  Expected
## 10:41  Exeter St Davids                        11    11:47
## 10:45  London Paddington                       8B    11:17
## 10:53  Bristol Parkway                         10    On time
## 10:53  London Paddington                       9     11:24
## 10:57  Worcester Foregate Street               11A   10:59
## 10:59  London Paddington                       -     Cancelled
## 11:03  London Paddington                       14    11:37
## 11:05  Bournemouth                             8     On time
## 11:05  Bristol Temple Meads                    10    On time
## 11:07  London Paddington                       9     Delayed
## 11:07  London Waterloo                         4     On time
## 11:08  Redhill                                 6     On time
## 11:10  Didcot Parkway                          15    11:12
## 11:12  London Paddington                       9     Delayed
## 11:14  Swansea                                 10    11:16
## 11:15  London Paddington                       12    11:41
## 11:19  Newbury                                 1     On time
## 11:25  Oxford                                  10    On time
## 11:26  London Paddington                       7     On time
## 11:33  Basingstoke                             2     On time
## 11:33  London Paddington                       14    Delayed
## 11:35  Plymouth                                11    On time
## 11:36  London Waterloo                         4     On time
## 11:38  Gatwick Airport                         5     On time
## 11:39  Manchester Piccadilly                   -     On time
## 11:44  Swansea                                 11    On time
## 11:45  London Paddington                       9B    On time
## 11:47  Salisbury                               1     On time
## 11:53  London Paddington                       9     On time
## 11:56  Worcester Foregate Street               10A   On time
## 11:58  Plymouth                                11    On time
## 12:03  London Paddington                       14    12:10
## 12:06  London Waterloo                         4     On time
## 12:07  London Paddington                       9     On time
## 12:08  Redhill                                 6     On time
## 12:09  Bristol Temple Meads                    10    On time
## 12:10  Didcot Parkway                          15    On time
## 12:12  London Paddington                       9     On time
## 12:19  Newbury                                 1     On time
## 12:25  Oxford                                  10A   On time
## 12:26  London Paddington                       7     On time
## 12:31  Cheltenham Spa                          -     Cancelled
## 12:33  Basingstoke                             2     On time
## 12:33  London Paddington                       14    12:39
## 12:36  London Waterloo                         4     On time
## 12:38  Gatwick Airport                         5     On time
## 12:39  Manchester Piccadilly                   12    On time
## 12:45  London Paddington                       9     On time
## 12:45  Swansea                                 10    On time
## 12:47  Salisbury                               1     On time
## 12:53  London Paddington                       9     On time
## 12:55  Penzance                                11    On time
## 12:56  Worcester Foregate Street               10A   On time
## 12:59  London Paddington                       7     On time
## 11:45  Heathrow Central Bus Stn                BUS   On time
## 12:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-05-29 10:03:53
## Time   To                                      Plat  Expected
## 10:48  Oxford                                  8B    11:18
## 10:55  Weston-super-Mare                       9     11:25
## 10:59  London Paddington                       11A   11:03
## 11:01  Paignton                                -     Cancelled
## 11:09  Swansea                                 9     11:26
## 11:11  London Paddington                       10    On time
## 11:12  Salisbury                               1     On time
## 11:14  Ealing Broadway                         15    On time
## 11:14  Worcester Foregate Street               9     Delayed
## 11:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 11:16  London Paddington                       10    11:16
## 11:21  Gatwick Airport                         5     11:41
##        via Guildford                           
## 11:24  Ealing Broadway                         14    11:40
## 11:24  London Waterloo                         4     On time
## 11:25  London Paddington                       10    On time
## 11:26  Didcot Parkway                          12    11:42
## 11:28  Exeter St Davids                        7     On time
## 11:35  London Paddington                       11    On time
## 11:38  Basingstoke                             2     On time
## 11:41  Redhill                                 6     On time
## 11:43  Bedwyn                                  1     On time
## 11:45  London Paddington                       11    On time
## 11:48  Oxford                                  9B    On time
## 11:52  Bournemouth                             -     On time
## 11:54  Bristol Temple Meads                    9     On time
## 11:54  Ealing Broadway                         14    On time
## 11:54  London Waterloo                         4     On time
## 11:59  London Paddington                       11    On time
## 12:02  London Paddington                       10A   On time
## 12:09  Carmarthen                              9     On time
## 12:11  London Paddington                       10    On time
## 12:12  Salisbury                               1     On time
## 12:14  Ealing Broadway                         15    On time
## 12:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 12:18  Worcester Shrub Hill                    9     On time
## 12:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 12:24  Ealing Broadway                         14    On time
## 12:24  London Waterloo                         4     On time
## 12:25  London Paddington                       10A   On time
## 12:26  Didcot Parkway                          12    On time
## 12:28  Penzance                                7     On time
## 12:33  London Paddington                       -     Cancelled
## 12:38  Basingstoke                             2     On time
## 12:41  Redhill                                 6     On time
## 12:43  Newbury                                 1     On time
## 12:46  London Paddington                       10    On time
## 12:48  Oxford                                  9     On time
## 12:54  Ealing Broadway                         14    On time
## 12:54  London Waterloo                         4     On time
## 12:55  Weston-super-Mare                       9     On time
## 12:57  London Paddington                       11    On time
## 13:00  London Paddington                       10A   On time
## 13:01  Paignton                                7     On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
```
