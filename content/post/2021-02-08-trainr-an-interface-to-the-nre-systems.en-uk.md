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

## Example (Last rendered on 2023-02-28 10:03)

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
## Reading (RDG) Station Board on 2023-02-28 10:03:42
## Time   From                                    Plat  Expected
## 08:16  London Paddington                       12    10:06
## 08:18  Swansea                                 10    10:07
## 08:26  Cheltenham Spa                          10    10:14
## 08:39  Weston-super-Mare                       11    10:25
## 08:50  Swansea                                 -     10:33
## 09:00  Plymouth                                10    10:33
## 09:16  London Paddington                       9B    10:07
## 09:21  London Paddington                       8     10:13
## 09:32  Worcester Shrub Hill                    10A   10:30
## 09:34  London Paddington                       7     Delayed
## 09:37  Didcot Parkway                          15    Delayed
## 09:39  Plymouth                                10    10:43
## 09:41  London Paddington                       9     Delayed
## 09:46  London Paddington                       9A    Delayed
## 09:52  London Paddington                       8B    10:10
## 09:53  Banbury                                 13    10:08
## 09:56  London Paddington                       9     10:10
## 10:00  London Paddington                       8     Delayed
## 10:02  Plymouth                                11    10:36
## 10:03  Guildford                               4     On time
## 10:06  Swansea                                 10    10:59
## 10:07  Abbey Wood                              14    On time
## 10:08  Didcot Parkway                          15    Delayed
## 10:11  London Paddington                       9     10:14
## 10:11  Theale                                  11    Delayed
## 10:12  London Waterloo                         5     10:15
## 10:14  London Paddington                       12    Delayed
## 10:14  Penzance                                10    10:51
## 10:18  Gatwick Airport                         6     10:30
## 10:18  London Paddington                       9     Delayed
## 10:19  Basingstoke                             2     On time
## 10:23  Oxford                                  11    On time
## 10:25  London Paddington                       9     On time
## 10:28  Cheltenham Spa                          10    10:36
## 10:33  London Paddington                       7     On time
## 10:36  Didcot Parkway                          15    Delayed
## 10:39  Abbey Wood                              -     Cancelled
## 10:41  London Paddington                       9     Delayed
## 10:42  Bristol Temple Meads                    10    11:02
## 10:43  London Waterloo                         6     On time
## 10:44  Manchester Piccadilly                   7     On time
## 10:45  Carmarthen                              11    11:11
## 10:45  Redhill                                 4     Delayed
## 10:46  London Paddington                       9     Delayed
## 10:49  London Paddington                       15    Delayed
## 10:52  London Paddington                       9     Delayed
## 10:53  Gatwick Airport                         5     10:58
## 10:54  Great Malvern                           10    On time
## 10:55  Basingstoke                             2     On time
## 10:55  London Paddington                       -     Cancelled
## 10:58  Didcot Parkway                          15    Delayed
## 11:06  Bournemouth                             8     On time
## 11:09  Abbey Wood                              -     Cancelled
## 11:09  Bristol Temple Meads                    -     Cancelled
## 11:11  London Paddington                       -     Cancelled
## 11:11  London Waterloo                         4     On time
## 11:13  Theale                                  11    On time
## 11:15  London Paddington                       12    Delayed
## 11:16  London Paddington                       9     Delayed
## 11:18  Cardiff Central                         10    11:21
## 11:19  Basingstoke                             2     On time
## 11:21  London Paddington                       8     Delayed
## 11:21  Penzance                                11    On time
## 11:25  London Paddington                       9     Delayed
## 11:26  Oxford                                  10    On time
## 11:30  Cheltenham Spa                          11    On time
## 11:30  Didcot Parkway                          15    On time
## 11:33  London Paddington                       7A    Delayed
## 11:33  Redhill                                 5     On time
## 11:40  Abbey Wood                              14    On time
## 11:40  Bristol Temple Meads                    10    On time
## 11:41  London Paddington                       9     Delayed
## 11:41  Manchester Piccadilly                   8     On time
## 11:43  London Waterloo                         6     On time
## 11:44  London Paddington                       13    Delayed
## 11:46  London Paddington                       9     On time
## 11:46  Swansea                                 11    On time
## 11:50  Basingstoke                             2     On time
## 11:51  Gatwick Airport                         5     On time
## 11:51  London Paddington                       7     On time
## 11:55  Great Malvern                           10    On time
## 11:55  London Paddington                       9     On time
## 12:00  London Paddington                       -     On time
## 10:04  Heathrow Central Bus Stn                BUS   On time
## 10:34  Heathrow Central Bus Stn                BUS   On time
## 11:04  Heathrow Central Bus Stn                BUS   On time
## 11:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-28 10:03:47
## Time   To                                      Plat  Expected
## 08:20  London Paddington                       10    10:08
## 08:26  Didcot Parkway                          12    10:07
## 08:29  London Paddington                       10    10:15
## 08:41  London Paddington                       11    10:26
## 08:50  London Paddington                       -     10:33
## 09:05  London Paddington                       10    10:34
## 09:19  Great Malvern                           9B    10:08
## 09:23  Paignton                                8     10:14
## 09:35  London Paddington                       10A   10:31
## 09:36  Theale                                  7     Delayed
## 09:38  Ealing Broadway                         15    Delayed
## 09:42  London Paddington                       10    10:44
## 09:43  Cardiff Central                         9     Delayed
## 09:48  Oxford                                  9A    Delayed
## 09:54  Cheltenham Spa                          8B    10:11
## 09:58  Bristol Temple Meads                    9     10:11
## 10:02  Penzance                                8     Delayed
## 10:04  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:04  London Paddington                       11    10:37
## 10:07  Basingstoke                             2     On time
## 10:08  London Paddington                       10    11:00
## 10:09  Ealing Broadway                         15    Delayed
## 10:09  London Waterloo                         6     On time
## 10:12  London Paddington                       11    Delayed
## 10:13  Swansea                                 9     10:15
## 10:16  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 10:17  London Paddington                       10    10:52
## 10:19  Hereford                                9     Delayed
## 10:20  Redhill                                 4     On time
## 10:23  Didcot Parkway                          12    Delayed
## 10:26  London Paddington                       11    On time
## 10:27  Abbey Wood                              14    On time
## 10:27  Bristol Temple Meads                    9     On time
## 10:32  Basingstoke                             2     On time
## 10:34  London Paddington                       10    10:37
## 10:37  Ealing Broadway                         15    Delayed
## 10:39  London Waterloo                         5     On time
## 10:39  Theale                                  7     On time
## 10:43  Cardiff Central                         9     Delayed
## 10:43  London Paddington                       10    11:03
## 10:48  London Paddington                       11    11:12
## 10:48  Oxford                                  9     Delayed
## 10:52  Bournemouth                             7     On time
## 10:53  Cheltenham Spa                          9     Delayed
## 10:53  Didcot Parkway                          15    Delayed
## 10:57  Abbey Wood                              15    On time
## 10:57  London Paddington                       10    On time
## 10:58  Plymouth                                12    On time
##        via Bristol                             
## 11:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 11:07  Basingstoke                             2     On time
## 11:09  London Waterloo                         6     On time
## 11:11  Ealing Broadway                         15    Delayed
## 11:12  London Paddington                       -     Cancelled
## 11:13  Swansea                                 -     Cancelled
## 11:15  London Paddington                       11    On time
## 11:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 11:19  Worcester Shrub Hill                    9     Delayed
## 11:20  London Paddington                       10    11:22
## 11:20  Redhill                                 5     On time
## 11:23  Taunton                                 8     Delayed
## 11:26  Didcot Parkway                          12    Delayed
## 11:26  London Paddington                       11    On time
## 11:27  Abbey Wood                              13    On time
## 11:27  Bristol Temple Meads                    9     Delayed
## 11:29  London Paddington                       10    On time
## 11:32  Basingstoke                             2     On time
## 11:34  London Paddington                       11    On time
## 11:37  Theale                                  7A    Delayed
## 11:39  London Waterloo                         4     On time
## 11:40  Ealing Broadway                         15    On time
## 11:43  Cardiff Central                         9     Delayed
## 11:43  London Paddington                       10    On time
## 11:48  London Paddington                       11    On time
## 11:49  Oxford                                  9     On time
## 11:53  Cheltenham Spa                          7     On time
## 11:53  Didcot Parkway                          13    Delayed
## 11:57  Abbey Wood                              14    On time
## 11:57  Bristol Temple Meads                    9     On time
## 11:58  London Paddington                       10    On time
## 12:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 12:02  Penzance                                -     On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               -     On time
```
