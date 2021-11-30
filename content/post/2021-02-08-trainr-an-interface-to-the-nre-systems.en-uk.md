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

## Example (Last rendered on 2021-11-30 18:16)

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
## Reading (RDG) Station Board on 2021-11-30 18:16:04
## Time   From                                    Plat  Expected
## 18:08  Bournemouth                             -     On time
## 18:17  Bristol Parkway                         -     On time
## 18:20  Basingstoke                             -     On time
## 18:25  Newbury                                 -     On time
## 18:26  London Paddington                       -     On time
## 18:26  Oxford                                  -     On time
## 18:27  London Paddington                       -     On time
## 18:28  Didcot Parkway                          -     On time
## 18:28  London Paddington                       -     On time
## 18:30  Cheltenham Spa                          -     On time
## 18:30  London Paddington                       -     On time
## 18:34  London Paddington                       -     On time
## 18:35  Newbury                                 -     On time
## 18:39  Newbury                                 -     On time
## 18:40  Bristol Temple Meads                    -     On time
## 18:42  London Paddington                       -     On time
## 18:43  London Paddington                       -     On time
## 18:43  Manchester Piccadilly                   -     On time
## 18:44  London Paddington                       -     On time
## 18:45  London Waterloo                         -     On time
## 18:45  Redhill                                 -     On time
## 18:47  Swansea                                 -     On time
## 18:50  Basingstoke                             -     On time
## 18:53  London Paddington                       -     On time
## 18:57  Great Malvern                           -     On time
## 18:57  London Paddington                       -     On time
## 18:57  Penzance                                -     On time
## 18:58  London Paddington                       -     On time
## 19:00  London Paddington                       -     On time
## 19:02  Basingstoke                             -     On time
## 19:05  Gatwick Airport                         -     On time
## 19:10  Bristol Temple Meads                    -     On time
## 19:11  London Paddington                       -     On time
## 19:13  London Paddington                       -     On time
## 19:14  London Paddington                       -     On time
## 19:15  Newbury                                 -     On time
## 19:16  Cardiff Central                         -     On time
## 19:17  London Waterloo                         -     On time
## 19:22  Newbury                                 -     On time
## 19:25  Worcester Foregate Street               -     On time
## 19:26  London Paddington                       -     On time
## 19:28  Didcot Parkway                          -     On time
## 19:28  London Paddington                       -     On time
## 19:29  London Paddington                       -     On time
## 19:30  London Paddington                       -     On time
## 19:31  Cheltenham Spa                          -     On time
## 19:33  Redhill                                 -     On time
## 19:34  Basingstoke                             -     On time
## 19:34  London Paddington                       -     On time
## 19:39  Bristol Temple Meads                    -     On time
## 19:41  London Paddington                       -     On time
## 19:41  Manchester Piccadilly                   -     On time
## 19:43  London Paddington                       -     On time
## 19:44  London Paddington                       -     On time
## 19:45  London Waterloo                         -     On time
## 19:46  Swansea                                 -     On time
## 19:53  London Paddington                       -     On time
## 19:54  Plymouth                                -     On time
## 19:54  Worcester Foregate Street               -     On time
## 19:55  London Paddington                       -     On time
## 19:56  London Paddington                       -     On time
## 19:57  Didcot Parkway                          -     On time
## 20:00  Basingstoke                             -     On time
## 20:03  Newbury                                 -     On time
## 20:04  Gatwick Airport                         -     On time
## 20:06  Bournemouth                             -     On time
## 20:10  Bristol Temple Meads                    -     On time
## 20:11  London Paddington                       -     On time
## 20:14  London Paddington                       -     On time
## 20:15  London Waterloo                         -     On time
## 18:21  Heathrow Central Bus Stn                -     On time
## 19:19  Heathrow Central Bus Stn                -     On time
## 20:13  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-11-30 18:16:09
## Time   To                                      Plat  Expected
## 18:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 18:20  London Paddington                       -     On time
## 18:20  Redhill                                 -     On time
## 18:22  London Paddington                       -     On time
## 18:26  London Paddington                       -     On time
## 18:28  Bristol Temple Meads                    -     On time
## 18:28  London Paddington                       -     On time
## 18:29  Penzance                                -     On time
## 18:32  Basingstoke                             -     On time
## 18:32  Didcot Parkway                          -     On time
## 18:32  London Paddington                       -     On time
## 18:33  London Paddington                       -     On time
## 18:38  Frome                                   -     On time
## 18:39  London Waterloo                         -     On time
## 18:40  London Paddington                       -     On time
## 18:43  London Paddington                       -     On time
## 18:43  Swansea                                 -     On time
## 18:44  London Paddington                       -     On time
## 18:49  London Paddington                       -     On time
## 18:52  London Paddington                       -     On time
## 18:57  Didcot Parkway                          -     On time
## 18:58  London Paddington                       -     On time
## 18:59  Weston-super-Mare                       -     On time
## 19:00  London Paddington                       -     On time
## 19:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 19:02  Plymouth                                -     On time
## 19:04  London Paddington                       -     On time
## 19:06  Basingstoke                             -     On time
## 19:09  London Waterloo                         -     On time
## 19:10  Newbury                                 -     On time
## 19:13  London Paddington                       -     On time
## 19:13  Swansea                                 -     On time
## 19:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 19:18  London Paddington                       -     On time
## 19:20  Redhill                                 -     On time
## 19:22  London Paddington                       -     On time
## 19:25  Basingstoke                             -     On time
## 19:25  London Paddington                       -     On time
## 19:27  London Paddington                       -     On time
## 19:27  Weston-super-Mare                       -     On time
## 19:30  Didcot Parkway                          -     On time
## 19:31  Plymouth                                -     On time
## 19:34  London Paddington                       -     On time
## 19:36  Bedwyn                                  -     On time
## 19:38  London Paddington                       -     On time
## 19:39  London Waterloo                         -     On time
## 19:41  London Paddington                       -     On time
## 19:42  Newbury                                 -     On time
## 19:43  Swansea                                 -     On time
## 19:49  Bournemouth                             -     On time
## 19:49  London Paddington                       -     On time
## 19:52  London Paddington                       -     On time
## 19:55  London Paddington                       -     On time
## 19:55  Oxford                                  -     On time
## 19:57  Basingstoke                             -     On time
## 19:57  Didcot Parkway                          -     On time
## 19:57  London Paddington                       -     On time
## 19:58  Bristol Temple Meads                    -     On time
## 20:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 20:09  London Waterloo                         -     On time
## 20:10  Newbury                                 -     On time
## 20:12  London Paddington                       -     On time
## 20:13  Swansea                                 -     On time
## 20:15  Birmingham New Street                   -     On time
##        via Coventry                            
## 20:15  London Paddington                       -     On time
## 19:00  Heathrow Central Bus Stn                -     On time
## 20:00  Heathrow Central Bus Stn                -     On time
```
