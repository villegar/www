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

## Example (Last rendered on 2022-12-27 10:04)

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
## Reading (RDG) Station Board on 2022-12-27 10:04:06
## Time   From                                    Plat  Expected
## 09:50  London Paddington                       9B    Delayed
## 10:00  London Paddington                       8     Delayed
## 10:10  Didcot Parkway                          15A   On time
## 10:17  London Paddington                       9     Delayed
## 10:21  Newbury                                 11    10:26
## 10:29  London Paddington                       8     On time
## 10:30  Didcot Parkway                          10    On time
## 10:44  Birmingham New Street                   7     On time
## 10:44  London Paddington                       8     On time
## 10:48  London Paddington                       12B   11:01
## 10:50  London Paddington                       9     On time
## 10:55  Moreton-in-Marsh                        15    On time
## 10:57  London Paddington                       8     On time
## 11:00  London Paddington                       7     On time
## 11:13  Bristol Temple Meads                    10    On time
## 11:17  Swansea                                 11A   On time
## 11:18  London Paddington                       9     On time
## 11:26  Oxford                                  10    On time
## 11:27  London Paddington                       8     On time
## 11:36  London Paddington                       12B   On time
## 11:36  Newbury                                 3     On time
## 11:40  Bristol Temple Meads                    10    On time
## 11:41  Birmingham New Street                   8     Delayed
## 11:46  London Paddington                       15    On time
## 11:46  London Paddington                       9     On time
## 11:55  London Paddington                       9     On time
## 10:04  Heathrow Central Bus Stn                BUS   On time
## 10:34  Heathrow Central Bus Stn                BUS   On time
## 11:04  Heathrow Central Bus Stn                BUS   On time
## 11:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-27 10:04:10
## Time   To                                      Plat  Expected
## 09:52  Oxford                                  9B    Delayed
## 10:01  Paignton                                8     Delayed
## 10:08  Newbury                                 12B   On time
## 10:11  London Paddington                       15A   On time
## 10:19  Hereford                                9     Delayed
## 10:22  London Paddington                       11    10:26
## 10:31  London Paddington                       10    On time
## 10:31  Penzance                                8     On time
## 10:47  Swansea                                 8     On time
## 10:52  Oxford                                  9     On time
## 10:53  Didcot Parkway                          12B   11:02
## 11:00  Bristol Temple Meads                    8     On time
## 11:02  Exeter St Davids                        7     On time
## 11:11  Ealing Broadway                         14    On time
## 11:12  Newbury                                 13B   On time
## 11:15  London Paddington                       10    On time
## 11:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 11:18  London Paddington                       11A   On time
## 11:20  Worcester Shrub Hill                    9     On time
## 11:25  London Paddington                       13    On time
## 11:27  Ealing Broadway                         14    On time
## 11:29  London Paddington                       10    On time
## 11:29  Plymouth                                8     On time
## 11:37  Newbury                                 13A   On time
## 11:40  Ealing Broadway                         15A   On time
## 11:43  London Paddington                       10    On time
## 11:49  Oxford                                  9     On time
## 11:53  Didcot Parkway                          13A   On time
## 11:57  Bristol Temple Meads                    9     On time
## 11:57  Ealing Broadway                         14    On time
## 12:01  Gatwick Airport                         15A   On time
##        via Guildford                           
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
```
