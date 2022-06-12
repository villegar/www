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

## Example (Last rendered on 2022-06-12 18:07)

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
## Reading (RDG) Station Board on 2022-06-12 18:07:10
## Time   From                                    Plat  Expected
## 18:02  Ascot                                   4     19:31
## 18:03  London Paddington                       14    19:38
## 18:39  Manchester Piccadilly                   12    Delayed
## 18:58  Penzance                                11    Delayed
## 19:05  Bournemouth                             8     On time
## 19:08  Redhill                                 15    19:28
## 19:12  London Paddington                       9     On time
## 19:13  Didcot Parkway                          13A   On time
## 19:13  London Paddington                       12B   On time
## 19:16  Taunton                                 10    On time
## 19:19  Bedwyn                                  1     On time
## 19:23  London Paddington                       9     On time
## 19:25  Oxford                                  10    On time
## 19:26  London Paddington                       -     On time
## 19:32  Ascot                                   -     On time
## 19:33  London Paddington                       -     On time
## 19:34  Basingstoke                             -     On time
## 19:38  Gatwick Airport                         -     On time
## 19:39  London Paddington                       -     On time
## 19:39  Manchester Piccadilly                   -     On time
## 19:40  Paignton                                -     Cancelled
## 19:45  London Paddington                       -     On time
## 19:50  London Paddington                       -     On time
## 19:53  London Paddington                       -     On time
## 19:55  Hereford                                -     On time
## 19:57  Penzance                                -     On time
## 20:02  Ascot                                   -     On time
## 20:04  London Paddington                       -     On time
## 20:08  Redhill                                 -     On time
## 20:09  Bristol Temple Meads                    -     On time
## 20:12  Carmarthen                              -     On time
## 20:12  London Paddington                       -     On time
## 20:13  Didcot Parkway                          -     On time
## 20:19  London Paddington                       -     On time
## 20:20  Newbury                                 -     On time
## 20:24  Oxford                                  -     On time
## 20:27  London Paddington                       -     On time
## 20:32  Ascot                                   -     On time
## 20:33  Basingstoke                             -     On time
## 20:33  London Paddington                       -     On time
## 20:38  Gatwick Airport                         -     On time
## 20:39  Manchester Piccadilly                   -     On time
## 20:42  Plymouth                                -     On time
## 20:45  London Paddington                       -     On time
## 20:53  London Paddington                       -     On time
## 20:57  Great Malvern                           -     On time
## 20:58  Penzance                                -     On time
## 21:02  Ascot                                   -     On time
## 21:03  London Paddington                       -     On time
## 19:38  Heathrow Central Bus Stn                -     On time
## 20:30  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-06-12 18:07:13
## Time   To                                      Plat  Expected
## 18:24  Ascot                                   4     19:34
## 18:24  Ealing Broadway                         14    19:41
## 18:59  London Paddington                       11    Delayed
## 19:13  Ealing Broadway                         13A   On time
## 19:14  Hereford                                9     On time
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 19:17  London Paddington                       10    On time
## 19:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:24  Ascot                                   4     On time
## 19:24  Ealing Broadway                         14    On time
## 19:25  Bristol Temple Meads                    9     On time
## 19:25  Didcot Parkway                          12B   On time
## 19:25  London Paddington                       10    On time
## 19:28  Plymouth                                -     On time
## 19:38  Basingstoke                             -     On time
## 19:40  Swindon                                 -     On time
## 19:42  London Paddington                       -     Cancelled
## 19:43  Bedwyn                                  -     On time
## 19:48  Oxford                                  -     On time
## 19:52  Bournemouth                             -     On time
## 19:52  Swansea                                 -     On time
## 19:54  Ascot                                   -     On time
## 19:54  Ealing Broadway                         -     On time
## 19:58  Bristol Temple Meads                    -     On time
## 19:58  London Paddington                       -     On time
## 20:01  London Paddington                       -     On time
## 20:11  London Paddington                       -     On time
## 20:12  Gatwick Airport                         -     On time
##        via Guildford                           
## 20:14  Ealing Broadway                         -     On time
## 20:14  Great Malvern                           -     On time
## 20:15  London Paddington                       -     On time
## 20:15  Manchester Piccadilly                   -     On time
##        via Coventry & Wilmslow                 
## 20:24  Ascot                                   -     On time
## 20:24  Ealing Broadway                         -     On time
## 20:25  Didcot Parkway                          -     On time
## 20:25  London Paddington                       -     On time
## 20:28  Plymouth                                -     On time
## 20:38  Basingstoke                             -     On time
## 20:43  Newbury                                 -     On time
## 20:44  London Paddington                       -     On time
## 20:48  Oxford                                  -     On time
## 20:52  Bournemouth                             -     On time
## 20:54  Ascot                                   -     On time
## 20:54  Ealing Broadway                         -     On time
## 20:55  Weston-super-Mare                       -     On time
## 20:59  London Paddington                       -     On time
## 21:01  London Paddington                       -     On time
## 20:00  Heathrow Central Bus Stn                -     On time
## 21:00  Heathrow Central Bus Stn                -     On time
```
