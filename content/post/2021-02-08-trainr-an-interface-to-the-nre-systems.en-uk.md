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

## Example (Last rendered on 2023-04-08 20:05)

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
## Reading (RDG) Station Board on 2023-04-08 20:05:12
## Time   From                                    Plat  Expected
## 20:58  Gatwick Airport                         15    21:05
## 21:01  Bournemouth                             13B   21:17
## 21:03  London Paddington                       14    On time
## 21:04  Didcot Parkway                          15    21:01
## 21:10  Bristol Temple Meads                    10    21:19
## 21:10  London Paddington                       12    On time
## 21:11  London Paddington                       9     On time
## 21:13  London Waterloo                         6     On time
## 21:25  Didcot Parkway                          10    On time
## 21:28  Penzance                                11    On time
## 21:31  Didcot Parkway                          13    On time
## 21:33  London Paddington                       14    On time
## 21:36  Cheltenham Spa                          10A   On time
## 21:36  London Paddington                       12    On time
## 21:42  London Waterloo                         5     On time
## 21:45  London Paddington                       13    On time
## 21:49  Swansea                                 10    21:54
## 21:51  London Paddington                       8     On time
## 21:51  Redhill                                 15B   On time
## 21:54  Worcester Foregate Street               -     Cancelled
## 21:56  London Paddington                       8     On time
## 21:58  Redhill                                 15    On time
## 22:03  London Paddington                       14    On time
## 22:09  Taunton                                 10    On time
## 22:10  London Paddington                       12    On time
## 22:13  London Waterloo                         4     On time
## 22:17  London Paddington                       -     Cancelled
## 22:25  London Paddington                       8B    On time
## 22:26  Gatwick Airport                         13    22:36
## 22:27  Didcot Parkway                          15    On time
## 22:29  Didcot Parkway                          11    On time
## 22:33  London Paddington                       14    On time
## 22:36  Cheltenham Spa                          10A   On time
## 22:40  London Paddington                       12    On time
## 22:43  Didcot Parkway                          -     On time
## 22:43  London Waterloo                         5     On time
## 22:51  London Paddington                       10    On time
## 22:54  London Paddington                       9     On time
## 23:03  London Paddington                       10    On time
## 23:04  Redhill                                 15    23:11
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
## Reading (RDG) Station Board on 2023-04-08 20:05:18
## Time   To                                      Plat  Expected
## 21:09  London Waterloo                         4     On time
## 21:13  London Paddington                       10    21:20
## 21:13  Swansea                                 9     On time
## 21:15  Didcot Parkway                          13B   21:18
## 21:15  Ealing Broadway                         15    On time
## 21:21  Didcot Parkway                          12    On time
## 21:24  Ealing Broadway                         14    On time
## 21:26  London Paddington                       10    On time
## 21:30  London Paddington                       11    On time
## 21:33  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:39  London Waterloo                         6     On time
## 21:40  London Paddington                       10A   On time
## 21:41  Ealing Broadway                         13    On time
## 21:51  London Paddington                       10    21:55
## 21:52  Ealing Broadway                         14    On time
## 21:53  Didcot Parkway                          8     On time
## 21:56  London Paddington                       -     Cancelled
## 21:57  Bristol Temple Meads                    8     On time
## 21:57  Southampton Central                     -     Cancelled
## 22:09  London Waterloo                         5     On time
## 22:15  London Paddington                       10    On time
## 22:16  Ealing Broadway                         13    On time
## 22:19  Worcester Shrub Hill                    -     Cancelled
## 22:22  Ealing Broadway                         14    On time
## 22:27  Bristol Parkway                         8B    On time
## 22:30  Didcot Parkway                          12    On time
## 22:34  London Paddington                       11    On time
## 22:39  London Paddington                       10A   On time
## 22:39  London Waterloo                         4     On time
## 22:52  Ealing Broadway                         14    On time
## 22:55  Southampton Central                     -     On time
## 22:56  Bristol Temple Meads                    9     On time
## 23:01  Didcot Parkway                          12    On time
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
