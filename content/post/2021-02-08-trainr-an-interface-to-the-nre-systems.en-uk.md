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

## Example (Last rendered on 2023-04-08 16:03)

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
## Reading (RDG) Station Board on 2023-04-08 16:03:57
## Time   From                                    Plat  Expected
## 16:51  London Paddington                       8B    On time
## 17:01  Didcot Parkway                          15    On time
## 17:02  Bournemouth                             -     17:18
## 17:03  London Paddington                       14    On time
## 17:10  Bristol Temple Meads                    10    On time
## 17:11  London Paddington                       7     On time
## 17:11  London Paddington                       12    17:23
## 17:13  London Waterloo                         4     On time
## 17:15  Penzance                                11    17:25
## 17:17  London Paddington                       -     Cancelled
## 17:25  London Paddington                       8     17:39
## 17:28  Didcot Parkway                          10    On time
## 17:31  Didcot Parkway                          15    On time
## 17:33  Cheltenham Spa                          -     Cancelled
## 17:33  London Paddington                       14    On time
## 17:33  Redhill                                 5     On time
## 17:40  Weston-super-Mare                       11    On time
## 17:41  London Paddington                       8     On time
## 17:43  London Paddington                       12    On time
## 17:43  London Waterloo                         6     On time
## 17:47  London Paddington                       8     On time
## 17:47  Swansea                                 10    On time
## 17:51  London Paddington                       7     On time
## 17:51  Redhill                                 4     On time
## 17:54  Hereford                                -     Cancelled
## 17:55  London Paddington                       8     On time
## 18:01  Didcot Parkway                          15    On time
## 18:03  London Paddington                       14    On time
## 18:10  Bristol Temple Meads                    10    On time
## 18:10  London Paddington                       12    On time
## 18:11  London Paddington                       8     On time
## 18:13  London Waterloo                         5     On time
## 18:17  London Paddington                       -     Cancelled
## 18:22  Bristol Parkway                         11    On time
## 18:24  London Paddington                       13    On time
## 18:28  Didcot Parkway                          10    On time
## 18:28  London Paddington                       7     On time
## 18:31  Didcot Parkway                          15    On time
## 18:33  Cheltenham Spa                          10    On time
## 18:33  London Paddington                       14    On time
## 18:33  Redhill                                 4     On time
## 18:36  Plymouth                                11    18:44
## 18:41  London Paddington                       8     On time
## 18:42  Didcot Parkway                          -     On time
## 18:42  Weston-super-Mare                       10    On time
## 18:43  London Paddington                       12    On time
## 18:43  London Waterloo                         6     On time
## 18:46  Swansea                                 11    On time
## 18:47  London Paddington                       8     On time
## 18:51  Gatwick Airport                         5     On time
## 18:51  London Paddington                       8     On time
## 18:54  Great Malvern                           -     Cancelled
## 18:55  London Paddington                       8     On time
## 19:01  Bournemouth                             13B   On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
## 17:21  Bedwyn                                  BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
## 17:40  Bramley (Hampshire)                     BUS   On time
## 17:47  Newbury                                 BUS   On time
## 18:00  Newbury                                 BUS   On time
## 18:01  Basingstoke                             BUS   On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:21  Bedwyn                                  BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 18:40  Bramley (Hampshire)                     BUS   On time
## 18:47  Newbury                                 BUS   On time
## 19:00  Newbury                                 BUS   On time
## 19:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-08 16:04:03
## Time   To                                      Plat  Expected
## 16:54  Cheltenham Spa                          8B    Delayed
## 17:09  London Waterloo                         6     On time
## 17:09  Penzance                                7     On time
## 17:13  Swansea                                 7     On time
## 17:14  London Paddington                       10    On time
## 17:15  Didcot Parkway                          -     17:19
## 17:16  London Paddington                       11    17:26
## 17:19  Hereford                                -     Cancelled
## 17:20  Ealing Broadway                         15    On time
## 17:20  Redhill                                 5     On time
## 17:23  Didcot Parkway                          12    17:23
## 17:24  Ealing Broadway                         14    On time
## 17:27  Bristol Temple Meads                    8     17:40
## 17:30  London Paddington                       10    On time
## 17:35  London Paddington                       -     Cancelled
## 17:39  London Waterloo                         4     On time
## 17:42  London Paddington                       11    On time
## 17:43  Carmarthen                              8     On time
## 17:45  Ealing Broadway                         15    On time
## 17:48  London Paddington                       10    On time
## 17:50  Didcot Parkway                          8     On time
## 17:54  Cheltenham Spa                          7     On time
## 17:54  Ealing Broadway                         14    On time
## 17:55  Didcot Parkway                          12    On time
## 17:56  London Paddington                       -     Cancelled
## 18:00  Weston-super-Mare                       8     On time
## 18:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:09  London Waterloo                         6     On time
## 18:12  London Paddington                       10    On time
## 18:13  Swansea                                 8     On time
## 18:15  Ealing Broadway                         15    On time
## 18:19  Worcester Foregate Street               -     Cancelled
## 18:23  Didcot Parkway                          12    On time
## 18:24  Ealing Broadway                         14    On time
## 18:24  London Paddington                       11    On time
## 18:27  Penzance                                8     On time
## 18:30  Bristol Temple Meads                    7     On time
## 18:30  London Paddington                       10    On time
## 18:35  London Paddington                       10    On time
## 18:36  Redhill                                 6     On time
## 18:39  London Waterloo                         5     On time
## 18:40  London Paddington                       11    18:45
## 18:44  London Paddington                       10    On time
## 18:44  Swansea                                 8     On time
## 18:45  Ealing Broadway                         15    On time
## 18:49  Didcot Parkway                          8     On time
## 18:50  London Paddington                       11    On time
## 18:53  Cheltenham Spa                          8     On time
## 18:53  Didcot Parkway                          12    On time
## 18:54  Ealing Broadway                         14    On time
## 18:56  Bournemouth                             -     On time
## 18:56  London Paddington                       -     Cancelled
## 18:57  Taunton                                 8     On time
## 19:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:10  Newbury                                 BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:38  Bramley (Hampshire)                     BUS   On time
## 17:40  Bedwyn                                  BUS   On time
## 17:44  Newbury                                 BUS   On time
## 17:55  Basingstoke                             BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:10  Newbury                                 BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:38  Bramley (Hampshire)                     BUS   On time
## 18:40  Bedwyn                                  BUS   On time
## 18:44  Newbury                                 BUS   On time
## 18:55  Winchester                              BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
```
