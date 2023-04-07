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

## Example (Last rendered on 2023-04-07 20:05)

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
## Reading (RDG) Station Board on 2023-04-07 20:05:03
## Time   From                                    Plat  Expected
## 19:47  Swansea                                 10    21:36
## 20:44  Swansea                                 10    Delayed
## 20:55  London Paddington                       8     21:14
## 21:03  Didcot Parkway                          15A   20:59
## 21:05  London Paddington                       13    21:08
## 21:06  Bournemouth                             8B    21:10
## 21:09  Bristol Temple Meads                    10    21:13
## 21:11  London Paddington                       8     21:15
## 21:11  London Waterloo                         6     21:14
## 21:16  London Paddington                       -     Cancelled
## 21:20  London Paddington                       14B   21:25
## 21:20  Penzance                                11    21:37
## 21:24  Didcot Parkway                          10    On time
## 21:25  London Paddington                       8     On time
## 21:27  London Paddington                       8     On time
## 21:29  Didcot Parkway                          14A   On time
## 21:29  Redhill                                 5     On time
## 21:33  Cheltenham Spa                          10A   On time
## 21:33  London Paddington                       13    21:39
## 21:41  Didcot Parkway                          15A   On time
## 21:42  London Waterloo                         5     On time
## 21:44  Swansea                                 11    21:57
## 21:45  London Paddington                       12B   On time
## 21:46  London Paddington                       -     Cancelled
## 21:51  London Paddington                       8B    On time
## 21:53  Great Malvern                           10    Delayed
## 21:56  Gatwick Airport                         15    On time
## 22:03  London Paddington                       14    On time
## 22:05  Didcot Parkway                          15A   On time
## 22:08  Taunton                                 10    22:14
## 22:11  London Paddington                       8     On time
## 22:11  London Waterloo                         4     On time
## 22:12  Paignton                                11    On time
## 22:15  London Paddington                       12B   On time
## 22:16  London Paddington                       -     Cancelled
## 22:25  Oxford                                  -     Cancelled
## 22:26  London Paddington                       8     On time
## 22:32  Cheltenham Spa                          10    On time
## 22:33  London Paddington                       13    On time
## 22:34  Shalford                                14A   On time
## 22:39  Didcot Parkway                          7A    On time
## 22:41  London Waterloo                         5     On time
## 22:43  London Paddington                       -     Cancelled
## 22:43  Swansea                                 10    22:48
## 22:45  London Paddington                       12B   On time
## 22:47  Didcot Parkway                          15    On time
## 22:55  London Paddington                       8     On time
## 22:59  Worcester Foregate Street               -     Cancelled
## 23:04  London Paddington                       13    On time
## 21:21  Bedwyn                                  BUS   On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
## 21:40  Bramley (Hampshire)                     BUS   On time
## 21:47  Newbury                                 BUS   On time
## 22:18  Bedwyn                                  BUS   On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:40  Basingstoke                             BUS   On time
## 22:47  Newbury                                 BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-07 20:05:08
## Time   To                                      Plat  Expected
## 19:50  London Paddington                       10    21:37
## 20:47  London Paddington                       10    Delayed
## 20:57  Weston-super-Mare                       8     21:15
## 21:01  Gatwick Airport                         6     21:13
##        via Guildford                           
## 21:07  Ealing Broadway                         15A   On time
## 21:11  London Paddington                       10    21:14
## 21:12  London Waterloo                         4     On time
## 21:13  Swansea                                 8     21:16
## 21:14  Didcot Parkway                          8B    On time
## 21:18  Great Malvern                           -     Cancelled
## 21:22  London Paddington                       11    21:38
## 21:23  Didcot Parkway                          14B   21:26
## 21:24  Ealing Broadway                         13    On time
## 21:26  London Paddington                       10    On time
## 21:27  Bristol Temple Meads                    8     On time
## 21:29  Plymouth                                8     On time
## 21:34  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:37  Ealing Broadway                         14A   On time
## 21:42  London Waterloo                         6     On time
## 21:43  London Paddington                       10A   On time
## 21:46  London Paddington                       11    21:58
## 21:48  Oxford                                  -     Cancelled
## 21:49  Didcot Parkway                          12B   On time
## 21:49  Ealing Broadway                         13    On time
## 21:53  Cheltenham Spa                          8B    On time
## 21:53  Southampton Central                     15A   On time
## 21:56  London Paddington                       10    Delayed
## 22:08  Ealing Broadway                         15A   On time
## 22:10  London Paddington                       10    22:15
## 22:12  London Waterloo                         5     On time
## 22:13  London Paddington                       11    On time
## 22:13  Swansea                                 8     On time
## 22:18  Didcot Parkway                          12B   On time
## 22:18  Worcester Shrub Hill                    -     Cancelled
## 22:22  Ealing Broadway                         14    On time
## 22:27  London Paddington                       -     Cancelled
## 22:27  Plymouth                                8     On time
##        via Bristol                             
## 22:35  London Paddington                       10    On time
## 22:42  London Waterloo                         4     On time
## 22:45  Oxford                                  -     Cancelled
## 22:46  London Paddington                       10    22:49
## 22:47  Didcot Parkway                          12B   On time
## 22:49  Southampton Central                     7A    On time
## 22:52  Ealing Broadway                         13    On time
## 22:57  Bristol Temple Meads                    8     On time
## 23:01  London Paddington                       -     Cancelled
## 21:10  Newbury                                 BUS   On time
## 21:38  Bramley (Hampshire)                     BUS   On time
## 21:40  Bedwyn                                  BUS   On time
## 21:55  Winchester                              BUS   On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
## 22:10  Bedwyn                                  BUS   On time
## 22:38  Bramley (Hampshire)                     BUS   On time
## 22:55  Winchester                              BUS   On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
```
