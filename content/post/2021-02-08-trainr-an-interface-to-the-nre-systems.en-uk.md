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

## Example (Last rendered on 2022-07-06 16:03)

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
## Reading (RDG) Station Board on 2022-07-06 16:03:41
## Time   From                                    Plat  Expected
## 15:09  Bristol Temple Meads                    10    17:17
## 15:30  Cheltenham Spa                          10A   17:02
## 15:35  Swansea                                 11    17:10
## 15:47  Exeter St Davids                        11    17:19
## 15:57  Par                                     11    17:46
## 16:16  Bristol Parkway                         11A   17:54
## 16:31  Didcot Parkway                          15    16:41
## 16:35  Swansea                                 11    18:09
## 16:39  Bristol Temple Meads                    10A   17:24
## 16:41  London Paddington                       9     Delayed
## 16:42  London Paddington                       12    17:35
## 16:43  Paignton                                11    18:18
## 16:46  London Paddington                       9B    17:19
## 16:54  Worcester Foregate Street               10A   17:26
## 16:56  London Paddington                       9     Delayed
## 16:59  London Paddington                       7     Delayed
## 17:01  Penzance                                10    Delayed
## 17:03  Didcot Parkway                          15    17:11
## 17:03  Gatwick Airport                         5     On time
## 17:06  Bournemouth                             8     On time
## 17:09  Bristol Temple Meads                    -     Cancelled
## 17:11  London Paddington                       9     Delayed
## 17:14  London Paddington                       -     Cancelled
## 17:16  London Waterloo                         6     On time
## 17:17  Bristol Parkway                         10    Delayed
## 17:22  London Paddington                       12    17:24
## 17:22  Newbury                                 -     Cancelled
## 17:24  Oxford                                  10A   On time
## 17:25  London Paddington                       8     On time
## 17:26  Basingstoke                             -     Cancelled
## 17:27  London Paddington                       7     On time
## 17:27  London Paddington                       13    17:35
## 17:29  Cheltenham Spa                          10A   18:05
## 17:34  Newbury                                 1     On time
## 17:35  Didcot Parkway                          15    On time
## 17:35  London Paddington                       -     Cancelled
## 17:35  Redhill                                 5     On time
## 17:35  Swansea                                 11    18:26
## 17:41  London Paddington                       -     Cancelled
## 17:41  London Paddington                       14    On time
## 17:41  Manchester Piccadilly                   8     On time
## 17:42  Bristol Temple Meads                    10    On time
## 17:42  Exeter St Davids                        11A   Delayed
## 17:42  London Waterloo                         4     On time
## 17:46  Basingstoke                             2     On time
## 17:54  London Paddington                       12B   On time
## 17:55  London Paddington                       8B    On time
## 17:56  Hereford                                10A   On time
## 17:57  Plymouth                                11    19:10
## 17:58  London Paddington                       9     On time
## 17:59  London Paddington                       13    On time
## 18:01  London Paddington                       7     On time
## 18:02  Gatwick Airport                         6     On time
## 18:03  Didcot Parkway                          15    On time
## 18:05  Bournemouth                             12B   On time
## 18:09  Bristol Temple Meads                    -     Cancelled
## 18:11  London Paddington                       9     On time
## 18:11  London Paddington                       14    On time
## 18:12  London Waterloo                         5     On time
## 18:17  Bristol Parkway                         10    Delayed
## 18:20  Basingstoke                             2     On time
## 18:25  Newbury                                 11    On time
## 18:26  London Paddington                       8     On time
## 18:26  London Paddington                       13    On time
## 18:26  Oxford                                  10    On time
## 18:27  London Paddington                       7     On time
## 18:29  Didcot Parkway                          -     On time
## 18:30  Cheltenham Spa                          -     Cancelled
## 18:30  London Paddington                       12    On time
## 18:33  Redhill                                 4     On time
## 18:34  London Paddington                       -     On time
## 18:35  Newbury                                 -     On time
## 18:35  Swansea                                 -     On time
## 18:40  Bristol Temple Meads                    -     On time
## 18:41  London Paddington                       -     On time
## 18:41  London Paddington                       -     On time
## 18:42  London Waterloo                         -     On time
## 18:43  Manchester Piccadilly                   -     On time
## 18:44  London Paddington                       -     On time
## 18:50  Basingstoke                             -     On time
## 18:53  London Paddington                       -     On time
## 18:57  Great Malvern                           -     Cancelled
## 18:57  London Paddington                       -     On time
## 18:57  Penzance                                -     19:26
## 18:58  London Paddington                       -     On time
## 18:59  London Paddington                       -     On time
## 17:16  Heathrow Central Bus Stn                BUS   On time
## 17:51  Heathrow Central Bus Stn                BUS   On time
## 18:26  Heathrow Central Bus Stn                BUS   On time
## 19:01  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-07-06 16:03:46
## Time   To                                      Plat  Expected
## 15:13  London Paddington                       10    17:18
## 15:34  London Paddington                       10A   17:03
## 15:43  London Paddington                       11    17:11
## 15:50  London Paddington                       11    17:20
## 16:04  London Paddington                       11    17:47
## 16:18  London Paddington                       11A   17:55
## 16:38  Ealing Broadway                         15    Delayed
## 16:42  London Paddington                       11    18:10
## 16:43  Swansea                                 9     Delayed
## 16:45  London Paddington                       10A   17:25
## 16:47  London Paddington                       11    18:19
## 16:48  Oxford                                  9B    17:20
## 16:50  Didcot Parkway                          12    17:36
## 16:54  Bedwyn                                  -     Delayed
## 16:57  London Paddington                       10A   17:27
## 16:58  Taunton                                 9     Delayed
## 17:02  Plymouth                                7     Delayed
## 17:05  London Paddington                       10    Delayed
## 17:10  Newbury                                 1     On time
## 17:11  Ealing Broadway                         15    17:12
## 17:11  London Paddington                       -     Cancelled
## 17:12  London Waterloo                         6     On time
## 17:13  Bristol Parkway                         9     Delayed
## 17:15  Basingstoke                             2     On time
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 17:18  Ealing Broadway                         9     On time
## 17:18  London Paddington                       10    Delayed
## 17:20  Redhill                                 5     On time
## 17:24  London Paddington                       -     Cancelled
## 17:25  Didcot Parkway                          12    On time
## 17:27  Bristol Temple Meads                    8     On time
## 17:27  London Paddington                       10A   On time
## 17:28  Ealing Broadway                         14    On time
## 17:29  Penzance                                7     On time
## 17:32  London Paddington                       10A   18:06
## 17:38  Basingstoke                             2     On time
## 17:41  London Paddington                       11    18:27
## 17:41  Newbury                                 -     Cancelled
## 17:42  Ealing Broadway                         15    On time
## 17:42  London Waterloo                         6     On time
## 17:43  Carmarthen                              -     Cancelled
## 17:43  London Paddington                       10    On time
## 17:48  Ealing Broadway                         13    On time
## 17:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:50  London Paddington                       11A   Delayed
## 17:52  Bournemouth                             8     On time
## 17:57  Basingstoke                             2     On time
## 17:57  Taunton                                 8B    On time
## 17:58  Didcot Parkway                          12B   On time
## 17:58  Ealing Broadway                         14    On time
## 17:58  London Paddington                       11    19:11
## 18:00  Hereford                                9     On time
## 18:00  London Paddington                       10A   On time
## 18:03  Plymouth                                7     On time
## 18:07  Newbury                                 1     On time
## 18:08  Ealing Broadway                         15    On time
## 18:12  London Paddington                       -     Cancelled
## 18:12  London Waterloo                         4     On time
## 18:13  Bristol Parkway                         9     On time
## 18:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 18:17  Ealing Broadway                         13    On time
## 18:20  London Paddington                       10    Delayed
## 18:20  Redhill                                 6     On time
## 18:26  London Paddington                       11    On time
## 18:28  Bristol Temple Meads                    8     On time
## 18:28  Ealing Broadway                         14    On time
## 18:28  London Paddington                       10    On time
## 18:29  Penzance                                7     On time
## 18:32  Basingstoke                             2     On time
## 18:32  Didcot Parkway                          12    On time
## 18:32  London Paddington                       -     Cancelled
## 18:37  Ealing Broadway                         -     On time
## 18:38  Frome                                   -     On time
## 18:42  London Waterloo                         -     On time
## 18:43  London Paddington                       -     On time
## 18:43  Swansea                                 -     On time
## 18:47  Ealing Broadway                         -     On time
## 18:49  London Paddington                       -     On time
## 18:57  Didcot Parkway                          -     On time
## 18:58  Ealing Broadway                         -     On time
## 18:58  London Paddington                       -     19:27
## 18:59  Weston-super-Mare                       -     On time
## 19:00  London Paddington                       -     Cancelled
## 19:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 19:01  Plymouth                                -     On time
## 17:05  Heathrow Central Bus Stn                BUS   On time
## 17:40  Heathrow Central Bus Stn                BUS   On time
## 18:15  Heathrow Central Bus Stn                BUS   On time
## 19:00  Heathrow Central Bus Stn                -     On time
```
