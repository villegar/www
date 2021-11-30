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

## Example (Last rendered on 2021-11-30 16:14)

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
## Reading (RDG) Station Board on 2021-11-30 16:14:20
## Time   From                                    Plat  Expected
## 15:57  Plymouth                                -     16:16
## 16:14  London Waterloo                         -     16:17
## 16:17  Bristol Parkway                         -     On time
## 16:18  Basingstoke                             -     On time
## 16:22  London Paddington                       -     On time
## 16:22  Newbury                                 -     On time
## 16:24  Oxford                                  -     On time
## 16:25  London Paddington                       -     16:28
## 16:27  London Paddington                       -     On time
## 16:31  Didcot Parkway                          -     On time
## 16:31  London Paddington                       -     16:38
## 16:32  Newbury                                 -     On time
## 16:33  Redhill                                 -     On time
## 16:39  Bristol Temple Meads                    -     On time
## 16:41  Manchester Piccadilly                   -     On time
## 16:43  London Paddington                       -     On time
## 16:43  Paignton                                -     On time
## 16:44  London Waterloo                         -     On time
## 16:45  Swansea                                 -     On time
## 16:46  London Paddington                       -     On time
## 16:46  London Paddington                       -     On time
## 16:50  Basingstoke                             -     On time
## 16:54  Worcester Foregate Street               -     On time
## 16:56  London Paddington                       -     On time
## 16:56  Newbury                                 -     On time
## 16:58  London Paddington                       -     On time
## 16:59  London Paddington                       -     On time
## 17:01  Penzance                                -     On time
## 17:03  Gatwick Airport                         -     On time
## 17:06  Bournemouth                             -     On time
## 17:09  Bristol Temple Meads                    -     On time
## 17:11  London Paddington                       -     On time
## 17:13  London Paddington                       -     On time
## 17:14  London Waterloo                         -     On time
## 17:22  Bedwyn                                  -     On time
## 17:22  London Paddington                       -     On time
## 17:25  London Paddington                       -     On time
## 17:26  Basingstoke                             -     On time
## 17:27  London Paddington                       -     On time
## 17:28  London Paddington                       -     On time
## 17:29  Cheltenham Spa                          -     On time
## 17:33  Newbury                                 -     On time
## 17:34  London Paddington                       -     On time
## 17:35  Didcot Parkway                          -     On time
## 17:38  Bristol Temple Meads                    -     On time
## 17:38  London Paddington                       -     On time
## 17:39  Exeter St Davids                        -     On time
## 17:40  Manchester Piccadilly                   -     On time
## 17:43  London Paddington                       -     On time
## 17:43  London Waterloo                         -     On time
## 17:44  Redhill                                 -     On time
## 17:44  Swansea                                 -     On time
## 17:46  Basingstoke                             -     On time
## 17:54  London Paddington                       -     On time
## 17:55  London Paddington                       -     On time
## 17:56  Hereford                                -     On time
## 17:57  Plymouth                                -     On time
## 17:58  London Paddington                       -     On time
## 17:58  London Paddington                       -     On time
## 18:01  London Paddington                       -     On time
## 18:02  Gatwick Airport                         -     On time
## 18:09  Bristol Temple Meads                    -     On time
## 18:11  London Paddington                       -     On time
## 18:13  London Paddington                       -     On time
## 16:21  Heathrow Central Bus Stn                -     On time
## 17:21  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-11-30 16:14:22
## Time   To                                      Plat  Expected
## 16:04  London Paddington                       -     16:17
## 16:15  London Paddington                       -     On time
## 16:16  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 16:19  Great Malvern                           -     On time
## 16:19  London Paddington                       -     On time
## 16:20  Redhill                                 -     On time
## 16:22  London Paddington                       -     On time
## 16:24  London Paddington                       -     On time
## 16:25  Didcot Parkway                          -     On time
## 16:27  Bristol Temple Meads                    -     16:29
## 16:27  London Paddington                       -     On time
## 16:27  London Paddington                       -     On time
## 16:29  Penzance                                -     On time
## 16:33  Basingstoke                             -     On time
## 16:33  London Paddington                       -     On time
## 16:37  Newbury                                 -     16:39
## 16:38  London Paddington                       -     On time
## 16:39  London Waterloo                         -     On time
## 16:42  London Paddington                       -     On time
## 16:45  London Paddington                       -     On time
## 16:48  London Paddington                       -     On time
## 16:48  Oxford                                  -     On time
## 16:50  Gatwick Airport                         -     On time
##        via Guildford                           
## 16:52  Bournemouth                             -     On time
## 16:52  London Paddington                       -     On time
## 16:57  London Paddington                       -     On time
## 16:58  Taunton                                 -     On time
## 17:02  Plymouth                                -     On time
## 17:03  London Paddington                       -     On time
## 17:05  London Paddington                       -     On time
## 17:06  London Paddington                       -     On time
## 17:09  London Waterloo                         -     On time
## 17:10  Newbury                                 -     On time
## 17:11  London Paddington                       -     On time
## 17:13  Swansea                                 -     On time
## 17:15  Basingstoke                             -     On time
## 17:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 17:20  Redhill                                 -     On time
## 17:22  London Paddington                       -     On time
## 17:24  London Paddington                       -     On time
## 17:25  Didcot Parkway                          -     On time
## 17:27  Bristol Temple Meads                    -     On time
## 17:29  Penzance                                -     On time
## 17:32  London Paddington                       -     On time
## 17:33  London Paddington                       -     On time
## 17:35  Newbury                                 -     On time
## 17:38  Basingstoke                             -     On time
## 17:39  Bristol Parkway                         -     On time
## 17:39  London Waterloo                         -     On time
## 17:41  London Paddington                       -     On time
## 17:42  London Paddington                       -     On time
## 17:43  London Paddington                       -     On time
## 17:46  London Paddington                       -     On time
## 17:49  Newbury                                 -     On time
## 17:50  Gatwick Airport                         -     On time
##        via Guildford                           
## 17:52  London Paddington                       -     On time
## 17:52  Southampton Central                     -     On time
## 17:57  Basingstoke                             -     On time
## 17:57  Taunton                                 -     On time
## 17:58  Didcot Parkway                          -     On time
## 17:58  London Paddington                       -     On time
## 18:00  Hereford                                -     On time
## 18:00  London Paddington                       -     On time
## 18:03  Plymouth                                -     On time
## 18:05  London Paddington                       -     On time
## 18:07  Newbury                                 -     On time
## 18:08  London Paddington                       -     On time
## 18:10  London Waterloo                         -     On time
## 18:12  London Paddington                       -     On time
## 18:13  Carmarthen                              -     On time
## 17:00  Heathrow Central Bus Stn                -     On time
## 18:00  Heathrow Central Bus Stn                -     On time
```
