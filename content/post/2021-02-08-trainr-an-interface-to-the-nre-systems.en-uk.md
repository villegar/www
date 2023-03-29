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

## Example (Last rendered on 2023-03-29 17:05)

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
## Reading (RDG) Station Board on 2023-03-29 17:05:28
## Time   From                                    Plat  Expected
## 17:40  Abbey Wood                              14    18:04
## 17:40  Manchester Piccadilly                   8     18:22
## 17:41  London Paddington                       9     18:12
## 17:42  Exeter St Davids                        10A   18:05
## 17:47  Swansea                                 10    18:25
## 17:54  London Paddington                       12B   18:11
## 17:57  Plymouth                                10    18:07
## 17:58  Abbey Wood                              13    18:07
## 17:58  London Paddington                       9     18:12
## 18:01  London Paddington                       7     18:13
## 18:06  Bournemouth                             12    18:11
## 18:09  Bristol Temple Meads                    11    18:59
## 18:10  Abbey Wood                              14    18:12
## 18:11  London Paddington                       9     18:16
## 18:13  London Waterloo                         6     On time
## 18:17  Cardiff Central                         -     Cancelled
## 18:20  Basingstoke                             2     On time
## 18:25  Abbey Wood                              13    On time
## 18:25  London Paddington                       8     Delayed
## 18:25  Newbury                                 11    On time
## 18:26  Oxford                                  -     Cancelled
## 18:27  London Paddington                       7     On time
## 18:29  Didcot Parkway                          15    On time
## 18:30  Gloucester                              11    18:33
## 18:30  London Paddington                       12    On time
## 18:33  Redhill                                 4     On time
## 18:34  London Paddington                       7     Delayed
## 18:35  Newbury                                 1     On time
## 18:40  Abbey Wood                              14    On time
## 18:40  Bristol Temple Meads                    10    Delayed
## 18:40  Manchester Piccadilly                   8     On time
## 18:40  Newbury                                 11    On time
## 18:42  London Paddington                       -     Cancelled
## 18:44  London Paddington                       -     Cancelled
## 18:44  London Waterloo                         5     On time
## 18:47  Swansea                                 10    19:00
## 18:50  Basingstoke                             3     On time
## 18:53  London Paddington                       9     Delayed
## 18:53  London Paddington                       12B   Delayed
## 18:57  Abbey Wood                              13    On time
## 18:57  Plymouth                                11    Delayed
## 18:57  Worcester Shrub Hill                    10    On time
## 18:59  London Paddington                       7     Delayed
## 19:04  Basingstoke                             2     On time
## 19:05  Didcot Parkway                          15    On time
## 19:09  Abbey Wood                              13    On time
## 19:09  Gatwick Airport                         14    On time
## 19:10  Weston-super-Mare                       10    Delayed
## 19:11  London Paddington                       9     Delayed
## 19:14  Abbey Wood                              14    On time
## 19:15  Newbury                                 1     On time
## 19:16  Cardiff Central                         -     Cancelled
## 19:17  London Waterloo                         6     On time
## 19:23  Worcester Foregate Street               10    On time
## 19:26  London Paddington                       8     Delayed
## 19:28  Didcot Parkway                          15    On time
## 19:28  London Paddington                       7     Delayed
## 19:31  Cheltenham Spa                          11    Delayed
## 19:33  Redhill                                 4     On time
## 19:34  London Paddington                       12    Delayed
## 19:35  Basingstoke                             2     On time
## 19:35  London Paddington                       -     Cancelled
## 19:39  Bristol Temple Meads                    10    Delayed
## 19:40  Abbey Wood                              13    On time
## 19:41  London Paddington                       9     Delayed
## 19:41  Manchester Piccadilly                   7     On time
## 19:44  Abbey Wood                              14    On time
## 19:44  London Waterloo                         5     On time
## 19:46  Swansea                                 10    On time
## 19:53  London Paddington                       -     Cancelled
## 19:54  Plymouth                                11    20:01
## 19:54  Worcester Foregate Street               10    On time
## 19:55  London Paddington                       12    Delayed
## 19:56  London Paddington                       -     On time
## 19:58  Didcot Parkway                          -     On time
## 20:00  Basingstoke                             -     On time
## 20:04  Gatwick Airport                         -     On time
## 20:04  Newbury                                 -     On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:58  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-29 17:05:35
## Time   To                                      Plat  Expected
## 17:43  London Paddington                       10A   18:06
## 17:43  Swansea                                 9     18:13
## 17:50  London Paddington                       10    18:26
## 17:52  Bournemouth                             8     18:23
## 17:58  Abbey Wood                              14    18:07
## 17:58  Didcot Parkway                          12B   18:12
## 17:58  London Paddington                       10    18:08
## 18:00  Hereford                                9     18:14
## 18:03  Plymouth                                7     18:14
## 18:07  Newbury                                 11A   On time
## 18:09  London Waterloo                         4     On time
## 18:12  London Paddington                       11    19:00
## 18:13  Carmarthen                              9     18:16
## 18:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 18:17  Abbey Wood                              13    On time
## 18:20  London Paddington                       -     Cancelled
## 18:20  Redhill                                 5     On time
## 18:26  London Paddington                       -     Cancelled
## 18:27  Bristol Temple Meads                    8     Delayed
## 18:28  Abbey Wood                              14    On time
## 18:28  London Paddington                       -     Cancelled
## 18:29  Liskeard                                7     On time
## 18:32  Basingstoke                             2     On time
## 18:32  Didcot Parkway                          12    On time
## 18:32  London Paddington                       11    18:34
## 18:37  Ealing Broadway                         15    On time
## 18:38  Frome                                   7     Delayed
## 18:39  London Waterloo                         6     On time
## 18:43  London Paddington                       10    Delayed
## 18:43  Swansea                                 -     Cancelled
## 18:45  London Paddington                       -     Cancelled
## 18:47  Abbey Wood                              13    On time
## 18:49  London Paddington                       10    19:01
## 18:55  Cheltenham Spa                          9     Delayed
## 18:57  Didcot Parkway                          12B   Delayed
## 18:58  Abbey Wood                              14    On time
## 18:58  London Paddington                       11    Delayed
## 19:00  London Paddington                       10    On time
## 19:00  Weston-super-Mare                       9     Delayed
## 19:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 19:01  Plymouth                                7     Delayed
## 19:05  Basingstoke                             3     On time
## 19:09  London Waterloo                         5     On time
## 19:10  Newbury                                 1     On time
## 19:12  Ealing Broadway                         15    On time
## 19:13  London Paddington                       10    Delayed
## 19:13  Swansea                                 9     Delayed
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:18  London Paddington                       -     Cancelled
## 19:20  Redhill                                 15A   On time
## 19:25  Basingstoke                             2     On time
## 19:27  Abbey Wood                              14    On time
## 19:27  Bristol Temple Meads                    8     Delayed
## 19:27  London Paddington                       10    On time
## 19:29  Plymouth                                7     Delayed
## 19:34  Didcot Parkway                          12    Delayed
## 19:34  London Paddington                       11    Delayed
## 19:37  Bedwyn                                  8     On time
## 19:37  Ealing Broadway                         15    On time
## 19:39  London Waterloo                         6     On time
## 19:41  London Paddington                       10    Delayed
## 19:42  Newbury                                 1     On time
## 19:43  Swansea                                 9     Delayed
## 19:49  London Paddington                       10    On time
## 19:50  Bournemouth                             7     On time
## 19:55  London Paddington                       11    20:01
## 19:55  Oxford                                  -     Cancelled
## 19:57  Abbey Wood                              13    On time
## 19:57  Basingstoke                             2     On time
## 19:57  Didcot Parkway                          12    Delayed
## 19:58  London Paddington                       10    On time
## 19:58  Weston-super-Mare                       -     On time
## 20:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               -     On time
```
