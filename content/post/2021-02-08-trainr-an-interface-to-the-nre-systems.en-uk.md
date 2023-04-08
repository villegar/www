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

## Example (Last rendered on 2023-04-08 08:03)

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
## Reading (RDG) Station Board on 2023-04-08 08:04:01
## Time   From                                    Plat  Expected
## 08:52  London Paddington                       8     On time
## 08:55  London Paddington                       8B    Delayed
## 08:56  Didcot Parkway                          7A    Delayed
## 09:01  Didcot Parkway                          15    On time
## 09:06  Southampton Central                     13B   09:08
## 09:10  London Paddington                       12    On time
## 09:10  Taunton                                 10    09:14
## 09:11  London Paddington                       8     On time
## 09:13  London Waterloo                         4     On time
## 09:16  Swansea                                 11    09:21
## 09:17  London Paddington                       -     Cancelled
## 09:19  Plymouth                                10    On time
## 09:25  London Paddington                       8     On time
## 09:28  Didcot Parkway                          10A   On time
## 09:31  Didcot Parkway                          15    On time
## 09:33  Cheltenham Spa                          11    On time
## 09:33  London Paddington                       14    On time
## 09:33  London Paddington                       10    On time
## 09:33  Redhill                                 5     On time
## 09:41  Bristol Temple Meads                    11    On time
## 09:43  London Paddington                       12    On time
## 09:43  London Waterloo                         6     On time
## 09:46  Swansea                                 10    09:48
## 09:47  London Paddington                       8     On time
## 09:51  Gatwick Airport                         4     On time
## 09:51  London Paddington                       8B    On time
## 09:54  Hereford                                -     Cancelled
## 09:55  London Paddington                       8     On time
## 10:00  Plymouth                                11    On time
## 10:01  Didcot Parkway                          15    On time
## 10:03  London Paddington                       14    On time
## 10:10  Exeter St Davids                        10    On time
## 10:10  London Paddington                       12    On time
## 10:11  London Paddington                       7     On time
## 10:13  London Waterloo                         5     On time
## 10:14  Worcester Foregate Street               -     Cancelled
## 10:17  London Paddington                       -     Cancelled
## 10:17  Swansea                                 10    On time
## 10:20  Plymouth                                11    On time
## 10:25  London Paddington                       7     On time
## 10:28  Didcot Parkway                          10    On time
## 10:31  Didcot Parkway                          15    On time
## 10:32  Cheltenham Spa                          10A   On time
## 10:33  London Paddington                       14    On time
## 10:33  Redhill                                 4     On time
## 10:41  Bristol Temple Meads                    10    On time
## 10:43  London Paddington                       12    On time
## 10:43  London Waterloo                         6     On time
## 10:46  Carmarthen                              -     Cancelled
## 10:47  London Paddington                       9     On time
## 10:51  Gatwick Airport                         5     On time
## 10:51  London Paddington                       8     On time
## 10:54  Great Malvern                           -     Cancelled
## 10:55  London Paddington                       9     On time
## 10:56  Didcot Parkway                          7     On time
## 11:01  Bournemouth                             13B   On time
## 09:04  Heathrow Central Bus Stn                BUS   On time
## 09:21  Bedwyn                                  BUS   On time
## 09:34  Heathrow Central Bus Stn                BUS   On time
## 09:40  Bramley (Hampshire)                     BUS   On time
## 09:47  Newbury                                 BUS   On time
## 10:00  Newbury                                 BUS   On time
## 10:01  Basingstoke                             BUS   On time
## 10:04  Heathrow Central Bus Stn                BUS   On time
## 10:21  Bedwyn                                  BUS   On time
## 10:34  Heathrow Central Bus Stn                BUS   On time
## 10:40  Bramley (Hampshire)                     BUS   On time
## 10:47  Newbury                                 BUS   On time
## 11:00  Newbury                                 BUS   On time
## 11:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-08 08:04:10
## Time   To                                      Plat  Expected
## 08:54  Cheltenham Spa                          8     Delayed
## 08:56  Bournemouth                             7A    Delayed
## 08:59  Taunton                                 8B    Delayed
## 09:09  London Waterloo                         6     On time
## 09:09  Plymouth                                8     On time
## 09:12  London Paddington                       10    09:15
## 09:13  Swansea                                 8     On time
## 09:15  Ealing Broadway                         15    On time
## 09:17  London Paddington                       11    09:22
## 09:20  Great Malvern                           -     Cancelled
## 09:20  London Paddington                       10    On time
## 09:20  Redhill                                 5     On time
## 09:24  Didcot Parkway                          12    On time
## 09:24  Ealing Broadway                         14    On time
## 09:27  Bristol Temple Meads                    8     On time
## 09:31  London Paddington                       10A   On time
## 09:35  London Paddington                       11    On time
## 09:39  London Waterloo                         4     On time
## 09:40  London Paddington                       10    On time
## 09:43  London Paddington                       11    On time
## 09:45  Ealing Broadway                         15    On time
## 09:48  London Paddington                       10    09:48
## 09:49  Didcot Parkway                          8     On time
## 09:53  Cheltenham Spa                          8B    On time
## 09:53  Didcot Parkway                          12    On time
## 09:54  Ealing Broadway                         14    On time
## 09:56  London Paddington                       -     Cancelled
## 09:58  Bristol Temple Meads                    8     On time
## 10:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:04  London Paddington                       11    On time
## 10:09  London Waterloo                         6     On time
## 10:09  Penzance                                8     On time
## 10:12  London Paddington                       10    On time
## 10:13  Swansea                                 7     On time
## 10:15  Ealing Broadway                         15    On time
## 10:15  London Paddington                       -     Cancelled
## 10:18  London Paddington                       10    On time
## 10:19  Hereford                                -     Cancelled
## 10:20  Redhill                                 4     On time
## 10:24  Didcot Parkway                          12    On time
## 10:24  Ealing Broadway                         14    On time
## 10:24  London Paddington                       11    On time
## 10:27  Bristol Temple Meads                    7     On time
## 10:30  London Paddington                       10    On time
## 10:35  London Paddington                       10A   On time
## 10:39  London Waterloo                         5     On time
## 10:43  London Paddington                       10    On time
## 10:45  Ealing Broadway                         15    On time
## 10:48  London Paddington                       -     Cancelled
## 10:49  Didcot Parkway                          9     On time
## 10:52  Didcot Parkway                          12    On time
## 10:53  Cheltenham Spa                          8     On time
## 10:54  Ealing Broadway                         14    On time
## 10:56  Bournemouth                             7     On time
## 10:56  London Paddington                       -     Cancelled
## 10:57  Weston-super-Mare                       9     On time
## 11:01  Didcot Parkway                          13B   On time
## 11:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 09:10  Newbury                                 BUS   On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:38  Bramley (Hampshire)                     BUS   On time
## 09:40  Bedwyn                                  BUS   On time
## 09:44  Newbury                                 BUS   On time
## 10:00  Basingstoke                             BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
## 10:10  Newbury                                 BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:38  Bramley (Hampshire)                     BUS   On time
## 10:40  Bedwyn                                  BUS   On time
## 10:44  Newbury                                 BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
## 11:00  Winchester                              BUS   On time
```
