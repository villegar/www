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

## Example (Last rendered on 2023-04-09 18:03)

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
## Reading (RDG) Station Board on 2023-04-09 18:03:55
## Time   From                                    Plat  Expected
## 18:56  Bournemouth                             8     18:58
## 19:02  Weybridge                               4     19:05
## 19:07  London Paddington                       7     On time
## 19:10  Bristol Temple Meads                    10    19:20
## 19:11  Redhill                                 15    19:13
## 19:13  Didcot Parkway                          13    On time
## 19:13  London Paddington                       12    On time
## 19:25  Didcot Parkway                          10    On time
## 19:26  London Paddington                       8     On time
## 19:28  London Paddington                       14    On time
## 19:28  Penzance                                11    On time
## 19:32  Virginia Water                          4     On time
## 19:38  Gatwick Airport                         5     On time
## 19:39  London Paddington                       8     On time
## 19:47  London Paddington                       8     On time
## 19:49  Carmarthen                              11    On time
## 19:53  London Paddington                       8     On time
## 19:59  London Paddington                       14    On time
## 20:02  Weybridge                               4     On time
## 20:07  London Paddington                       8     On time
## 20:11  Bristol Temple Meads                    10    On time
## 20:11  Redhill                                 15    On time
## 20:13  Didcot Parkway                          13    On time
## 20:14  Penzance                                11    On time
## 20:19  London Paddington                       12    On time
## 20:24  Didcot Parkway                          10    On time
## 20:27  London Paddington                       8     On time
## 20:28  London Paddington                       14    On time
## 20:32  Virginia Water                          4     On time
## 20:38  Gatwick Airport                         5     On time
## 20:40  Didcot Parkway                          -     On time
## 20:47  London Paddington                       13    On time
## 20:49  Swansea                                 10    On time
## 20:53  London Paddington                       -     Cancelled
## 20:58  London Paddington                       14    On time
## 21:02  Weybridge                               6     On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:23  Bramley (Hampshire)                     BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
## 20:07  Bedwyn                                  BUS   On time
## 20:23  Basingstoke                             BUS   On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:51  Newbury                                 BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
## 21:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-09 18:04:01
## Time   To                                      Plat  Expected
## 19:10  Swansea                                 7     On time
## 19:11  London Paddington                       10    19:21
## 19:13  Ealing Broadway                         13    On time
## 19:15  Didcot Parkway                          8     On time
## 19:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:23  Ealing Broadway                         14    On time
## 19:24  Virginia Water                          4     On time
## 19:25  Didcot Parkway                          12    On time
## 19:25  Plymouth                                8     On time
## 19:26  London Paddington                       10    On time
## 19:28  Bristol Temple Meads                    8     On time
## 19:32  London Paddington                       11    On time
## 19:40  Swindon                                 8     On time
## 19:49  Didcot Parkway                          8     On time
## 19:50  London Paddington                       11    On time
## 19:53  Ealing Broadway                         14    On time
## 19:54  Weybridge                               4     On time
## 19:55  Bristol Temple Meads                    8     On time
## 20:09  Swansea                                 8     On time
## 20:12  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:14  Ealing Broadway                         13    On time
## 20:14  London Paddington                       10    On time
## 20:18  London Paddington                       11    On time
## 20:23  Ealing Broadway                         14    On time
## 20:24  Virginia Water                          4     On time
## 20:25  Didcot Parkway                          12    On time
## 20:27  London Paddington                       10    On time
## 20:28  Plymouth                                8     On time
## 20:46  Southampton Central                     -     On time
## 20:50  London Paddington                       10    On time
## 20:53  Ealing Broadway                         14    On time
## 20:54  Weybridge                               4     On time
## 20:55  Weston-super-Mare                       -     Cancelled
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:38  Bramley (Hampshire)                     BUS   On time
## 19:43  Bedwyn                                  BUS   On time
## 19:52  Winchester                              BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 20:38  Bramley (Hampshire)                     BUS   On time
## 20:43  Newbury                                 BUS   On time
## 20:52  Winchester                              BUS   On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
```
