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

## Example (Last rendered on 2023-04-08 14:04)

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
## Reading (RDG) Station Board on 2023-04-08 14:04:31
## Time   From                                    Plat  Expected
## 14:51  Redhill                                 5     15:06
## 15:01  Didcot Parkway                          15    14:58
## 15:02  Bournemouth                             7     15:16
## 15:10  Bristol Temple Meads                    10    On time
## 15:11  London Paddington                       8     On time
## 15:11  London Paddington                       12    On time
## 15:13  London Waterloo                         4     15:15
## 15:15  Penzance                                11    On time
## 15:17  London Paddington                       -     Cancelled
## 15:25  London Paddington                       8     On time
## 15:28  Didcot Parkway                          10    On time
## 15:31  Didcot Parkway                          15    On time
## 15:33  Cheltenham Spa                          10    On time
## 15:33  London Paddington                       14    On time
## 15:33  Redhill                                 5     On time
## 15:38  London Paddington                       8     On time
## 15:40  Weston-super-Mare                       11    On time
## 15:43  London Paddington                       12    On time
## 15:43  London Waterloo                         6     On time
## 15:47  London Paddington                       8     On time
## 15:47  Swansea                                 10    On time
## 15:51  Redhill                                 4     On time
## 15:53  Hereford                                -     Cancelled
## 15:55  London Paddington                       8     On time
## 16:00  Didcot Parkway                          15    On time
## 16:03  London Paddington                       14    On time
## 16:10  Bristol Temple Meads                    10    On time
## 16:11  London Paddington                       8     On time
## 16:11  London Paddington                       12    On time
## 16:13  London Waterloo                         5     On time
## 16:17  London Paddington                       -     Cancelled
## 16:19  Cardiff Central                         10    On time
## 16:25  London Paddington                       8     On time
## 16:28  Didcot Parkway                          11    On time
## 16:28  Plymouth                                10    16:34
## 16:31  Didcot Parkway                          15    On time
## 16:33  London Paddington                       14    On time
## 16:33  Redhill                                 4     On time
## 16:40  Weston-super-Mare                       10    On time
## 16:41  London Paddington                       8     On time
## 16:42  Didcot Parkway                          13    On time
## 16:43  London Paddington                       12    On time
## 16:43  London Waterloo                         6     On time
## 16:46  Swansea                                 10    On time
## 16:47  London Paddington                       8     On time
## 16:51  Gatwick Airport                         5     On time
## 16:51  London Paddington                       8     On time
## 16:54  Great Malvern                           -     Cancelled
## 16:54  London Paddington                       7     On time
## 17:03  London Paddington                       14    On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
## 15:21  Bedwyn                                  BUS   On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
## 15:40  Bramley (Hampshire)                     BUS   On time
## 15:47  Newbury                                 BUS   On time
## 16:00  Newbury                                 BUS   On time
## 16:01  Basingstoke                             BUS   On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:21  Bedwyn                                  BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 16:40  Bramley (Hampshire)                     BUS   On time
## 16:47  Newbury                                 BUS   On time
## 17:00  Newbury                                 BUS   On time
## 17:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-08 14:04:35
## Time   To                                      Plat  Expected
## 15:09  London Waterloo                         6     On time
## 15:09  Penzance                                8     On time
## 15:12  London Paddington                       10    On time
## 15:13  Swansea                                 8     On time
## 15:15  Ealing Broadway                         15    On time
## 15:16  London Paddington                       11    On time
## 15:19  Great Malvern                           -     Cancelled
## 15:20  Redhill                                 5     On time
## 15:24  Didcot Parkway                          12    On time
## 15:24  Ealing Broadway                         14    On time
## 15:27  Bristol Temple Meads                    8     On time
## 15:30  London Paddington                       10    On time
## 15:35  London Paddington                       10    On time
## 15:39  London Waterloo                         4     On time
## 15:40  Bristol Parkway                         8     On time
## 15:43  London Paddington                       11    On time
## 15:45  Ealing Broadway                         15    On time
## 15:49  Didcot Parkway                          8     On time
## 15:50  London Paddington                       10    On time
## 15:53  Didcot Parkway                          12    On time
## 15:54  Ealing Broadway                         14    On time
## 15:57  Weston-super-Mare                       8     On time
## 15:58  London Paddington                       -     Cancelled
## 16:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:09  London Waterloo                         6     On time
## 16:09  Plymouth                                8     On time
## 16:12  London Paddington                       10    On time
## 16:13  Swansea                                 8     On time
## 16:15  Ealing Broadway                         15    On time
## 16:19  Great Malvern                           -     Cancelled
## 16:20  London Paddington                       10    On time
## 16:20  Redhill                                 4     On time
## 16:23  Didcot Parkway                          12    On time
## 16:24  Ealing Broadway                         14    On time
## 16:27  Bristol Temple Meads                    8     On time
## 16:29  London Paddington                       11    On time
## 16:32  London Paddington                       10    16:35
## 16:39  London Waterloo                         5     On time
## 16:42  London Paddington                       10    On time
## 16:43  Cardiff Central                         8     On time
## 16:45  Ealing Broadway                         15    On time
## 16:48  London Paddington                       10    On time
## 16:49  Didcot Parkway                          8     On time
## 16:53  Bournemouth                             13    On time
## 16:53  Didcot Parkway                          12    On time
## 16:54  Cheltenham Spa                          8     On time
## 16:54  Ealing Broadway                         14    On time
## 16:56  London Paddington                       -     Cancelled
## 16:58  Taunton                                 7     On time
## 17:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 15:10  Newbury                                 BUS   On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:38  Bramley (Hampshire)                     BUS   On time
## 15:40  Bedwyn                                  BUS   On time
## 15:44  Newbury                                 BUS   On time
## 15:55  Basingstoke                             BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
## 16:10  Newbury                                 BUS   On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:38  Bramley (Hampshire)                     BUS   On time
## 16:40  Bedwyn                                  BUS   On time
## 16:44  Newbury                                 BUS   On time
## 16:55  Winchester                              BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
```
