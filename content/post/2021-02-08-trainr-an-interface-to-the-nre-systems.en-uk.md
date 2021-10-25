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

## Example (Last rendered on 2021-10-25 04:03)

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
## Reading (RDG) Station Board on 2021-10-25 04:04:01
## Time   From                                    Plat  Expected
## 05:35  Didcot Parkway                          -     On time
## 05:36  London Paddington                       -     On time
## 05:46  Oxford                                  -     On time
## 05:47  London Paddington                       -     On time
## 05:58  Bristol Temple Meads                    -     On time
## 05:58  London Paddington                       -     On time
## 05:59  Newbury                                 -     On time
## 06:12  Didcot Parkway                          -     On time
## 06:13  London Paddington                       -     On time
## 06:14  Newbury                                 -     On time
## 06:14  Staines                                 -     On time
## 06:16  London Paddington                       -     On time
## 06:25  Cheltenham Spa                          -     On time
## 06:28  Oxford                                  -     On time
## 06:30  Basingstoke                             -     Cancelled
## 06:31  Bristol Temple Meads                    -     On time
## 06:41  Bedwyn                                  -     On time
## 06:43  London Paddington                       -     On time
## 06:44  London Waterloo                         -     On time
## 06:46  Didcot Parkway                          -     On time
## 06:47  London Paddington                       -     On time
## 06:48  Swansea                                 -     On time
## 06:51  Basingstoke                             -     Cancelled
## 06:51  Gatwick Airport                         -     On time
## 06:53  Worcester Shrub Hill                    -     On time
## 06:55  London Paddington                       -     On time
## 06:58  London Paddington                       -     On time
## 06:59  Didcot Parkway                          -     On time
## 07:00  London Paddington                       -     On time
## 07:00  Newbury                                 -     On time
## 06:03  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-10-25 04:04:04
## Time   To                                      Plat  Expected
## 05:08  London Paddington                       -     On time
## 05:12  Bedwyn                                  -     On time
## 05:14  Newbury                                 -     On time
## 05:18  Basingstoke                             -     Cancelled
## 05:30  Gatwick Airport                         -     On time
##        via Guildford                           
## 05:36  London Paddington                       -     On time
## 05:38  Didcot Parkway                          -     On time
## 05:38  Oxford                                  -     On time
## 05:40  Basingstoke                             -     Cancelled
## 05:42  London Waterloo                         -     On time
## 05:48  London Paddington                       -     On time
## 05:49  Didcot Parkway                          -     On time
## 05:49  Swansea                                 -     On time
## 05:50  Newbury                                 -     On time
## 05:51  London Paddington                       -     On time
## 05:54  Redhill                                 -     On time
## 06:00  London Paddington                       -     On time
## 06:00  Worcester Shrub Hill                    -     On time
##        via Gloucester                          
## 06:03  London Paddington                       -     On time
## 06:08  London Waterloo                         -     On time
## 06:13  Newbury                                 -     On time
## 06:15  London Paddington                       -     On time
## 06:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 06:18  Great Malvern                           -     On time
## 06:19  Basingstoke                             -     Cancelled
## 06:19  London Paddington                       -     On time
## 06:22  London Paddington                       -     On time
## 06:22  Oxford                                  -     On time
## 06:25  Gatwick Airport                         -     On time
##        via Guildford                           
## 06:28  London Paddington                       -     On time
## 06:34  London Paddington                       -     On time
## 06:36  London Paddington                       -     On time
## 06:37  Newbury                                 -     On time
## 06:38  London Waterloo                         -     On time
## 06:40  Basingstoke                             -     Cancelled
## 06:42  London Paddington                       -     On time
## 06:46  Gatwick Airport                         -     On time
##        via Guildford                           
## 06:48  London Paddington                       -     On time
## 06:50  London Paddington                       -     On time
## 06:52  London Paddington                       -     On time
## 06:54  Didcot Parkway                          -     On time
## 06:56  London Paddington                       -     On time
## 06:57  Basingstoke                             -     Cancelled
## 06:57  Bristol Temple Meads                    -     On time
## 07:01  London Paddington                       -     On time
## 07:03  London Paddington                       -     On time
## 07:03  Penzance                                -     On time
## 06:00  Heathrow Central Bus Stn                -     On time
## 07:00  Heathrow Central Bus Stn                -     On time
```
