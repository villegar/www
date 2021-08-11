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

## Example (Last rendered on 2021-08-11 14:07)

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
## Reading (RDG) Station Board on 2021-08-11 14:07:04
## Time   From                                    Plat  Expected
## 14:45  Swansea                                 -     16:01
## 14:59  Penzance                                -     15:03
## 15:05  Bournemouth                             -     On time
## 15:09  Bristol Parkway                         -     On time
## 15:11  London Paddington                       -     15:13
## 15:11  London Waterloo                         -     On time
## 15:13  London Paddington                       -     On time
## 15:14  London Paddington                       -     On time
## 15:16  London Paddington                       -     On time
## 15:22  Newbury                                 -     On time
## 15:25  London Paddington                       -     On time
## 15:25  Oxford                                  -     On time
## 15:26  Basingstoke                             -     On time
## 15:27  London Paddington                       -     On time
## 15:30  Cheltenham Spa                          -     On time
## 15:32  Didcot Parkway                          -     On time
## 15:32  London Paddington                       -     On time
## 15:33  Redhill                                 -     On time
## 15:36  Newbury                                 -     On time
## 15:39  Bath Spa                                -     On time
## 15:40  Manchester Piccadilly                   -     On time
## 15:41  London Paddington                       -     On time
## 15:41  London Waterloo                         -     On time
## 15:43  London Paddington                       -     On time
## 15:44  Swansea                                 -     16:07
## 15:46  London Paddington                       -     On time
## 15:47  Exeter St Davids                        -     On time
## 15:51  Gatwick Airport                         -     On time
## 15:53  Basingstoke                             -     On time
## 15:53  Hereford                                -     On time
## 15:56  London Paddington                       -     On time
## 15:57  Paignton                                -     On time
## 16:09  Bristol Parkway                         -     On time
## 16:11  London Waterloo                         -     On time
## 16:13  London Paddington                       -     On time
## 16:17  Bristol Parkway                         -     On time
## 16:18  Basingstoke                             -     On time
## 16:22  London Paddington                       -     On time
## 16:22  Newbury                                 -     On time
## 16:24  Oxford                                  -     On time
## 16:25  London Paddington                       -     On time
## 16:27  London Paddington                       -     On time
## 16:31  Didcot Parkway                          -     On time
## 16:31  London Paddington                       -     On time
## 16:32  Newbury                                 -     On time
## 16:33  Redhill                                 -     Delayed
## 16:39  Bath Spa                                -     On time
## 16:41  London Waterloo                         -     On time
## 16:41  Manchester Piccadilly                   -     On time
## 16:43  London Paddington                       -     On time
## 16:45  Swansea                                 -     On time
## 16:46  London Paddington                       -     On time
## 16:46  London Paddington                       -     On time
## 16:50  Basingstoke                             -     On time
## 16:54  Worcester Foregate Street               -     On time
## 16:56  London Paddington                       -     On time
## 16:56  Newbury                                 -     On time
## 16:58  London Paddington                       -     On time
## 16:59  London Paddington                       -     On time
## 17:00  Gatwick Airport                         -     Delayed
## 17:01  Plymouth                                -     On time
## 15:21  Heathrow Central Bus Stn                -     On time
## 16:21  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-08-11 14:07:06
## Time   To                                      Plat  Expected
## 15:04  London Paddington                       -     On time
## 15:05  Basingstoke                             -     On time
## 15:10  Newbury                                 -     On time
## 15:12  London Waterloo                         -     On time
## 15:13  London Paddington                       -     On time
## 15:13  Swansea                                 -     15:14
## 15:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 15:18  Redhill                                 -     On time
## 15:18  Worcester Foregate Street               -     On time
## 15:22  Ealing Broadway                         -     On time
## 15:23  Didcot Parkway                          -     On time
## 15:24  London Paddington                       -     On time
## 15:27  Bath Spa                                -     On time
## 15:27  London Paddington                       -     On time
## 15:29  Penzance                                -     On time
## 15:32  Basingstoke                             -     On time
## 15:34  London Paddington                       -     On time
## 15:37  Bedwyn                                  -     On time
## 15:39  Ealing Broadway                         -     On time
## 15:42  London Waterloo                         -     On time
## 15:43  Cardiff Central                         -     On time
## 15:43  London Paddington                       -     On time
## 15:45  London Paddington                       -     16:08
## 15:48  Worcester Foregate Street               -     On time
## 15:50  London Paddington                       -     On time
## 15:50  Newbury                                 -     On time
## 15:52  Ealing Broadway                         -     On time
## 15:55  Oxford                                  -     On time
## 15:56  London Paddington                       -     On time
## 15:58  Bristol Parkway                         -     On time
## 16:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 16:04  London Paddington                       -     On time
## 16:07  Basingstoke                             -     On time
## 16:12  London Paddington                       -     On time
## 16:12  London Waterloo                         -     On time
## 16:12  Newbury                                 -     On time
## 16:13  Swansea                                 -     On time
## 16:15  Ealing Broadway                         -     On time
## 16:16  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 16:19  Great Malvern                           -     On time
## 16:19  London Paddington                       -     On time
## 16:20  Redhill                                 -     On time
## 16:22  Ealing Broadway                         -     On time
## 16:24  London Paddington                       -     On time
## 16:25  Didcot Parkway                          -     On time
## 16:27  Bath Spa                                -     On time
## 16:27  London Paddington                       -     On time
## 16:27  London Paddington                       -     On time
## 16:29  Penzance                                -     On time
## 16:33  Basingstoke                             -     On time
## 16:33  Ealing Broadway                         -     On time
## 16:37  Newbury                                 -     On time
## 16:38  Ealing Broadway                         -     On time
## 16:41  London Waterloo                         -     On time
## 16:42  London Paddington                       -     On time
## 16:48  London Paddington                       -     On time
## 16:48  Oxford                                  -     On time
## 16:50  Gatwick Airport                         -     On time
##        via Guildford                           
## 16:52  Bournemouth                             -     On time
## 16:52  Ealing Broadway                         -     On time
## 16:57  London Paddington                       -     On time
## 16:58  Bristol Parkway                         -     On time
## 17:02  Plymouth                                -     On time
## 17:03  Ealing Broadway                         -     On time
## 17:05  London Paddington                       -     On time
## 17:06  Ealing Broadway                         -     On time
## 16:00  Heathrow Central Bus Stn                -     On time
## 17:00  Heathrow Central Bus Stn                -     On time
```
