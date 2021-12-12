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

## Example (Last rendered on 2021-12-12 12:03)

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
## Reading (RDG) Station Board on 2021-12-12 12:03:40
## Time   From                                    Plat  Expected
## 11:56  Great Malvern                           10A   11:52
## 12:01  London Paddington                       8     On time
## 12:07  London Paddington                       9     12:14
## 12:08  Ash                                     6     On time
## 12:10  Didcot Parkway                          15    On time
## 12:12  Bristol Temple Meads                    10    On time
## 12:12  London Paddington                       9     On time
## 12:13  London Paddington                       14    On time
## 12:15  London Paddington                       12    On time
## 12:19  Newbury                                 1     On time
## 12:21  Plymouth                                -     12:24
## 12:25  Oxford                                  -     Cancelled
## 12:31  Cheltenham Spa                          -     Cancelled
## 12:33  Basingstoke                             2     On time
## 12:39  Manchester Piccadilly                   12    On time
## 12:43  London Paddington                       14    On time
## 12:44  London Paddington                       9     On time
## 12:47  Salisbury                               1     On time
## 12:53  London Paddington                       9     On time
## 12:53  Swansea                                 11    On time
## 12:56  Great Malvern                           -     Cancelled
## 13:01  London Paddington                       8     On time
## 13:06  Bournemouth                             7     On time
## 13:07  London Paddington                       9     On time
## 13:08  Ash                                     6     Delayed
## 13:10  Didcot Parkway                          15    On time
## 13:10  Weston-super-Mare                       10    On time
## 13:12  London Paddington                       9     On time
## 13:13  London Paddington                       14    On time
## 13:15  London Paddington                       12    On time
## 13:16  Penzance                                11    13:24
## 13:17  Newbury                                 1     On time
## 13:26  Swindon                                 10    On time
## 13:29  Oxford                                  11    On time
## 13:33  Basingstoke                             2     On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:40  Bristol Temple Meads                    11    On time
## 13:43  London Paddington                       14    On time
## 13:45  London Paddington                       8     On time
## 13:47  Salisbury                               1     On time
## 13:53  London Paddington                       9     On time
## 13:55  Great Malvern                           -     Cancelled
## 13:58  Swansea                                 11    On time
## 12:15  Virginia Water                          BUS   On time
## 12:21  Heathrow Central Bus Stn                BUS   On time
## 12:26  Virginia Water                          BUS   On time
## 12:45  Virginia Water                          BUS   On time
## 12:56  Virginia Water                          BUS   On time
## 13:15  Virginia Water                          BUS   On time
## 13:21  Heathrow Central Bus Stn                BUS   On time
## 13:26  Virginia Water                          BUS   On time
## 13:45  Virginia Water                          BUS   On time
## 13:56  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-12-12 12:03:44
## Time   To                                      Plat  Expected
## 12:02  London Paddington                       10A   On time
## 12:05  Penzance                                8     On time
## 12:09  Carmarthen                              9     12:15
## 12:12  Ealing Broadway                         15    On time
## 12:12  Salisbury                               1     On time
## 12:14  London Paddington                       10    On time
## 12:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 12:18  Hereford                                9     On time
## 12:22  Ealing Broadway                         14    On time
## 12:25  London Paddington                       -     On time
## 12:26  Didcot Parkway                          12    On time
## 12:27  London Paddington                       -     Cancelled
## 12:33  London Paddington                       -     Cancelled
## 12:38  Basingstoke                             2     On time
## 12:41  Guildford                               6     On time
## 12:44  Newbury                                 1     On time
## 12:48  Oxford                                  9     On time
## 12:52  Ealing Broadway                         14    On time
## 12:54  London Paddington                       11    On time
## 12:55  Weston-super-Mare                       9     On time
## 12:59  London Paddington                       -     Cancelled
## 13:05  Plymouth                                8     On time
## 13:09  Swansea                                 9     On time
## 13:12  Ealing Broadway                         15    On time
## 13:12  London Paddington                       10    On time
## 13:12  Salisbury                               1     On time
## 13:14  Great Malvern                           9     On time
## 13:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 13:20  London Paddington                       11    13:25
## 13:22  Ealing Broadway                         14    On time
## 13:26  Didcot Parkway                          12    On time
## 13:28  London Paddington                       10    On time
## 13:31  London Paddington                       11    On time
## 13:38  Basingstoke                             2     On time
## 13:41  Guildford                               6     On time
## 13:42  London Paddington                       11    On time
## 13:44  Newbury                                 1     On time
## 13:48  Oxford                                  8     On time
## 13:52  Bournemouth                             7     On time
## 13:52  Ealing Broadway                         14    On time
## 13:55  Bristol Temple Meads                    9     On time
## 13:58  London Paddington                       11    On time
## 14:00  London Paddington                       -     Cancelled
## 12:05  Virginia Water                          BUS   On time
## 12:25  Virginia Water                          BUS   On time
## 12:35  Virginia Water                          BUS   On time
## 12:55  Virginia Water                          BUS   On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
## 13:05  Virginia Water                          BUS   On time
## 13:25  Virginia Water                          BUS   On time
## 13:35  Virginia Water                          BUS   On time
## 13:55  Virginia Water                          BUS   On time
## 14:00  Heathrow Central Bus Stn                BUS   On time
```
