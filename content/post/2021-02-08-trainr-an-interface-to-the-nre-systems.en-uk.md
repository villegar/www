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

## Example (Last rendered on 2022-09-19 08:09)

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
## Reading (RDG) Station Board on 2022-09-19 08:09:44
## Time   From                                    Plat  Expected
## 07:46  Penzance                                10    09:08
## 07:49  Swansea                                 8     08:41
## 07:54  Hereford                                9     09:01
## 08:01  Plymouth                                11    Delayed
## 08:18  Swansea                                 10    Delayed
## 08:39  Weston-super-Mare                       11    Delayed
## 08:45  Didcot Parkway                          14    Delayed
## 08:53  Plymouth                                11    Delayed
## 08:59  Bristol Temple Meads                    11    09:45
## 09:01  Didcot Parkway                          15    Delayed
## 09:05  Bournemouth                             12    09:08
## 09:09  Newbury                                 11    Delayed
## 09:11  Hereford                                10A   09:31
## 09:13  London Paddington                       -     Cancelled
## 09:16  London Paddington                       -     Cancelled
## 09:16  London Waterloo                         4     On time
## 09:19  Swansea                                 10    Delayed
## 09:24  Oxford                                  10    Delayed
## 09:25  Gatwick Airport                         5     On time
## 09:25  London Paddington                       9     Delayed
## 09:26  London Paddington                       -     Cancelled
## 09:27  London Paddington                       -     Cancelled
## 09:32  Worcester Shrub Hill                    10A   Delayed
## 09:34  London Paddington                       7     On time
## 09:37  Didcot Parkway                          15    On time
## 09:38  London Paddington                       -     Cancelled
## 09:39  Taunton                                 -     Cancelled
## 09:40  Nottingham                              7     Delayed
## 09:41  London Paddington                       9     On time
## 09:41  London Waterloo                         6     09:43
## 09:41  Newbury                                 11    On time
## 09:45  London Paddington                       12    Delayed
## 09:45  Swansea                                 10    Delayed
## 09:46  London Paddington                       9     On time
## 09:51  Cheltenham Spa                          -     On time
## 09:52  London Paddington                       8     On time
## 09:53  Banbury                                 13    On time
## 09:55  Newbury                                 1     On time
## 09:55  Worcester Shrub Hill                    10A   On time
## 09:56  London Paddington                       9     On time
## 10:00  London Paddington                       8     On time
## 10:01  Guildford                               4     10:05
## 10:02  Penzance                                11    Delayed
## 10:07  London Paddington                       -     Cancelled
## 10:08  Didcot Parkway                          15    On time
## 10:11  London Paddington                       9     On time
## 10:11  London Waterloo                         5     On time
## 10:11  Newbury                                 11    On time
## 10:14  Bristol Temple Meads                    10    Delayed
## 10:16  London Paddington                       12    On time
## 10:18  Gatwick Airport                         -     Cancelled
## 10:18  London Paddington                       9     On time
## 10:19  Basingstoke                             2     On time
## 10:23  Oxford                                  11    Delayed
## 10:25  London Paddington                       9     On time
## 10:27  London Paddington                       7     On time
## 10:28  Cheltenham Spa                          -     Cancelled
## 10:33  London Paddington                       8     On time
## 10:36  Didcot Parkway                          15    On time
## 10:39  London Paddington                       -     Cancelled
## 10:40  Bristol Temple Meads                    10    Delayed
## 10:41  London Paddington                       9     On time
## 10:41  London Waterloo                         6     On time
## 10:43  Newbury                                 1     On time
## 10:44  Manchester Piccadilly                   7     On time
## 10:45  Carmarthen                              11    Delayed
## 10:45  Redhill                                 4     On time
## 10:46  London Paddington                       13    On time
## 10:46  London Paddington                       9     On time
## 10:52  London Paddington                       9     On time
## 10:53  Gatwick Airport                         5     On time
## 10:54  Great Malvern                           10    On time
## 10:55  London Paddington                       -     On time
## 10:56  Basingstoke                             2     On time
## 10:59  London Paddington                       -     On time
## 11:00  Plymouth                                -     Cancelled
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
## Reading (RDG) Station Board on 2022-09-19 08:09:49
## Time   To                                      Plat  Expected
## 07:48  London Paddington                       10    09:09
## 07:51  London Paddington                       8     Delayed
## 07:56  London Paddington                       9     Delayed
## 08:10  London Paddington                       11    Delayed
## 08:20  London Paddington                       10    Delayed
## 08:41  London Paddington                       11    Delayed
## 08:46  Newbury                                 15    Delayed
## 08:47  London Paddington                       14    Delayed
## 08:56  London Paddington                       11    Delayed
## 08:57  Bristol Temple Meads                    8     Delayed
## 09:05  London Paddington                       11    09:46
## 09:07  Ealing Broadway                         15    Delayed
## 09:10  London Paddington                       11    Delayed
## 09:12  London Waterloo                         5     On time
## 09:13  London Paddington                       10A   09:32
## 09:13  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 09:13  Newbury                                 2     On time
## 09:13  Swansea                                 9     On time
## 09:18  Great Malvern                           -     Cancelled
## 09:20  London Paddington                       10    Delayed
## 09:20  Redhill                                 6     On time
## 09:23  Didcot Parkway                          13    On time
## 09:26  London Paddington                       10    Delayed
## 09:27  Bristol Temple Meads                    9     Delayed
## 09:27  Ealing Broadway                         -     Cancelled
## 09:29  Plymouth                                -     Cancelled
## 09:32  Basingstoke                             1     On time
## 09:35  London Paddington                       10A   Delayed
## 09:36  Newbury                                 7     On time
## 09:38  Ealing Broadway                         15    On time
## 09:42  London Paddington                       -     Cancelled
## 09:42  London Waterloo                         4     On time
## 09:43  Cardiff Central                         9     On time
## 09:44  London Paddington                       11    On time
## 09:47  London Paddington                       10    Delayed
## 09:48  Oxford                                  9     On time
## 09:51  London Paddington                       -     On time
## 09:54  Cheltenham Spa                          8     On time
## 09:55  Didcot Parkway                          12    Delayed
## 09:57  Ealing Broadway                         -     Cancelled
## 09:57  London Paddington                       10A   On time
## 09:58  Bristol Temple Meads                    9     On time
## 10:02  Paignton                                8     On time
## 10:04  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:04  London Paddington                       11    Delayed
## 10:10  Ealing Broadway                         15    On time
## 10:12  London Paddington                       11    On time
## 10:12  London Waterloo                         6     On time
## 10:12  Newbury                                 1     On time
## 10:13  Swansea                                 9     On time
## 10:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 10:17  London Paddington                       10    Delayed
## 10:19  Hereford                                9     On time
## 10:20  Redhill                                 4     On time
## 10:23  Didcot Parkway                          12    On time
## 10:26  London Paddington                       11    Delayed
## 10:27  Bristol Temple Meads                    9     On time
## 10:27  Ealing Broadway                         -     Cancelled
## 10:29  Penzance                                7     On time
## 10:32  Basingstoke                             2     On time
## 10:34  London Paddington                       -     Cancelled
## 10:38  Ealing Broadway                         15    On time
## 10:39  Newbury                                 8     On time
## 10:42  London Paddington                       10    Delayed
## 10:42  London Waterloo                         5     On time
## 10:43  Cardiff Central                         9     On time
## 10:48  London Paddington                       11    Delayed
## 10:48  Oxford                                  9     On time
## 10:52  Bournemouth                             7     On time
## 10:53  Cheltenham Spa                          9     On time
## 10:53  Didcot Parkway                          13    On time
## 10:57  Ealing Broadway                         -     Cancelled
## 10:57  London Paddington                       10    On time
## 10:58  Bristol Temple Meads                    -     On time
## 11:01  Exeter St Davids                        -     On time
## 11:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 11:04  London Paddington                       -     Cancelled
## 11:07  Basingstoke                             -     On time
## 09:30  Heathrow Central Bus Stn                BUS   On time
## 10:05  Heathrow Central Bus Stn                BUS   On time
## 10:40  Heathrow Central Bus Stn                BUS   On time
```
