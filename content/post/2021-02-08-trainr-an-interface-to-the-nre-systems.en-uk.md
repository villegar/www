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

## Example (Last rendered on 2023-04-07 16:03)

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
## Reading (RDG) Station Board on 2023-04-07 16:03:59
## Time   From                                    Plat  Expected
## 16:53  Worcester Foregate Street               10    Delayed
## 17:03  Didcot Parkway                          15A   On time
## 17:03  Gatwick Airport                         5     On time
## 17:09  Bristol Temple Meads                    11    17:15
## 17:10  Bournemouth                             8B    On time
## 17:11  London Paddington                       7     On time
## 17:17  Cardiff Central                         11A   17:23
## 17:20  London Waterloo                         6     On time
## 17:21  London Paddington                       -     Cancelled
## 17:22  London Paddington                       12B   On time
## 17:24  Didcot Parkway                          10    On time
## 17:25  London Paddington                       8     On time
## 17:29  Cheltenham Spa                          10A   On time
## 17:33  London Paddington                       14    On time
## 17:33  Penzance                                11    On time
## 17:35  Didcot Parkway                          15A   On time
## 17:35  Redhill                                 5     On time
## 17:38  Bristol Temple Meads                    10    On time
## 17:41  London Paddington                       8     On time
## 17:41  London Waterloo                         4     17:47
## 17:48  Swansea                                 10    On time
## 17:53  London Paddington                       8     On time
## 17:54  London Paddington                       12B   On time
## 17:56  Hereford                                10    Delayed
## 17:58  London Paddington                       7     On time
## 18:02  Gatwick Airport                         5     On time
## 18:02  London Paddington                       8     On time
## 18:03  Didcot Parkway                          15A   On time
## 18:03  London Paddington                       14    On time
## 18:09  Bristol Temple Meads                    11A   18:18
## 18:11  London Paddington                       8     On time
## 18:11  London Waterloo                         6     On time
## 18:17  Cardiff Central                         11    On time
## 18:21  London Paddington                       -     Cancelled
## 18:25  London Paddington                       8     On time
## 18:26  Oxford                                  -     Cancelled
## 18:29  Didcot Parkway                          15A   On time
## 18:30  Cheltenham Spa                          11A   On time
## 18:30  London Paddington                       12B   On time
## 18:33  Redhill                                 4     On time
## 18:34  Plymouth                                10    On time
## 18:36  London Paddington                       14    On time
## 18:40  Bristol Temple Meads                    11    On time
## 18:40  Didcot Parkway                          15A   On time
## 18:41  London Waterloo                         5     On time
## 18:42  London Paddington                       8     On time
## 18:48  Swansea                                 10    On time
## 18:51  London Paddington                       -     Cancelled
## 18:53  London Paddington                       8     On time
## 18:53  London Paddington                       12B   On time
## 18:57  Great Malvern                           -     Cancelled
## 18:59  London Paddington                       7     On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
## 17:21  Bedwyn                                  BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
## 17:40  Bramley (Hampshire)                     BUS   On time
## 17:47  Newbury                                 BUS   On time
## 18:00  Newbury                                 BUS   On time
## 18:00  Winchester                              BUS   On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:21  Bedwyn                                  BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 18:40  Bramley (Hampshire)                     BUS   On time
## 18:47  Newbury                                 BUS   On time
## 19:00  Newbury                                 BUS   On time
## 19:01  Basingstoke                             BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-07 16:04:04
## Time   To                                      Plat  Expected
## 16:57  London Paddington                       10    Delayed
## 17:00  Taunton                                 8     17:04
## 17:02  Penzance                                7     On time
## 17:11  Ealing Broadway                         15A   On time
## 17:11  London Paddington                       11    17:16
## 17:12  London Waterloo                         6     On time
## 17:13  Swansea                                 7     On time
## 17:15  Didcot Parkway                          8B    On time
## 17:18  London Paddington                       11A   17:24
## 17:20  Redhill                                 5     On time
## 17:21  Ealing Broadway                         14    On time
## 17:23  Great Malvern                           -     Cancelled
## 17:25  Didcot Parkway                          12B   On time
## 17:27  Bristol Temple Meads                    8     On time
## 17:27  London Paddington                       10    On time
## 17:32  London Paddington                       10A   On time
## 17:33  London Paddington                       11    On time
## 17:41  London Paddington                       10    On time
## 17:42  Ealing Broadway                         15A   On time
## 17:42  London Waterloo                         6     On time
## 17:43  Swansea                                 8     On time
## 17:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:50  London Paddington                       10    On time
## 17:52  Cheltenham Spa                          7     On time
## 17:54  Ealing Broadway                         14    On time
## 17:57  Taunton                                 8     On time
## 17:58  Didcot Parkway                          12B   On time
## 18:00  Hereford                                7     On time
## 18:00  London Paddington                       10    Delayed
## 18:02  Penzance                                8     On time
## 18:08  Ealing Broadway                         15A   On time
## 18:12  London Paddington                       11A   18:19
## 18:12  London Waterloo                         4     On time
## 18:13  Carmarthen                              8     On time
## 18:20  London Paddington                       11    On time
## 18:20  Redhill                                 5     On time
## 18:23  Worcester Foregate Street               -     Cancelled
## 18:24  Ealing Broadway                         14    On time
## 18:27  Bristol Temple Meads                    8     On time
## 18:28  London Paddington                       -     Cancelled
## 18:32  Didcot Parkway                          12B   On time
## 18:32  London Paddington                       11A   On time
## 18:37  Ealing Broadway                         15A   On time
## 18:40  London Paddington                       10    On time
## 18:42  London Waterloo                         6     On time
## 18:43  London Paddington                       11    On time
## 18:43  Swansea                                 8     On time
## 18:50  London Paddington                       10    On time
## 18:51  Bournemouth                             15A   On time
## 18:53  Banbury                                 -     Cancelled
## 18:54  Ealing Broadway                         14    On time
## 18:56  Cheltenham Spa                          8     On time
## 18:57  Didcot Parkway                          12B   On time
## 19:00  London Paddington                       -     Cancelled
## 19:00  Weston-super-Mare                       8     On time
## 19:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 19:01  Penzance                                7     On time
## 17:10  Newbury                                 BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:38  Bramley (Hampshire)                     BUS   On time
## 17:40  Bedwyn                                  BUS   On time
## 17:44  Newbury                                 BUS   On time
## 17:55  Winchester                              BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:10  Newbury                                 BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:38  Bramley (Hampshire)                     BUS   On time
## 18:40  Bedwyn                                  BUS   On time
## 18:44  Newbury                                 BUS   On time
## 18:55  Basingstoke                             BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
```
