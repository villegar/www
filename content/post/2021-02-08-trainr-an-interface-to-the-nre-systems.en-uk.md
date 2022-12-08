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

## Example (Last rendered on 2022-12-08 08:04)

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
## Reading (RDG) Station Board on 2022-12-08 08:04:12
## Time   From                                    Plat  Expected
## 07:38  London Paddington                       9     Delayed
## 07:44  Abbey Wood                              14    08:10
## 07:46  London Paddington                       8B    08:13
## 07:48  London Paddington                       12B   08:16
## 07:54  Hereford                                11A   08:09
## 07:56  London Paddington                       9     08:04
## 07:57  Abbey Wood                              13    Delayed
## 08:01  Plymouth                                11    08:04
## 08:06  Basingstoke                             2     08:08
## 08:09  Bournemouth                             -     Cancelled
## 08:09  Oxford                                  10A   Delayed
## 08:10  Didcot Parkway                          15A   On time
## 08:11  London Paddington                       9     08:15
## 08:14  Abbey Wood                              14    08:48
## 08:14  London Waterloo                         4     08:56
## 08:14  Worcester Shrub Hill                    11    On time
## 08:16  London Paddington                       9B    08:22
## 08:16  Redhill                                 6     On time
## 08:17  London Paddington                       12B   08:35
## 08:18  Swansea                                 10    On time
## 08:22  Newbury                                 3     On time
## 08:25  London Paddington                       9     08:39
## 08:26  Cheltenham Spa                          10    On time
## 08:27  London Paddington                       7     08:41
## 08:29  Abbey Wood                              14    08:53
## 08:30  Plymouth                                11    On time
## 08:34  Gatwick Airport                         5     On time
## 08:39  Weston-super-Mare                       11    On time
## 08:41  London Paddington                       8     On time
## 08:42  Basingstoke                             2     On time
## 08:43  London Paddington                       9     08:57
## 08:45  Abbey Wood                              12    09:08
## 08:45  Didcot Parkway                          14    On time
## 08:45  London Waterloo                         -     Cancelled
## 08:46  Manchester Piccadilly                   7     On time
## 08:51  London Paddington                       9     09:05
## 08:53  Plymouth                                11    On time
## 08:55  London Paddington                       8     On time
## 08:56  Abbey Wood                              13    09:25
## 08:59  Bristol Temple Meads                    11    On time
## 09:01  Didcot Parkway                          15    On time
## 09:02  Basingstoke                             -     Cancelled
## 09:04  Redhill                                 5     On time
## 09:05  Southampton Central                     8     On time
## 09:09  Newbury                                 11    On time
## 09:11  Hereford                                10    On time
## 09:11  London Paddington                       9     On time
## 09:13  Abbey Wood                              14    09:25
## 09:16  London Paddington                       9     On time
## 09:16  London Waterloo                         -     Cancelled
## 09:19  Swansea                                 10    On time
## 09:24  Oxford                                  10    On time
## 09:25  Gatwick Airport                         5     On time
## 09:25  London Paddington                       9     On time
## 09:26  Abbey Wood                              13    09:35
## 09:27  London Paddington                       7     On time
## 09:30  Truro                                   11    On time
## 09:32  Worcester Shrub Hill                    10    On time
## 09:34  London Paddington                       7     On time
## 09:37  Didcot Parkway                          15    On time
## 09:38  London Paddington                       14    On time
## 09:39  Taunton                                 10    On time
## 09:40  Nottingham                              7     On time
## 09:41  London Paddington                       9     On time
## 09:41  Newbury                                 11    On time
## 09:44  London Waterloo                         6     On time
## 09:45  London Paddington                       12    On time
## 09:45  Swansea                                 10    On time
## 09:46  Basingstoke                             2     On time
## 09:46  London Paddington                       9     On time
## 09:52  London Paddington                       8     On time
## 09:53  Banbury                                 -     Cancelled
## 09:55  Newbury                                 1     On time
## 09:55  Worcester Shrub Hill                    10    On time
## 09:56  London Paddington                       9     On time
## 10:00  London Paddington                       -     On time
## 10:01  Guildford                               -     On time
## 08:27  Heathrow Central Bus Stn                BUS   On time
## 09:04  Heathrow Central Bus Stn                BUS   On time
## 09:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-08 08:04:16
## Time   To                                      Plat  Expected
## 07:39  Bristol Parkway                         9     Delayed
## 07:39  London Waterloo                         4     Delayed
## 07:49  Oxford                                  8B    08:14
## 07:51  Didcot Parkway                          12B   08:17
## 07:53  Cheltenham Spa                          9B    Delayed
## 07:56  Abbey Wood                              14    08:13
## 07:56  London Paddington                       11A   08:10
## 08:00  Basingstoke                             -     Cancelled
## 08:00  Bristol Temple Meads                    9     08:05
## 08:03  Newbury                                 1     On time
## 08:08  London Waterloo                         -     Cancelled
## 08:10  Abbey Wood                              -     Cancelled
## 08:10  London Paddington                       11    On time
## 08:13  Swansea                                 9     08:16
## 08:14  London Paddington                       10A   Delayed
## 08:15  Manchester Piccadilly                   -     Cancelled
##        via Coventry & Stoke-on-Trent           
## 08:17  London Paddington                       11    On time
## 08:19  Great Malvern                           9B    08:23
## 08:20  Guildford                               4     On time
## 08:20  London Paddington                       10    On time
## 08:23  Basingstoke                             -     Cancelled
## 08:25  Abbey Wood                              14    08:51
## 08:26  Didcot Parkway                          12B   08:36
## 08:27  Bristol Temple Meads                    9     08:40
## 08:29  London Paddington                       10    On time
## 08:29  Truro                                   7     08:42
## 08:31  London Paddington                       13    On time
## 08:32  London Paddington                       11    On time
## 08:36  Newbury                                 7     On time
## 08:36  Redhill                                 6     On time
## 08:39  London Waterloo                         4     08:59
## 08:41  London Paddington                       11    On time
## 08:42  Abbey Wood                              14    08:56
## 08:43  Bristol Parkway                         8     On time
## 08:46  Newbury                                 15    On time
## 08:46  Oxford                                  9     08:58
## 08:47  London Paddington                       14    On time
## 08:52  Bournemouth                             7     On time
## 08:53  Cheltenham Spa                          9     09:06
## 08:53  Didcot Parkway                          13    On time
## 08:56  London Paddington                       11    On time
## 08:57  Abbey Wood                              12    09:11
## 08:57  Bristol Temple Meads                    8     On time
## 08:59  Basingstoke                             2     On time
## 09:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 09:05  London Paddington                       11    On time
## 09:07  Ealing Broadway                         15    On time
## 09:09  London Waterloo                         5     On time
## 09:10  London Paddington                       11    On time
## 09:13  London Paddington                       10    On time
## 09:13  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:13  Newbury                                 3     On time
## 09:13  Swansea                                 9     On time
## 09:18  Abbey Wood                              13    09:28
## 09:18  Great Malvern                           9     On time
## 09:20  London Paddington                       10    On time
## 09:20  Redhill                                 5     On time
## 09:23  Didcot Parkway                          12    On time
## 09:26  London Paddington                       10    On time
## 09:27  Abbey Wood                              14    On time
## 09:27  Bristol Temple Meads                    9     On time
## 09:29  Plymouth                                7     On time
## 09:32  Basingstoke                             1     On time
## 09:32  London Paddington                       11    On time
## 09:35  London Paddington                       10    On time
## 09:36  Newbury                                 7     On time
## 09:38  Ealing Broadway                         15    On time
## 09:39  London Waterloo                         4     Delayed
## 09:42  London Paddington                       10    On time
## 09:43  Bristol Parkway                         9     On time
## 09:44  London Paddington                       11    On time
## 09:47  London Paddington                       10    On time
## 09:48  Abbey Wood                              13    On time
## 09:48  Oxford                                  9     On time
## 09:54  Cheltenham Spa                          8     On time
## 09:55  Didcot Parkway                          12    On time
## 09:57  Abbey Wood                              14    On time
## 09:57  London Paddington                       10    On time
## 09:58  Bristol Temple Meads                    9     On time
## 10:02  Paignton                                -     On time
## 08:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
```
