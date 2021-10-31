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

## Example (Last rendered on 2021-10-31 20:06)

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
## Reading (RDG) Station Board on 2021-10-31 20:06:15
## Time   From                                    Plat  Expected
## 19:18  Swansea                                 11    20:04
## 19:40  Bristol Temple Meads                    10    20:34
## 19:40  London Paddington                       8     20:16
## 19:53  London Paddington                       7     Delayed
## 19:58  Penzance                                11    20:54
## 20:01  London Paddington                       9     On time
## 20:05  Ascot                                   4     20:19
## 20:12  London Paddington                       8B    On time
## 20:12  London Paddington                       13    Delayed
## 20:12  Redhill                                 15    On time
## 20:13  Didcot Parkway                          14A   On time
## 20:17  Swansea                                 10    20:31
## 20:20  Newbury                                 1     On time
## 20:23  London Paddington                       12B   On time
## 20:29  London Paddington                       7     On time
## 20:35  Ascot                                   6     On time
## 20:38  Redhill                                 5     20:41
## 20:39  Manchester Piccadilly                   8A    20:58
## 20:40  Plymouth                                11    Delayed
## 20:44  London Paddington                       14    On time
## 20:56  Great Malvern                           10A   On time
## 20:58  Penzance                                11    21:26
## 21:01  London Paddington                       8     On time
## 21:04  Bournemouth                             7     On time
## 21:05  Ascot                                   4     On time
## 21:11  London Paddington                       9     On time
## 21:12  Bristol Temple Meads                    10    On time
## 21:12  Redhill                                 15B   On time
## 21:13  Didcot Parkway                          13A   On time
## 21:14  London Paddington                       14    On time
## 21:19  Bedwyn                                  1     On time
## 21:23  London Paddington                       12B   On time
## 21:26  London Paddington                       7     On time
## 21:31  London Paddington                       9     On time
## 21:32  Swansea                                 10    On time
## 21:35  Ascot                                   6     On time
## 21:39  Manchester Piccadilly                   8A    On time
## 21:39  Redhill                                 15    On time
## 21:44  London Paddington                       14    On time
## 21:59  Worcester Foregate Street               10    On time
## 22:00  London Paddington                       9     On time
## 22:05  Ascot                                   6     On time
## 20:13  Heathrow Central Bus Stn                BUS   On time
## 20:18  Basingstoke                             BUS   On time
## 21:00  Basingstoke                             BUS   On time
## 21:03  Heathrow Central Bus Stn                BUS   On time
## 21:18  Basingstoke                             BUS   On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-10-31 20:06:18
## Time   To                                      Plat  Expected
## 19:25  London Paddington                       11    20:06
## 19:50  Oxford                                  8     20:17
## 19:55  Bristol Temple Meads                    7     Delayed
## 20:00  London Paddington                       11    20:55
## 20:09  Swansea                                 9     On time
## 20:12  Redhill                                 5     On time
## 20:14  Ealing Broadway                         14A   On time
## 20:14  Great Malvern                           8B    On time
## 20:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 20:21  Ascot                                   4     On time
## 20:25  London Paddington                       10    20:32
## 20:26  Didcot Parkway                          12B   On time
## 20:31  Ealing Broadway                         13    On time
## 20:33  Plymouth                                7     On time
## 20:42  Newbury                                 1     On time
## 20:45  London Paddington                       11    Delayed
## 20:46  Southampton Central                     8A    20:59
## 20:51  Ascot                                   6     On time
## 20:55  Weston-super-Mare                       8     On time
## 21:00  London Paddington                       11    21:27
## 21:01  Ealing Broadway                         14    On time
## 21:02  London Paddington                       10A   On time
## 21:09  Swansea                                 8     On time
## 21:12  Birmingham New Street                   7     On time
##        via Coventry                            
## 21:13  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:14  Ealing Broadway                         13A   On time
## 21:15  London Paddington                       10    On time
## 21:15  Worcester Shrub Hill                    9     On time
## 21:21  Ascot                                   4     On time
## 21:25  Didcot Parkway                          12B   On time
## 21:27  Exeter St Davids                        7     On time
## 21:30  Ealing Broadway                         14    On time
## 21:40  London Paddington                       10    On time
## 21:44  Bedwyn                                  1     On time
## 21:44  Oxford                                  9     On time
## 21:46  Southampton Central                     8A    On time
## 21:51  Ascot                                   6     On time
## 22:00  Bristol Temple Meads                    9     On time
## 22:01  Ealing Broadway                         14    On time
## 22:02  London Paddington                       10    On time
## 20:38  Basingstoke                             BUS   On time
## 20:52  Basingstoke                             BUS   On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
## 21:38  Basingstoke                             BUS   On time
## 21:52  Basingstoke                             BUS   On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
```
