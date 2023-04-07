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

## Example (Last rendered on 2023-04-07 18:04)

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
## Reading (RDG) Station Board on 2023-04-07 18:04:10
## Time   From                                    Plat  Expected
## 18:53  London Paddington                       8     On time
## 18:57  Great Malvern                           -     Cancelled
## 18:59  London Paddington                       7     19:03
## 19:03  London Paddington                       13    19:10
## 19:05  Didcot Parkway                          15A   On time
## 19:09  Gatwick Airport                         14    Delayed
## 19:10  Weston-super-Mare                       10    19:14
## 19:11  Bournemouth                             8B    On time
## 19:11  London Paddington                       8     On time
## 19:18  Cardiff Central                         10    Delayed
## 19:20  London Waterloo                         6     On time
## 19:20  Penzance                                11    On time
## 19:21  London Paddington                       -     Cancelled
## 19:22  Didcot Parkway                          10    On time
## 19:23  Oxford                                  -     Cancelled
## 19:26  London Paddington                       8     19:34
## 19:28  Didcot Parkway                          15A   On time
## 19:31  Cheltenham Spa                          11A   On time
## 19:33  Redhill                                 4     19:49
## 19:34  London Paddington                       12B   On time
## 19:38  London Paddington                       13    On time
## 19:39  Bristol Temple Meads                    10    On time
## 19:41  London Paddington                       8     On time
## 19:41  London Waterloo                         5     19:44
## 19:47  Swansea                                 10    Delayed
## 19:50  Didcot Parkway                          7     On time
## 19:51  London Paddington                       8B    On time
## 19:53  London Paddington                       8B    On time
## 19:54  Worcester Foregate Street               -     Cancelled
## 19:55  London Paddington                       12B   On time
## 19:56  London Paddington                       8     On time
## 19:58  Didcot Parkway                          15A   On time
## 19:59  London Paddington                       8     On time
## 19:59  Plymouth                                11    20:10
## 20:04  Gatwick Airport                         4     On time
## 20:07  London Paddington                       14    On time
## 20:10  Weston-super-Mare                       10    On time
## 20:11  London Paddington                       8     On time
## 20:11  London Waterloo                         6     On time
## 20:17  London Paddington                       12B   On time
## 20:17  London Paddington                       -     Cancelled
## 20:24  London Paddington                       8     On time
## 20:28  Banbury                                 -     Cancelled
## 20:32  Cheltenham Spa                          10A   On time
## 20:33  London Paddington                       15    On time
## 20:34  Didcot Parkway                          13A   On time
## 20:35  Redhill                                 14A   On time
## 20:41  London Waterloo                         4     Delayed
## 20:44  Swansea                                 10    On time
## 20:46  London Paddington                       12B   On time
## 20:47  London Paddington                       -     Cancelled
## 20:51  London Paddington                       7B    On time
## 20:53  Gatwick Airport                         6     On time
## 20:53  Great Malvern                           -     Cancelled
## 20:55  London Paddington                       8     On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:21  Bedwyn                                  BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:40  Bramley (Hampshire)                     BUS   On time
## 19:47  Newbury                                 BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
## 20:00  Newbury                                 BUS   On time
## 20:00  Winchester                              BUS   On time
## 20:21  Bedwyn                                  BUS   On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:40  Bramley (Hampshire)                     BUS   On time
## 20:47  Newbury                                 BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
## 21:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-07 18:04:18
## Time   To                                      Plat  Expected
## 18:56  Cheltenham Spa                          8     19:02
## 19:00  London Paddington                       -     Cancelled
## 19:01  Penzance                                7     19:04
## 19:12  Ealing Broadway                         15A   On time
## 19:12  London Waterloo                         5     On time
## 19:13  London Paddington                       10    19:15
## 19:13  Swansea                                 8     On time
## 19:15  Didcot Parkway                          8B    On time
## 19:20  London Paddington                       10    Delayed
## 19:20  Redhill                                 4     Delayed
## 19:22  London Paddington                       10    On time
## 19:23  Hereford                                -     Cancelled
## 19:24  Ealing Broadway                         13    On time
## 19:24  London Paddington                       11    On time
## 19:27  Bristol Temple Meads                    8     19:35
## 19:27  London Paddington                       -     Cancelled
## 19:34  Didcot Parkway                          12B   On time
## 19:34  London Paddington                       11A   On time
## 19:37  Ealing Broadway                         15A   On time
## 19:41  London Paddington                       10    On time
## 19:42  London Waterloo                         6     On time
## 19:43  Swansea                                 8     On time
## 19:50  London Paddington                       10    Delayed
## 19:53  Worcester Shrub Hill                    8B    On time
##        via Gloucester                          
## 19:54  Ealing Broadway                         13    On time
## 19:56  Didcot Parkway                          8B    On time
## 19:57  Didcot Parkway                          12B   On time
## 19:58  London Paddington                       -     Cancelled
## 20:00  Weston-super-Mare                       8     On time
## 20:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 20:02  London Paddington                       11    20:11
## 20:03  Plymouth                                8     On time
## 20:12  London Paddington                       10    On time
## 20:12  London Waterloo                         5     On time
## 20:13  Ealing Broadway                         15A   On time
## 20:13  Swansea                                 8     On time
## 20:15  Didcot Parkway                          7B    On time
## 20:19  Hereford                                -     Cancelled
## 20:20  Shalford                                4     On time
## 20:23  Didcot Parkway                          12B   On time
## 20:27  Bristol Temple Meads                    8     On time
## 20:27  Ealing Broadway                         14    On time
## 20:31  London Paddington                       -     Cancelled
## 20:36  London Paddington                       10A   On time
## 20:42  London Waterloo                         6     On time
## 20:45  Ealing Broadway                         13A   On time
## 20:47  London Paddington                       10    On time
## 20:49  Oxford                                  -     Cancelled
## 20:51  Didcot Parkway                          12B   On time
## 20:53  Cheltenham Spa                          7B    On time
## 20:54  Ealing Broadway                         15    On time
## 20:56  London Paddington                       -     Cancelled
## 20:57  Weston-super-Mare                       8     On time
## 21:01  Gatwick Airport                         6     On time
##        via Guildford                           
## 19:10  Newbury                                 BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:38  Bramley (Hampshire)                     BUS   On time
## 19:40  Bedwyn                                  BUS   On time
## 19:55  Winchester                              BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 20:10  Newbury                                 BUS   On time
## 20:38  Bramley (Hampshire)                     BUS   On time
## 20:40  Bedwyn                                  BUS   On time
## 20:55  Basingstoke                             BUS   On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
```
