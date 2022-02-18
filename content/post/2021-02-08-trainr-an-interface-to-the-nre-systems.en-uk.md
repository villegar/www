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

## Example (Last rendered on 2022-02-18 16:04)

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
## Reading (RDG) Station Board on 2022-02-18 16:04:33
## Time   From                                    Plat  Expected
## 15:57  Plymouth                                -     Cancelled
## 16:07  Didcot Parkway                          -     Cancelled
## 16:09  Bristol Temple Meads                    -     Cancelled
## 16:10  London Waterloo                         -     Cancelled
## 16:11  London Paddington                       -     Cancelled
## 16:13  London Paddington                       -     Cancelled
## 16:16  Cardiff Central                         -     Cancelled
## 16:18  Basingstoke                             -     Cancelled
## 16:22  Newbury                                 -     Cancelled
## 16:24  Oxford                                  -     Cancelled
## 16:25  London Paddington                       -     Cancelled
## 16:29  Cheltenham Spa                          -     Cancelled
## 16:31  Didcot Parkway                          -     Cancelled
## 16:33  London Paddington                       -     Cancelled
## 16:33  Redhill                                 -     Cancelled
## 16:34  Bedwyn                                  -     Cancelled
## 16:34  Bedwyn                                  -     Cancelled
## 16:39  Bristol Temple Meads                    -     Cancelled
## 16:39  Paignton                                -     Cancelled
## 16:41  London Paddington                       -     Cancelled
## 16:41  London Waterloo                         -     Cancelled
## 16:43  London Paddington                       -     Cancelled
## 16:45  Swansea                                 -     Cancelled
## 16:46  London Paddington                       -     Cancelled
## 16:50  Basingstoke                             -     Cancelled
## 16:54  Worcester Foregate Street               -     Cancelled
## 16:56  London Paddington                       -     Cancelled
## 16:56  London Waterloo                         -     Cancelled
## 16:58  London Paddington                       -     Cancelled
## 16:59  London Paddington                       -     Cancelled
## 17:01  Penzance                                -     Cancelled
## 17:03  Gatwick Airport                         -     Cancelled
## 17:05  Exeter St Davids                        -     Cancelled
## 17:06  Didcot Parkway                          -     Cancelled
## 17:09  Bristol Temple Meads                    -     Cancelled
## 17:11  London Paddington                       -     Cancelled
## 17:11  London Waterloo                         -     Cancelled
## 17:13  London Paddington                       -     Cancelled
## 17:22  Bedwyn                                  -     Cancelled
## 17:24  Oxford                                  -     Cancelled
## 17:25  London Paddington                       -     Cancelled
## 17:26  Basingstoke                             -     Cancelled
## 17:29  Cheltenham Spa                          -     Cancelled
## 17:33  Bedwyn                                  -     Cancelled
## 17:33  Newbury                                 -     Cancelled
## 17:35  Didcot Parkway                          -     Cancelled
## 17:37  London Paddington                       -     Cancelled
## 17:38  Bristol Temple Meads                    -     Cancelled
## 17:39  Exeter St Davids                        -     Cancelled
## 17:40  London Waterloo                         -     Cancelled
## 17:41  Birmingham New Street                   -     Cancelled
## 17:41  London Paddington                       -     Cancelled
## 17:43  London Paddington                       -     Cancelled
## 17:43  Swansea                                 -     Cancelled
## 17:44  Redhill                                 -     Cancelled
## 17:46  Basingstoke                             -     Cancelled
## 17:55  London Paddington                       -     Cancelled
## 17:56  Hereford                                -     Cancelled
## 17:58  London Paddington                       -     Cancelled
## 18:01  London Paddington                       -     Cancelled
## 18:02  Exeter St Davids                        -     Cancelled
## 18:02  Gatwick Airport                         -     Cancelled
## 18:02  Plymouth                                -     Cancelled
## 18:03  Didcot Parkway                          -     Cancelled
## 16:21  Heathrow Central Bus Stn                BUS   On time
## 17:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-18 16:04:38
## Time   To                                      Plat  Expected
## 16:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 16:04  London Paddington                       -     Cancelled
## 16:07  Basingstoke                             -     Cancelled
## 16:12  Bedwyn                                  -     Cancelled
## 16:12  London Paddington                       -     Cancelled
## 16:12  London Waterloo                         -     Cancelled
## 16:12  Newbury                                 -     Delayed
## 16:13  Swansea                                 -     Cancelled
## 16:18  London Paddington                       -     Cancelled
## 16:19  Great Malvern                           -     Cancelled
## 16:20  Redhill                                 -     Cancelled
## 16:23  London Paddington                       -     Cancelled
## 16:25  Didcot Parkway                          -     Cancelled
## 16:27  Bristol Temple Meads                    -     Cancelled
## 16:27  London Paddington                       -     Cancelled
## 16:29  Penzance                                -     Cancelled
## 16:32  London Paddington                       -     Cancelled
## 16:33  Basingstoke                             -     Cancelled
## 16:33  Ealing Broadway                         -     Cancelled
## 16:37  Newbury                                 -     Cancelled
## 16:42  London Paddington                       -     Cancelled
## 16:42  London Waterloo                         -     Cancelled
## 16:43  Swansea                                 -     Cancelled
## 16:45  Bedwyn                                  -     Cancelled
## 16:45  London Paddington                       -     Cancelled
## 16:47  London Paddington                       -     Cancelled
## 16:48  Oxford                                  -     Cancelled
## 16:50  Didcot Parkway                          -     Cancelled
## 16:50  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 16:53  London Waterloo                         -     Cancelled
## 16:57  London Paddington                       -     Cancelled
## 16:58  Bristol Temple Meads                    -     Cancelled
## 17:02  Plymouth                                -     Cancelled
## 17:03  Ealing Broadway                         -     Cancelled
## 17:05  London Paddington                       -     Cancelled
## 17:05  London Paddington                       -     Cancelled
## 17:10  Newbury                                 -     On time
## 17:11  London Paddington                       -     Cancelled
## 17:12  Bedwyn                                  -     Cancelled
## 17:12  London Waterloo                         -     Cancelled
## 17:13  Swansea                                 -     Cancelled
## 17:15  Basingstoke                             -     Cancelled
## 17:15  Birmingham New Street                   -     Cancelled
##        via Coventry                            
## 17:20  Redhill                                 -     Cancelled
## 17:22  Ealing Broadway                         -     Cancelled
## 17:24  London Paddington                       -     Cancelled
## 17:25  Didcot Parkway                          -     On time
## 17:27  Bristol Temple Meads                    -     Cancelled
## 17:27  London Paddington                       -     Cancelled
## 17:29  Penzance                                -     Cancelled
## 17:32  London Paddington                       -     Cancelled
## 17:34  Basingstoke                             -     Cancelled
## 17:38  Newbury                                 -     Cancelled
## 17:41  London Paddington                       -     Cancelled
## 17:42  London Waterloo                         -     Cancelled
## 17:43  London Paddington                       -     Cancelled
## 17:43  Swansea                                 -     Cancelled
## 17:46  London Paddington                       -     Cancelled
## 17:50  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 17:52  Ealing Broadway                         -     Cancelled
## 17:57  Basingstoke                             -     Cancelled
## 17:57  Taunton                                 -     Cancelled
## 17:58  Didcot Parkway                          -     On time
## 18:00  Hereford                                -     Cancelled
## 18:00  London Paddington                       -     Cancelled
## 18:02  London Paddington                       -     Cancelled
## 18:02  London Paddington                       -     Cancelled
## 18:03  Plymouth                                -     Cancelled
## 17:00  Heathrow Central Bus Stn                BUS   On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
```
