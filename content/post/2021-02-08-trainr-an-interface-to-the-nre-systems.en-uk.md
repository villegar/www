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

## Example (Last rendered on 2023-04-07 22:03)

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
## Reading (RDG) Station Board on 2023-04-07 22:03:47
## Time   From                                    Plat  Expected
## 22:26  London Paddington                       8     23:02
## 22:43  Swansea                                 10    23:17
## 22:59  Worcester Foregate Street               -     Cancelled
## 23:04  London Paddington                       13    23:24
## 23:11  London Waterloo                         4     On time
## 23:11  Penzance                                15    00:20
## 23:13  London Paddington                       14    On time
## 23:18  London Paddington                       8     On time
## 23:20  Redhill                                 15A   On time
## 23:25  Didcot Parkway                          13A   On time
## 23:27  London Paddington                       -     Cancelled
## 23:34  London Paddington                       14    23:39
## 23:35  Didcot Parkway                          13    On time
## 23:41  London Waterloo                         6     23:50
## 23:46  Didcot Parkway                          15    On time
## 23:49  Manchester Piccadilly                   -     Cancelled
## 23:51  Bristol Temple Meads                    14    On time
## 00:03  London Paddington                       13    00:25
## 00:12  London Waterloo                         6     On time
## 00:17  Gatwick Airport                         15B   On time
## 00:23  London Paddington                       13B   On time
## 00:40  Henley-on-Thames                        14    On time
## 00:41  Hereford                                -     Cancelled
## 00:41  London Waterloo                         6     On time
## 00:44  Gatwick Airport                         5     On time
## 00:46  London Paddington                       13    On time
## 23:18  Bedwyn                                  BUS   On time
## 23:18  Heathrow Central Bus Stn                BUS   On time
## 23:40  Basingstoke                             BUS   On time
## 23:47  Newbury                                 BUS   On time
## 00:18  Heathrow Central Bus Stn                BUS   On time
## 00:37  Bedwyn                                  BUS   On time
## 00:40  Basingstoke                             BUS   On time
## 00:47  Newbury                                 BUS   On time
## 00:55  Banbury                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-07 22:03:54
## Time   To                                      Plat  Expected
## 22:27  Plymouth                                8     23:03
##        via Bristol                             
## 22:46  London Paddington                       10    23:18
## 23:01  London Paddington                       -     Cancelled
## 23:12  London Waterloo                         6     On time
## 23:13  London Paddington                       15    00:21
## 23:19  Swansea                                 8     On time
## 23:22  Ealing Broadway                         13    23:27
## 23:26  Ealing Broadway                         13A   On time
## 23:28  Worcestershire Parkway                  -     Cancelled
## 23:32  Didcot Parkway                          14B   On time
## 23:33  Gatwick Airport                         13A   On time
##        via Guildford                           
## 23:38  London Paddington                       13    On time
## 23:52  Feltham                                 6     On time
## 23:54  London Paddington                       14    On time
## 00:05  Bristol Temple Meads                    13    00:26
## 00:08  Oxford                                  -     Cancelled
## 00:18  London Paddington                       14A   On time
## 00:26  Didcot Parkway                          13B   On time
## 00:43  London Paddington                       -     Cancelled
## 00:49  Penzance                                12    On time
## 23:10  Bedwyn                                  BUS   On time
## 23:40  Basingstoke                             BUS   On time
## 00:20  Newbury                                 BUS   On time
```
