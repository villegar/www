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

## Example (Last rendered on 2023-04-09 20:03)

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
## Reading (RDG) Station Board on 2023-04-09 20:03:58
## Time   From                                    Plat  Expected
## 20:57  Bournemouth                             8     20:51
## 21:02  Weybridge                               6     21:11
## 21:07  London Paddington                       7     On time
## 21:11  Bristol Temple Meads                    -     Cancelled
## 21:11  Redhill                                 15B   On time
## 21:12  London Paddington                       12    On time
## 21:13  Didcot Parkway                          13    On time
## 21:26  London Paddington                       7     On time
## 21:27  Penzance                                11    21:29
## 21:28  London Paddington                       14    On time
## 21:32  Virginia Water                          4     On time
## 21:40  Didcot Parkway                          -     On time
## 21:40  Gatwick Airport                         15    On time
## 21:42  London Paddington                       13    On time
## 21:49  Swansea                                 10    On time
## 21:53  London Paddington                       8     On time
## 21:58  London Paddington                       14    On time
## 22:02  Weybridge                               4     On time
## 22:07  London Paddington                       9     On time
## 22:10  Bristol Temple Meads                    10    On time
## 22:10  London Paddington                       12    On time
## 22:13  Didcot Parkway                          13    On time
## 22:32  London Paddington                       14    On time
## 22:32  Virginia Water                          4     On time
## 22:37  Henley-on-Thames                        12    On time
## 22:38  London Paddington                       9     On time
## 22:45  Gatwick Airport                         15B   On time
## 22:49  Carmarthen                              10    On time
## 22:59  London Paddington                       10    On time
## 23:02  Weybridge                               4     On time
## 21:23  Bramley (Hampshire)                     BUS   On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
## 22:07  Bedwyn                                  BUS   On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:23  Basingstoke                             BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
## 22:54  Newbury                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-09 20:04:03
## Time   To                                      Plat  Expected
## 21:09  Swansea                                 7     On time
## 21:11  London Paddington                       -     Cancelled
## 21:12  Didcot Parkway                          8     On time
## 21:13  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:14  Didcot Parkway                          12    On time
## 21:14  Ealing Broadway                         13    On time
## 21:24  Ealing Broadway                         14    On time
## 21:28  London Paddington                       11    21:30
## 21:30  Exeter St Davids                        7     On time
## 21:46  Southampton Central                     -     On time
## 21:50  London Paddington                       10    On time
## 21:54  Ealing Broadway                         14    On time
## 21:54  Weybridge                               4     On time
## 21:55  Bristol Temple Meads                    8     On time
## 22:09  Cardiff Central                         9     On time
## 22:11  London Paddington                       10    On time
## 22:12  Didcot Parkway                          12    On time
## 22:24  Virginia Water                          4     On time
## 22:28  Ealing Broadway                         14    On time
## 22:39  Bristol Temple Meads                    9     On time
## 22:52  Ealing Broadway                         14    On time
## 22:54  Weybridge                               4     On time
## 22:55  London Paddington                       10    On time
## 23:03  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:38  Bramley (Hampshire)                     BUS   On time
## 21:43  Bedwyn                                  BUS   On time
## 21:52  Winchester                              BUS   On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
## 22:46  Newbury                                 BUS   On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
```
