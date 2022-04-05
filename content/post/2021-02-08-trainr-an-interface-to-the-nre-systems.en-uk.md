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

## Example (Last rendered on 2022-04-05 16:05)

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
## Reading (RDG) Station Board on 2022-04-05 16:05:12
## Time   From                                    Plat  Expected
## 17:01  Penzance                                -     On time
## 17:03  Gatwick Airport                         -     On time
## 17:06  Bournemouth                             -     On time
## 17:06  Didcot Parkway                          -     On time
## 17:09  Bristol Temple Meads                    -     On time
## 17:11  London Paddington                       -     On time
## 17:13  London Paddington                       -     On time
## 17:16  London Waterloo                         -     On time
## 17:22  Bedwyn                                  -     On time
## 17:22  London Paddington                       -     On time
## 17:24  Oxford                                  -     On time
## 17:25  London Paddington                       -     On time
## 17:26  Basingstoke                             -     On time
## 17:27  London Paddington                       -     On time
## 17:28  London Paddington                       -     On time
## 17:29  Cheltenham Spa                          -     On time
## 17:33  Newbury                                 -     On time
## 17:35  Didcot Parkway                          -     On time
## 17:37  London Paddington                       -     On time
## 17:38  Bristol Temple Meads                    -     On time
## 17:39  Exeter St Davids                        -     On time
## 17:41  London Paddington                       -     On time
## 17:41  Manchester Piccadilly                   -     17:43
## 17:42  London Waterloo                         -     On time
## 17:43  London Paddington                       -     On time
## 17:43  Swansea                                 -     On time
## 17:44  Redhill                                 -     On time
## 17:46  Basingstoke                             -     On time
## 17:54  London Paddington                       -     On time
## 17:55  London Paddington                       -     On time
## 17:56  Hereford                                -     On time
## 17:57  Plymouth                                -     On time
## 17:58  London Paddington                       -     On time
## 17:58  London Paddington                       -     On time
## 18:01  London Paddington                       -     On time
## 18:02  Gatwick Airport                         -     On time
## 18:03  Didcot Parkway                          -     On time
## 18:08  Bournemouth                             -     On time
## 18:09  Bristol Temple Meads                    -     On time
## 18:11  London Paddington                       -     On time
## 18:12  London Waterloo                         -     On time
## 18:13  London Paddington                       -     On time
## 18:20  Basingstoke                             -     On time
## 18:25  Newbury                                 -     On time
## 18:26  London Paddington                       -     On time
## 18:26  Oxford                                  -     On time
## 18:27  London Paddington                       -     On time
## 18:28  London Paddington                       -     On time
## 18:29  Didcot Parkway                          -     On time
## 18:30  Cheltenham Spa                          -     On time
## 18:30  London Paddington                       -     On time
## 18:35  Newbury                                 -     On time
## 18:40  Bristol Temple Meads                    -     On time
## 18:42  London Paddington                       -     On time
## 18:42  London Waterloo                         -     On time
## 18:43  London Paddington                       -     On time
## 18:43  Manchester Piccadilly                   -     On time
## 18:44  London Paddington                       -     On time
## 18:45  Redhill                                 -     On time
## 18:47  Swansea                                 -     On time
## 18:50  Basingstoke                             -     On time
## 18:53  London Paddington                       -     On time
## 18:57  Great Malvern                           -     On time
## 18:57  London Paddington                       -     On time
## 18:57  Penzance                                -     On time
## 18:58  London Paddington                       -     On time
## 18:59  London Paddington                       -     On time
## 19:04  Basingstoke                             -     On time
## 17:16  Heathrow Central Bus Stn                -     On time
## 17:51  Heathrow Central Bus Stn                -     On time
## 18:26  Heathrow Central Bus Stn                -     On time
## 19:01  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-04-05 16:05:16
## Time   To                                      Plat  Expected
## 17:03  Ealing Broadway                         -     17:05
## 17:05  London Paddington                       -     On time
## 17:10  Newbury                                 -     On time
## 17:11  London Paddington                       -     On time
## 17:12  London Waterloo                         -     On time
## 17:13  Ealing Broadway                         -     On time
## 17:13  Swansea                                 -     On time
## 17:15  Basingstoke                             -     On time
## 17:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 17:20  Redhill                                 -     On time
## 17:22  Ealing Broadway                         -     On time
## 17:24  London Paddington                       -     On time
## 17:25  Didcot Parkway                          -     On time
## 17:27  Bristol Temple Meads                    -     On time
## 17:27  London Paddington                       -     On time
## 17:29  Plymouth                                -     On time
## 17:32  London Paddington                       -     On time
## 17:33  Ealing Broadway                         -     On time
## 17:34  Basingstoke                             -     On time
## 17:38  Newbury                                 -     On time
## 17:41  London Paddington                       -     On time
## 17:42  Ealing Broadway                         -     On time
## 17:42  London Waterloo                         -     On time
## 17:43  London Paddington                       -     On time
## 17:43  Swansea                                 -     On time
## 17:46  London Paddington                       -     On time
## 17:50  Gatwick Airport                         -     On time
##        via Guildford                           
## 17:52  Ealing Broadway                         -     On time
## 17:52  Southampton Central                     -     On time
## 17:57  Basingstoke                             -     On time
## 17:57  Taunton                                 -     On time
## 17:58  Didcot Parkway                          -     On time
## 17:58  London Paddington                       -     On time
## 18:00  Hereford                                -     On time
## 18:00  London Paddington                       -     On time
## 18:03  Plymouth                                -     On time
## 18:05  Ealing Broadway                         -     On time
## 18:07  Newbury                                 -     On time
## 18:08  Ealing Broadway                         -     On time
## 18:12  London Paddington                       -     On time
## 18:12  London Waterloo                         -     On time
## 18:13  Carmarthen                              -     On time
## 18:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 18:20  Redhill                                 -     On time
## 18:22  Ealing Broadway                         -     On time
## 18:26  London Paddington                       -     On time
## 18:28  Bristol Temple Meads                    -     On time
## 18:28  London Paddington                       -     On time
## 18:29  Penzance                                -     On time
## 18:32  Basingstoke                             -     On time
## 18:32  Didcot Parkway                          -     On time
## 18:32  London Paddington                       -     On time
## 18:33  Ealing Broadway                         -     On time
## 18:40  Ealing Broadway                         -     On time
## 18:42  London Waterloo                         -     On time
## 18:43  London Paddington                       -     On time
## 18:43  Swansea                                 -     On time
## 18:49  London Paddington                       -     On time
## 18:52  Ealing Broadway                         -     On time
## 18:57  Didcot Parkway                          -     On time
## 18:58  London Paddington                       -     On time
## 18:59  Weston-super-Mare                       -     On time
## 19:00  London Paddington                       -     On time
## 19:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 19:01  Plymouth                                -     On time
## 19:04  Ealing Broadway                         -     On time
## 17:05  Heathrow Central Bus Stn                -     On time
## 17:40  Heathrow Central Bus Stn                -     On time
## 18:15  Heathrow Central Bus Stn                -     On time
## 19:00  Heathrow Central Bus Stn                -     On time
```
