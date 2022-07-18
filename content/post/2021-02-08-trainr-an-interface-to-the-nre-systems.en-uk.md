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

## Example (Last rendered on 2022-07-18 14:18)

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
## Reading (RDG) Station Board on 2022-07-18 14:18:47
## Time   From                                    Plat  Expected
## 14:33  London Paddington                       -     15:21
## 14:45  Swansea                                 10    15:25
## 14:46  London Paddington                       8     15:15
## 14:58  Penzance                                11    15:47
## 15:09  Bristol Temple Meads                    10    15:35
## 15:11  London Paddington                       9     15:50
## 15:15  Cardiff Central                         -     Cancelled
## 15:16  London Paddington                       -     Cancelled
## 15:17  London Paddington                       12    15:19
## 15:22  Newbury                                 11    On time
## 15:25  London Paddington                       -     Cancelled
## 15:25  Oxford                                  10    15:31
## 15:26  Basingstoke                             2     On time
## 15:27  London Paddington                       7     15:46
## 15:30  Cheltenham Spa                          -     Cancelled
## 15:33  London Paddington                       -     15:41
## 15:33  Redhill                                 5     On time
## 15:35  Didcot Parkway                          -     Cancelled
## 15:36  Newbury                                 1     On time
## 15:39  Bristol Temple Meads                    -     Cancelled
## 15:39  London Paddington                       -     Cancelled
## 15:41  Birmingham New Street                   8     16:06
## 15:41  London Paddington                       -     Cancelled
## 15:41  London Waterloo                         6     On time
## 15:44  Swansea                                 10    16:05
## 15:46  London Paddington                       -     Cancelled
## 15:46  London Paddington                       -     Cancelled
## 15:47  Exeter St Davids                        11    16:10
## 15:49  London Paddington                       -     15:54
## 15:51  Gatwick Airport                         -     Cancelled
## 15:51  London Paddington                       -     Cancelled
## 15:53  Basingstoke                             2     On time
## 15:53  Hereford                                -     Cancelled
## 15:56  London Paddington                       9     On time
## 15:57  Newquay                                 11    16:12
## 16:07  Didcot Parkway                          15    On time
## 16:09  Bristol Temple Meads                    10    16:15
## 16:11  London Paddington                       9     On time
## 16:11  London Paddington                       14    16:17
## 16:11  London Waterloo                         4     On time
## 16:16  Cardiff Central                         -     Cancelled
## 16:18  Basingstoke                             2     On time
## 16:21  London Paddington                       12    On time
## 16:24  Oxford                                  10    On time
## 16:25  London Paddington                       -     Cancelled
## 16:27  London Paddington                       7     On time
## 16:29  Cheltenham Spa                          -     Cancelled
## 16:31  Didcot Parkway                          -     Cancelled
## 16:32  Newbury                                 1     On time
## 16:33  London Paddington                       -     On time
## 16:33  Redhill                                 5     On time
## 16:39  Bristol Temple Meads                    -     Cancelled
## 16:39  London Paddington                       -     Cancelled
## 16:41  London Paddington                       -     Cancelled
## 16:41  London Waterloo                         6     On time
## 16:42  London Paddington                       -     Cancelled
## 16:43  Paignton                                11    On time
## 16:45  Swansea                                 10    On time
## 16:46  London Paddington                       9     On time
## 16:50  Basingstoke                             2     On time
## 16:54  Worcester Foregate Street               -     Cancelled
## 16:55  Newbury                                 12    On time
## 16:56  London Paddington                       9     On time
## 16:56  London Paddington                       13    On time
## 16:59  London Paddington                       7     On time
## 17:01  Penzance                                10    On time
## 17:03  Didcot Parkway                          15    On time
## 17:03  Gatwick Airport                         -     Cancelled
## 17:09  Bristol Temple Meads                    11    On time
## 17:11  London Paddington                       9     On time
## 17:14  London Paddington                       14    On time
## 17:16  London Waterloo                         6     On time
## 15:31  Heathrow Central Bus Stn                BUS   On time
## 16:06  Heathrow Central Bus Stn                BUS   On time
## 16:41  Heathrow Central Bus Stn                BUS   On time
## 17:16  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-07-18 14:18:54
## Time   To                                      Plat  Expected
## 14:48  London Paddington                       10    15:26
## 14:49  Oxford                                  8     15:18
## 14:57  Weston-super-Mare                       9     Delayed
## 15:04  London Paddington                       11    15:48
## 15:10  Newbury                                 13B   Delayed
## 15:13  London Paddington                       10    15:36
## 15:13  Swansea                                 9     15:51
## 15:15  Birmingham New Street                   -     Cancelled
##        via Coventry                            
## 15:18  London Paddington                       -     Cancelled
## 15:18  Redhill                                 5     On time
## 15:18  Worcester Foregate Street               -     Cancelled
## 15:23  Didcot Parkway                          12    On time
## 15:24  London Paddington                       11    On time
## 15:27  Bristol Temple Meads                    -     Cancelled
## 15:27  Ealing Broadway                         14    On time
## 15:27  London Paddington                       10    15:32
## 15:29  Penzance                                7     15:47
##        via Bristol                             
## 15:32  Basingstoke                             -     On time
## 15:34  London Paddington                       -     Cancelled
## 15:37  Newbury                                 -     15:42
## 15:42  Ealing Broadway                         -     Cancelled
## 15:42  London Waterloo                         4     On time
## 15:43  Cardiff Central                         -     Cancelled
## 15:43  London Paddington                       -     Cancelled
## 15:45  London Paddington                       10    16:06
## 15:48  Worcester Foregate Street               -     Cancelled
## 15:49  Oxford                                  -     15:54
## 15:50  London Paddington                       11    16:11
## 15:50  Newbury                                 3     On time
## 15:51  Didcot Parkway                          -     Cancelled
## 15:53  Cheltenham Spa                          -     Cancelled
## 15:56  London Paddington                       -     Cancelled
## 15:58  Ealing Broadway                         -     Cancelled
## 15:58  Weston-super-Mare                       9     On time
## 16:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 16:04  London Paddington                       11    16:13
## 16:07  Basingstoke                             -     On time
## 16:12  London Paddington                       10    16:16
## 16:12  London Waterloo                         6     On time
## 16:12  Newbury                                 -     On time
## 16:13  Swansea                                 9     On time
## 16:14  Ealing Broadway                         15    On time
## 16:18  Ealing Broadway                         13    On time
## 16:18  London Paddington                       -     Cancelled
## 16:19  Great Malvern                           -     Cancelled
## 16:20  Redhill                                 5     On time
## 16:24  London Paddington                       11    On time
## 16:27  Bristol Temple Meads                    -     Cancelled
## 16:27  London Paddington                       10    On time
## 16:28  Ealing Broadway                         14    On time
## 16:29  Penzance                                7     On time
## 16:32  London Paddington                       -     Cancelled
## 16:33  Basingstoke                             2     On time
## 16:37  Newbury                                 -     On time
## 16:38  Ealing Broadway                         -     Cancelled
## 16:41  London Waterloo                         4     On time
## 16:42  London Paddington                       -     Cancelled
## 16:43  Swansea                                 -     Cancelled
## 16:45  London Paddington                       11    On time
## 16:47  London Paddington                       10    On time
## 16:48  Ealing Broadway                         -     Cancelled
## 16:48  Oxford                                  9     On time
## 16:50  Didcot Parkway                          -     Cancelled
## 16:50  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 16:57  London Paddington                       -     Cancelled
## 16:58  Ealing Broadway                         -     Cancelled
## 16:58  Taunton                                 9     On time
## 17:02  Plymouth                                7     On time
## 17:05  London Paddington                       10    On time
## 17:10  Newbury                                 1     On time
## 17:11  London Paddington                       11    On time
## 17:12  London Waterloo                         6     On time
## 17:13  Swansea                                 9     On time
## 17:15  Basingstoke                             -     On time
## 17:15  Birmingham New Street                   8     On time
##        via Coventry                            
## 15:20  Heathrow Central Bus Stn                BUS   On time
## 15:55  Heathrow Central Bus Stn                BUS   On time
## 16:30  Heathrow Central Bus Stn                BUS   On time
## 17:05  Heathrow Central Bus Stn                BUS   On time
```
