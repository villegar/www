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

## Example (Last rendered on 2021-12-12 18:03)

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
## Reading (RDG) Station Board on 2021-12-12 18:03:34
## Time   From                                    Plat  Expected
## 17:57  Hereford                                11    18:00
## 18:06  Exeter St Davids                        10    18:47
## 18:07  London Paddington                       9     On time
## 18:08  Guildford                               6     18:10
## 18:12  London Paddington                       9B    On time
## 18:13  Didcot Parkway                          15    On time
## 18:13  London Paddington                       14    On time
## 18:15  London Paddington                       12    On time
## 18:21  Newbury                                 1     On time
## 18:21  Swindon                                 10    On time
## 18:24  Plymouth                                11    18:46
## 18:26  London Paddington                       8     18:35
## 18:28  London Paddington                       9B    18:37
## 18:29  Oxford                                  10A   On time
## 18:33  Basingstoke                             2     On time
## 18:33  Cheltenham Spa                          -     Cancelled
## 18:39  Manchester Piccadilly                   12    18:43
## 18:40  Bristol Temple Meads                    10    On time
## 18:43  London Paddington                       14    On time
## 18:44  London Paddington                       8     On time
## 18:53  London Paddington                       9     On time
## 18:53  Swansea                                 11    On time
## 18:56  Great Malvern                           10A   On time
## 19:07  London Paddington                       9     On time
## 19:09  Bournemouth                             7     On time
## 19:09  Taunton                                 10    19:14
## 19:10  Guildford                               6     On time
## 19:12  London Paddington                       9B    On time
## 19:13  London Paddington                       13    On time
## 19:14  Didcot Parkway                          14    On time
## 19:15  London Paddington                       12    On time
## 19:17  Penzance                                11    On time
## 19:19  Newbury                                 1     On time
## 19:26  London Paddington                       8     On time
## 19:28  London Paddington                       9     On time
## 19:29  Oxford                                  10A   On time
## 19:34  Basingstoke                             2     On time
## 19:39  London Paddington                       9     On time
## 19:39  Manchester Piccadilly                   7B    On time
## 19:43  London Paddington                       14    On time
## 19:47  London Paddington                       9B    On time
## 19:53  London Paddington                       9     On time
## 19:55  Hereford                                10    On time
## 19:59  Carmarthen                              11    On time
## 18:15  Virginia Water                          BUS   On time
## 18:21  Heathrow Central Bus Stn                BUS   On time
## 18:26  Virginia Water                          BUS   On time
## 18:45  Virginia Water                          BUS   On time
## 18:56  Virginia Water                          BUS   On time
## 19:15  Virginia Water                          BUS   On time
## 19:19  Heathrow Central Bus Stn                BUS   On time
## 19:26  Virginia Water                          BUS   On time
## 19:45  Virginia Water                          BUS   On time
## 19:56  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-12-12 18:03:38
## Time   To                                      Plat  Expected
## 18:01  London Paddington                       11    On time
## 18:09  Swansea                                 9     On time
## 18:14  Ealing Broadway                         15    On time
## 18:14  Great Malvern                           9B    On time
## 18:14  London Paddington                       10    18:48
## 18:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 18:22  Ealing Broadway                         14    On time
## 18:23  London Paddington                       10    On time
## 18:25  Didcot Parkway                          12    On time
## 18:27  London Paddington                       11    18:47
## 18:29  Penzance                                8     18:36
## 18:31  London Paddington                       10A   On time
## 18:32  Plymouth                                9B    18:38
##        via Bristol                             
## 18:36  London Paddington                       -     Cancelled
## 18:39  Basingstoke                             2     On time
## 18:41  Guildford                               6     On time
## 18:41  London Paddington                       10    On time
## 18:44  Newbury                                 1     On time
## 18:47  Oxford                                  8     On time
## 18:52  Ealing Broadway                         14    On time
## 18:55  London Paddington                       11    On time
## 18:55  Weston-super-Mare                       9     On time
## 19:02  London Paddington                       10A   On time
## 19:08  Swansea                                 9     On time
## 19:11  London Paddington                       10    19:15
## 19:14  Ealing Broadway                         14    On time
## 19:14  Hereford                                9B    On time
## 19:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 19:19  London Paddington                       11    On time
## 19:22  Ealing Broadway                         13    On time
## 19:25  Didcot Parkway                          12    On time
## 19:29  Plymouth                                8     On time
## 19:31  London Paddington                       10A   On time
## 19:32  Bristol Temple Meads                    9     On time
## 19:38  Basingstoke                             2     On time
## 19:40  Swindon                                 9     On time
## 19:44  Newbury                                 1     On time
## 19:50  Oxford                                  9B    On time
## 19:52  Bournemouth                             7B    On time
## 19:52  Ealing Broadway                         14    On time
## 19:55  Bristol Temple Meads                    9     On time
## 19:59  London Paddington                       11    On time
## 20:01  London Paddington                       10    On time
## 18:05  Virginia Water                          BUS   On time
## 18:25  Virginia Water                          BUS   On time
## 18:35  Virginia Water                          BUS   On time
## 18:55  Virginia Water                          BUS   On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
## 19:05  Virginia Water                          BUS   On time
## 19:25  Virginia Water                          BUS   On time
## 19:35  Virginia Water                          BUS   On time
## 19:55  Virginia Water                          BUS   On time
## 20:00  Heathrow Central Bus Stn                BUS   On time
```
