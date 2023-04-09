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

## Example (Last rendered on 2023-04-09 10:03)

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
## Reading (RDG) Station Board on 2023-04-09 10:04:01
## Time   From                                    Plat  Expected
## 10:53  London Paddington                       8     10:57
## 10:57  Southampton Central                     7     11:00
## 11:02  Weybridge                               4     11:05
## 11:07  London Paddington                       8     On time
## 11:09  Bristol Temple Meads                    10A   11:14
## 11:10  Didcot Parkway                          15    On time
## 11:10  Redhill                                 6     11:12
## 11:15  London Paddington                       12    On time
## 11:15  Swansea                                 11    On time
## 11:28  London Paddington                       14    On time
## 11:32  Virginia Water                          4     On time
## 11:38  Gatwick Airport                         5     On time
## 11:44  Swansea                                 11    On time
## 11:47  London Paddington                       13    On time
## 11:48  Plymouth                                10    On time
## 11:53  London Paddington                       8     On time
## 11:58  London Paddington                       14    On time
## 12:02  Weybridge                               4     On time
## 12:07  London Paddington                       8     On time
## 12:07  Plymouth                                11    On time
## 12:10  Didcot Parkway                          15    On time
## 12:10  Redhill                                 6     On time
## 12:13  London Paddington                       12    On time
## 12:15  Bristol Temple Meads                    10    On time
## 12:25  Didcot Parkway                          10    On time
## 12:28  London Paddington                       14    On time
## 12:31  Cheltenham Spa                          10    On time
## 12:32  Virginia Water                          4     On time
## 12:38  Gatwick Airport                         5     On time
## 12:40  Didcot Parkway                          7     On time
## 12:44  Swansea                                 10    On time
## 12:47  London Paddington                       13    On time
## 12:52  Bournemouth                             13    On time
## 12:53  London Paddington                       8     On time
## 12:58  London Paddington                       14    On time
## 13:02  Weybridge                               4     On time
## 11:04  Heathrow Central Bus Stn                BUS   On time
## 11:08  Bedwyn                                  BUS   On time
## 11:34  Andover                                 BUS   On time
## 11:34  Heathrow Central Bus Stn                BUS   On time
## 12:04  Heathrow Central Bus Stn                BUS   On time
## 12:07  Bedwyn                                  BUS   On time
## 12:23  Basingstoke                             BUS   On time
## 12:34  Andover                                 -     Cancelled
## 12:34  Heathrow Central Bus Stn                BUS   On time
## 12:51  Newbury                                 BUS   On time
## 13:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-09 10:04:07
## Time   To                                      Plat  Expected
## 10:55  Bristol Temple Meads                    8     11:02
## 11:03  Plymouth                                8     11:05
## 11:10  Swansea                                 8     On time
## 11:11  London Paddington                       10A   11:15
## 11:14  Ealing Broadway                         15    On time
## 11:15  Didcot Parkway                          7     On time
## 11:16  London Paddington                       11    On time
## 11:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:23  Ealing Broadway                         -     Cancelled
## 11:24  Virginia Water                          4     On time
## 11:26  Didcot Parkway                          12    On time
## 11:41  Redhill                                 6     On time
## 11:45  London Paddington                       11    On time
## 11:49  Didcot Parkway                          13    On time
## 11:50  London Paddington                       10    On time
## 11:53  Ealing Broadway                         14    On time
## 11:54  Weybridge                               4     On time
## 11:55  Bristol Temple Meads                    8     On time
## 12:03  Penzance                                9     On time
## 12:10  Carmarthen                              8     On time
## 12:10  London Paddington                       11    On time
## 12:14  Ealing Broadway                         15    On time
## 12:16  London Paddington                       10    On time
## 12:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 12:23  Ealing Broadway                         14    On time
## 12:24  Virginia Water                          4     On time
## 12:26  Didcot Parkway                          12    On time
## 12:26  London Paddington                       10    On time
## 12:33  London Paddington                       10    On time
## 12:41  Redhill                                 6     On time
## 12:46  Bournemouth                             15    On time
## 12:46  Bournemouth                             7     On time
## 12:46  London Paddington                       10    On time
## 12:49  Didcot Parkway                          13    On time
## 12:53  Ealing Broadway                         14    On time
## 12:54  Weybridge                               4     On time
## 12:55  Bristol Temple Meads                    8     On time
## 13:03  Plymouth                                9     On time
## 11:30  Andover                                 BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:38  Bramley (Hampshire)                     BUS   On time
## 11:43  Bedwyn                                  BUS   On time
## 11:52  Winchester                              BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
## 12:30  Andover                                 BUS   On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:38  Basingstoke                             BUS   On time
## 12:43  Newbury                                 BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
```
