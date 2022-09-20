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

## Example (Last rendered on 2022-09-20 08:04)

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
## Reading (RDG) Station Board on 2022-09-20 08:04:47
## Time   From                                    Plat  Expected
## 08:53  Plymouth                                7     08:59
## 08:56  West Drayton                            13    09:07
## 08:59  Bristol Temple Meads                    -     09:04
## 09:01  Didcot Parkway                          15    On time
## 09:02  Basingstoke                             1     On time
## 09:03  Taunton                                 10    09:42
## 09:04  Redhill                                 5     On time
## 09:05  Bournemouth                             8     09:12
## 09:09  Newbury                                 -     Cancelled
## 09:11  Hereford                                -     09:15
## 09:13  London Paddington                       -     Cancelled
## 09:16  London Waterloo                         4     On time
## 09:17  Slough                                  12    On time
## 09:19  Swansea                                 10    On time
## 09:24  Oxford                                  -     Cancelled
## 09:25  Gatwick Airport                         5     09:28
## 09:26  West Drayton                            13    On time
## 09:30  Penzance                                11    09:33
## 09:32  Worcester Shrub Hill                    10    On time
## 09:34  London Paddington                       -     Cancelled
## 09:37  Didcot Parkway                          15    On time
## 09:38  London Paddington                       -     Cancelled
## 09:39  Taunton                                 10    09:44
## 09:40  Nottingham                              7     On time
## 09:41  London Waterloo                         6     On time
## 09:41  Newbury                                 -     Cancelled
## 09:45  Slough                                  12    On time
## 09:45  Swansea                                 10    On time
## 09:46  Basingstoke                             2     On time
## 09:46  London Paddington                       -     Cancelled
## 09:53  Banbury                                 13    On time
## 09:55  Newbury                                 1     On time
## 09:55  Worcester Shrub Hill                    10    On time
## 10:01  Guildford                               4     On time
## 10:02  Plymouth                                11    On time
## 10:06  Swansea                                 10    On time
## 10:07  West Drayton                            14    On time
## 10:08  Didcot Parkway                          15    On time
## 10:11  London Waterloo                         5     On time
## 10:11  Newbury                                 11    On time
## 10:14  Bristol Temple Meads                    10    On time
## 10:14  Swansea                                 -     On time
## 10:16  Slough                                  12    On time
## 10:18  Gatwick Airport                         6     On time
## 10:19  Basingstoke                             2     On time
## 10:23  Oxford                                  -     Cancelled
## 10:28  Cheltenham Spa                          -     Cancelled
## 10:34  Swansea                                 -     On time
## 10:36  Didcot Parkway                          15    On time
## 10:39  London Paddington                       14    On time
## 10:40  Bristol Temple Meads                    10    On time
## 10:41  London Waterloo                         6     On time
## 10:43  Newbury                                 1     On time
## 10:44  Manchester Piccadilly                   7     On time
## 10:45  Carmarthen                              11    On time
## 10:45  Redhill                                 4     On time
## 10:46  London Paddington                       -     Cancelled
## 10:46  Slough                                  13    On time
## 10:53  Gatwick Airport                         5     10:56
## 10:54  Great Malvern                           -     Cancelled
## 10:56  Basingstoke                             2     On time
## 10:58  Penzance                                11    On time
## 09:06  Heathrow Central Bus Stn                BUS   On time
## 09:41  Heathrow Central Bus Stn                BUS   On time
## 10:16  Heathrow Central Bus Stn                BUS   On time
## 10:51  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-09-20 08:04:52
## Time   To                                      Plat  Expected
## 08:57  Bristol Temple Meads                    8     Delayed
## 09:01  Gatwick Airport                         5     09:06
##        via Guildford                           
## 09:07  Slough                                  15    On time
## 09:08  West Drayton                            14    Delayed
## 09:12  London Waterloo                         6     On time
## 09:13  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:13  Newbury                                 3     On time
## 09:13  Swansea                                 9     On time
## 09:18  Great Malvern                           9     On time
## 09:20  Redhill                                 5     On time
## 09:23  Didcot Parkway                          12    On time
## 09:27  Bristol Temple Meads                    9     On time
## 09:27  Ealing Broadway                         -     Cancelled
## 09:29  Plymouth                                13    On time
## 09:32  Basingstoke                             1     On time
## 09:36  Newbury                                 -     Cancelled
## 09:37  West Drayton                            -     On time
## 09:38  Ealing Broadway                         15    On time
## 09:42  London Waterloo                         4     On time
## 09:43  Cardiff Central                         9     On time
## 09:47  Reading                                 10    On time
## 09:48  Oxford                                  -     Cancelled
## 09:54  Cheltenham Spa                          -     Cancelled
## 09:55  Didcot Parkway                          12    On time
## 09:57  Ealing Broadway                         14    On time
## 09:57  London Paddington                       10    On time
## 09:58  Bristol Temple Meads                    9     On time
## 10:02  Paignton                                8     On time
## 10:04  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:07  Basingstoke                             2     On time
## 10:08  Reading                                 10    On time
## 10:09  Ealing Broadway                         15    On time
## 10:12  London Waterloo                         6     On time
## 10:12  Newbury                                 1     On time
## 10:13  Swansea                                 9     On time
## 10:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 10:19  Hereford                                9     On time
## 10:20  Redhill                                 4     On time
## 10:23  Didcot Parkway                          12    On time
## 10:26  London Paddington                       -     Cancelled
## 10:27  Bristol Temple Meads                    9     On time
## 10:27  Ealing Broadway                         14    On time
## 10:29  Penzance                                7     On time
## 10:32  Basingstoke                             2     On time
## 10:34  London Paddington                       -     Cancelled
## 10:37  Ealing Broadway                         15    On time
## 10:39  Newbury                                 8     On time
## 10:42  London Waterloo                         5     On time
## 10:43  Cardiff Central                         9     On time
## 10:48  London Paddington                       11    On time
## 10:48  Oxford                                  -     Cancelled
## 10:52  Bournemouth                             7     On time
## 10:53  Cheltenham Spa                          -     Cancelled
## 10:53  Didcot Parkway                          13    On time
## 10:57  Ealing Broadway                         14    On time
## 10:57  London Paddington                       -     Cancelled
## 10:58  Bristol Temple Meads                    8     On time
## 11:01  Exeter St Davids                        7     On time
## 11:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 09:30  Heathrow Central Bus Stn                BUS   On time
## 10:05  Heathrow Central Bus Stn                BUS   On time
## 10:40  Heathrow Central Bus Stn                BUS   On time
```
