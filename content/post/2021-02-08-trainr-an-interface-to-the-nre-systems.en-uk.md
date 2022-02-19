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

## Example (Last rendered on 2022-02-19 22:03)

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
## Reading (RDG) Station Board on 2022-02-19 22:04:00
## Time   From                                    Plat  Expected
## 21:26  Bedwyn                                  15    21:51
## 21:42  Newbury                                 1     Delayed
## 21:50  Swansea                                 10    22:28
## 21:56  London Paddington                       9     22:11
## 22:07  London Waterloo                         -     Cancelled
## 22:09  Bristol Temple Meads                    10    Delayed
## 22:13  London Paddington                       14    On time
## 22:17  London Paddington                       8B    On time
## 22:19  Basingstoke                             2     On time
## 22:22  Newbury                                 1     Delayed
## 22:25  Gatwick Airport                         -     Cancelled
## 22:25  London Paddington                       9     On time
## 22:27  Didcot Parkway                          13    On time
## 22:32  Oxford                                  -     Cancelled
## 22:36  Cheltenham Spa                          10A   On time
## 22:43  London Paddington                       14    On time
## 22:43  London Waterloo                         -     Cancelled
## 22:47  London Paddington                       -     Cancelled
## 22:50  Basingstoke                             2     On time
## 22:56  London Paddington                       -     Cancelled
## 23:04  Hereford                                13A   On time
## 23:04  Redhill                                 -     Cancelled
## 23:10  Newbury                                 7B    On time
## 23:11  Exeter St Davids                        -     Cancelled
## 23:11  London Waterloo                         -     Cancelled
## 23:14  London Paddington                       9     On time
## 23:19  London Paddington                       7A    On time
## 23:23  Basingstoke                             3     On time
## 23:26  Didcot Parkway                          8B    On time
## 23:31  London Paddington                       -     Cancelled
## 23:42  London Waterloo                         -     Cancelled
## 23:44  London Paddington                       -     On time
## 23:44  London Paddington                       -     On time
## 23:46  London Paddington                       10    On time
## 23:52  Basingstoke                             3     On time
## 23:52  Taunton                                 11    On time
## 23:59  London Paddington                       8     On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-19 22:04:04
## Time   To                                      Plat  Expected
## 21:51  London Paddington                       10    22:29
## 21:57  Bristol Temple Meads                    9     22:12
## 22:05  Basingstoke                             2     On time
## 22:10  Newbury                                 1     On time
## 22:12  London Waterloo                         -     Cancelled
## 22:15  Ealing Broadway                         15    On time
## 22:15  London Paddington                       10    Delayed
## 22:19  Worcester Shrub Hill                    8B    On time
## 22:22  Ealing Broadway                         14    On time
## 22:27  Bristol Parkway                         9     On time
## 22:30  Didcot Parkway                          12    On time
## 22:34  London Paddington                       -     Cancelled
## 22:35  Basingstoke                             2     On time
## 22:39  London Paddington                       10A   On time
## 22:42  London Waterloo                         -     Cancelled
## 22:52  Ealing Broadway                         14    On time
## 22:57  Bristol Temple Meads                    -     Cancelled
## 23:05  Basingstoke                             2     On time
## 23:05  Didcot Parkway                          12    On time
## 23:06  London Paddington                       13A   On time
## 23:10  Newbury                                 1     On time
## 23:15  London Waterloo                         -     Cancelled
## 23:16  London Paddington                       -     Cancelled
## 23:34  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 23:48  Didcot Parkway                          7     On time
## 23:52  Staines                                 -     Cancelled
## 23:53  London Paddington                       11    On time
## 00:02  Bristol Temple Meads                    8     On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
