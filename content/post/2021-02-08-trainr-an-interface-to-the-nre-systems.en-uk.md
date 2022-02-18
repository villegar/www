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

## Example (Last rendered on 2022-02-18 18:03)

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
## Reading (RDG) Station Board on 2022-02-18 18:03:53
## Time   From                                    Plat  Expected
## 17:56  Hereford                                -     Cancelled
## 17:58  London Paddington                       -     Cancelled
## 18:01  London Paddington                       -     Cancelled
## 18:02  Exeter St Davids                        -     Cancelled
## 18:02  Gatwick Airport                         -     Cancelled
## 18:02  Plymouth                                -     Cancelled
## 18:03  Didcot Parkway                          -     Cancelled
## 18:09  Bristol Temple Meads                    -     Cancelled
## 18:10  London Waterloo                         -     Cancelled
## 18:11  London Paddington                       -     Cancelled
## 18:13  London Paddington                       -     Cancelled
## 18:20  Basingstoke                             -     Cancelled
## 18:25  Newbury                                 -     Cancelled
## 18:26  London Paddington                       -     Cancelled
## 18:26  Oxford                                  -     Cancelled
## 18:29  Didcot Parkway                          -     Cancelled
## 18:30  Cheltenham Spa                          -     Cancelled
## 18:35  Bedwyn                                  -     Cancelled
## 18:35  Newbury                                 -     On time
## 18:40  Bristol Temple Meads                    -     Cancelled
## 18:40  London Waterloo                         -     Cancelled
## 18:42  London Paddington                       -     Cancelled
## 18:43  London Paddington                       -     Cancelled
## 18:44  London Paddington                       -     Cancelled
## 18:45  Redhill                                 -     Cancelled
## 18:47  Swansea                                 -     Cancelled
## 18:50  Basingstoke                             -     Cancelled
## 18:56  London Waterloo                         -     Cancelled
## 18:57  Great Malvern                           -     Cancelled
## 18:57  London Paddington                       -     Cancelled
## 18:57  Penzance                                -     Cancelled
## 18:58  Exeter St Davids                        -     Cancelled
## 18:59  London Paddington                       -     Cancelled
## 19:04  Basingstoke                             -     Cancelled
## 19:05  Didcot Parkway                          -     Cancelled
## 19:05  Gatwick Airport                         -     Cancelled
## 19:10  Weston-super-Mare                       -     Cancelled
## 19:11  London Paddington                       -     Cancelled
## 19:13  London Paddington                       -     Cancelled
## 19:15  London Paddington                       13    On time
## 19:15  London Waterloo                         -     Cancelled
## 19:15  Newbury                                 -     On time
## 19:22  Newbury                                 -     Cancelled
## 19:25  Worcester Foregate Street               -     Cancelled
## 19:26  London Paddington                       -     Cancelled
## 19:28  Didcot Parkway                          -     Cancelled
## 19:33  Redhill                                 -     Cancelled
## 19:34  Basingstoke                             -     Cancelled
## 19:34  Bedwyn                                  -     Cancelled
## 19:34  London Paddington                       -     Cancelled
## 19:39  Bristol Temple Meads                    -     Cancelled
## 19:40  London Waterloo                         -     Cancelled
## 19:41  Birmingham New Street                   -     Cancelled
## 19:41  London Paddington                       -     Cancelled
## 19:43  London Paddington                       -     Cancelled
## 19:45  London Paddington                       -     Cancelled
## 19:46  Swansea                                 -     Cancelled
## 19:53  London Paddington                       -     Cancelled
## 19:54  Worcester Foregate Street               -     Cancelled
## 19:55  Exeter St Davids                        -     Cancelled
## 19:55  Plymouth                                -     Cancelled
## 19:56  London Paddington                       -     Cancelled
## 19:57  Didcot Parkway                          -     Cancelled
## 19:58  London Waterloo                         -     Cancelled
## 20:00  Basingstoke                             -     Cancelled
## 18:21  Heathrow Central Bus Stn                BUS   On time
## 19:19  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-18 18:03:57
## Time   To                                      Plat  Expected
## 18:00  Hereford                                -     Cancelled
## 18:00  London Paddington                       -     Cancelled
## 18:02  London Paddington                       -     Cancelled
## 18:02  London Paddington                       -     Cancelled
## 18:03  Plymouth                                -     Cancelled
## 18:07  Bedwyn                                  -     Cancelled
## 18:07  Newbury                                 -     Delayed
## 18:12  London Paddington                       -     Cancelled
## 18:12  London Waterloo                         -     Cancelled
## 18:13  Carmarthen                              -     Cancelled
## 18:20  Redhill                                 -     Cancelled
## 18:22  Ealing Broadway                         -     Cancelled
## 18:26  London Paddington                       -     Cancelled
## 18:28  Bristol Temple Meads                    -     Cancelled
## 18:28  London Paddington                       -     Cancelled
## 18:29  Penzance                                -     Cancelled
## 18:32  Basingstoke                             -     Cancelled
## 18:32  Didcot Parkway                          -     Cancelled
## 18:32  London Paddington                       -     Cancelled
## 18:42  London Waterloo                         -     Cancelled
## 18:43  London Paddington                       -     Cancelled
## 18:43  Swansea                                 -     Cancelled
## 18:49  London Paddington                       -     Cancelled
## 18:52  Ealing Broadway                         -     Cancelled
## 18:52  Staines                                 -     Cancelled
## 18:57  Didcot Parkway                          -     Cancelled
## 18:58  London Paddington                       -     Cancelled
## 18:58  London Paddington                       -     Cancelled
## 18:59  Weston-super-Mare                       -     Cancelled
## 19:00  London Paddington                       -     Cancelled
## 19:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 19:01  Plymouth                                -     Cancelled
## 19:05  Basingstoke                             -     Cancelled
## 19:10  Newbury                                 -     Delayed
## 19:12  Bedwyn                                  -     Cancelled
## 19:12  London Waterloo                         -     Cancelled
## 19:13  London Paddington                       -     Cancelled
## 19:13  Swansea                                 -     Cancelled
## 19:15  Birmingham New Street                   -     Cancelled
##        via Coventry                            
## 19:20  Redhill                                 -     Cancelled
## 19:22  Ealing Broadway                         14    On time
## 19:25  Basingstoke                             -     Cancelled
## 19:25  London Paddington                       -     Cancelled
## 19:27  Bristol Temple Meads                    -     Cancelled
## 19:27  London Paddington                       -     Cancelled
## 19:30  Didcot Parkway                          -     Cancelled
## 19:31  Penzance                                -     Cancelled
## 19:36  Bedwyn                                  -     Cancelled
## 19:36  London Waterloo                         -     Cancelled
## 19:41  London Paddington                       -     Cancelled
## 19:42  Newbury                                 -     On time
## 19:43  Swansea                                 -     Cancelled
## 19:49  London Paddington                       -     Cancelled
## 19:52  Ealing Broadway                         13    On time
## 19:55  London Paddington                       -     Cancelled
## 19:55  London Paddington                       -     Cancelled
## 19:55  Oxford                                  -     Cancelled
## 19:57  Basingstoke                             -     Cancelled
## 19:57  Didcot Parkway                          -     Cancelled
## 19:58  London Paddington                       -     Cancelled
## 19:58  Weston-super-Mare                       -     Cancelled
## 20:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 19:00  Heathrow Central Bus Stn                BUS   On time
## 20:00  Heathrow Central Bus Stn                BUS   On time
```
