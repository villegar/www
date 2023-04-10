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

## Example (Last rendered on 2023-04-10 16:03)

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
## Reading (RDG) Station Board on 2023-04-10 16:03:40
## Time   From                                    Plat  Expected
## 16:45  Swansea                                 10    17:46
## 16:59  London Paddington                       9     17:02
## 17:03  Didcot Parkway                          15A   On time
## 17:03  Gatwick Airport                         5     On time
## 17:09  Bournemouth                             7B    On time
## 17:09  Bristol Temple Meads                    11    17:14
## 17:11  London Paddington                       9     On time
## 17:17  Cardiff Central                         11    17:27
## 17:20  London Waterloo                         4     On time
## 17:22  London Paddington                       12    On time
## 17:24  Didcot Parkway                          10A   On time
## 17:25  London Paddington                       8     On time
## 17:29  Cheltenham Spa                          10A   On time
## 17:33  Penzance                                11    18:05
## 17:35  Didcot Parkway                          15A   On time
## 17:35  Redhill                                 5     On time
## 17:36  London Paddington                       14    On time
## 17:38  Bristol Temple Meads                    10    On time
## 17:41  London Paddington                       9     On time
## 17:41  London Waterloo                         6     17:43
## 17:48  Swansea                                 10    Delayed
## 17:53  London Paddington                       8     On time
## 17:54  London Paddington                       12    On time
## 17:57  Hereford                                10A   On time
## 17:58  London Paddington                       9B    On time
## 18:02  Gatwick Airport                         5     On time
## 18:02  London Paddington                       8     On time
## 18:03  Didcot Parkway                          15A   On time
## 18:03  London Paddington                       14    On time
## 18:09  Bristol Temple Meads                    11    On time
## 18:11  London Paddington                       -     Cancelled
## 18:11  London Waterloo                         4     On time
## 18:17  Cardiff Central                         11A   On time
## 18:25  London Paddington                       8     On time
## 18:28  Didcot Parkway                          15A   On time
## 18:30  Cheltenham Spa                          11A   On time
## 18:30  London Paddington                       12    On time
## 18:33  London Paddington                       14    On time
## 18:33  Redhill                                 5     On time
## 18:34  Plymouth                                10    On time
## 18:40  Bristol Temple Meads                    11    On time
## 18:40  Didcot Parkway                          15A   On time
## 18:41  London Waterloo                         6     On time
## 18:42  London Paddington                       9     On time
## 18:48  Swansea                                 10    On time
## 18:53  London Paddington                       8     On time
## 18:53  London Paddington                       12    On time
## 18:59  London Paddington                       -     Cancelled
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
## Reading (RDG) Station Board on 2023-04-10 16:03:46
## Time   To                                      Plat  Expected
## 16:47  London Paddington                       10    17:47
## 17:02  Penzance                                9     17:03
## 17:11  Ealing Broadway                         15A   On time
## 17:11  London Paddington                       11    17:15
## 17:12  London Waterloo                         6     On time
## 17:13  Swansea                                 9     On time
## 17:15  Didcot Parkway                          7B    On time
## 17:18  London Paddington                       11    17:28
## 17:20  Redhill                                 5     On time
## 17:24  Ealing Broadway                         14A   On time
## 17:25  Didcot Parkway                          12    On time
## 17:27  Bristol Temple Meads                    8     On time
## 17:27  London Paddington                       10A   On time
## 17:32  London Paddington                       10A   On time
## 17:36  London Paddington                       -     Cancelled
## 17:41  London Paddington                       10    On time
## 17:42  Ealing Broadway                         15A   On time
## 17:42  London Waterloo                         4     On time
## 17:43  Swansea                                 9     On time
## 17:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:50  London Paddington                       10    Delayed
## 17:52  Cheltenham Spa                          9B    On time
## 17:54  Ealing Broadway                         14A   On time
## 17:57  Taunton                                 8     On time
## 17:58  Didcot Parkway                          12    On time
## 18:00  Hereford                                9B    On time
## 18:00  London Paddington                       10A   On time
## 18:02  Penzance                                8     On time
## 18:08  Ealing Broadway                         15A   On time
## 18:12  London Paddington                       11    On time
## 18:12  London Waterloo                         6     On time
## 18:13  Carmarthen                              -     Cancelled
## 18:20  London Paddington                       11A   On time
## 18:20  Redhill                                 5     On time
## 18:24  Ealing Broadway                         14A   On time
## 18:27  Bristol Temple Meads                    8     On time
## 18:32  Didcot Parkway                          12    On time
## 18:32  London Paddington                       11A   On time
## 18:37  Ealing Broadway                         15A   On time
## 18:40  London Paddington                       10    On time
## 18:42  London Waterloo                         4     On time
## 18:43  London Paddington                       11    On time
## 18:43  Swansea                                 9     On time
## 18:50  London Paddington                       10    On time
## 18:53  Bournemouth                             15A   On time
## 18:54  Ealing Broadway                         14A   On time
## 18:56  Cheltenham Spa                          8     On time
## 18:57  Didcot Parkway                          12    On time
## 19:00  Weston-super-Mare                       9B    On time
## 19:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:01  Plymouth                                -     On time
## 17:10  Newbury                                 BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:38  Bramley (Hampshire)                     BUS   On time
## 17:40  Bedwyn                                  BUS   On time
## 17:44  Newbury                                 BUS   On time
## 17:55  Winchester                              BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:10  Newbury                                 -     Cancelled
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:38  Bramley (Hampshire)                     BUS   On time
## 18:40  Bedwyn                                  BUS   On time
## 18:44  Newbury                                 BUS   On time
## 18:55  Basingstoke                             BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
```
