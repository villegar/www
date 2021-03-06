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

## Example (Last rendered on 2021-03-06 22:11)

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
## Reading (RDG) Station Board on 2021-03-06 22:11:42
## Time   From                                    Plat  Expected
## 21:50  Port Talbot Parkway                     -     22:11
## 22:05  Didcot Parkway                          -     On time
## 22:08  Bristol Temple Meads                    -     22:04
## 22:13  London Paddington                       -     22:05
## 22:16  London Paddington                       -     On time
## 22:21  London Paddington                       -     On time
## 22:22  Newbury                                 -     On time
## 22:36  Cheltenham Spa                          -     Cancelled
## 22:41  Manchester Piccadilly                   -     On time
## 22:43  London Paddington                       -     On time
## 22:44  London Paddington                       -     On time
## 22:50  London Paddington                       -     On time
## 22:53  London Paddington                       -     On time
## 22:57  Basingstoke                             -     On time
## 23:01  Didcot Parkway                          -     On time
## 23:03  Gatwick Airport                         -     On time
## 23:04  Hereford                                -     On time
## 23:10  Newbury                                 -     On time
## 23:13  London Paddington                       -     On time
## 23:31  London Paddington                       -     On time
## 23:43  London Paddington                       -     On time
## 23:46  London Paddington                       -     On time
## 23:51  Taunton                                 -     On time
## 00:01  London Paddington                       -     On time
## 00:02  Gatwick Airport                         -     On time
## 00:06  Basingstoke                             -     On time
## 22:12  Ascot                                   -     On time
## 22:27  Ascot                                   -     On time
## 22:42  Ascot                                   -     On time
## 22:57  Ascot                                   -     On time
## 23:12  Ascot                                   -     On time
## 23:27  Ascot                                   -     On time
## 23:42  Ascot                                   -     On time
## 23:57  Ascot                                   -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-06 22:11:44
## Time   To                                      Plat  Expected
## 21:51  London Paddington                       -     22:12
## 22:10  London Paddington                       -     On time
## 22:10  Newbury                                 -     On time
## 22:15  Ealing Broadway                         -     On time
## 22:18  Worcester Shrub Hill                    -     On time
## 22:22  Ealing Broadway                         -     On time
## 22:23  Bristol Parkway                         -     On time
## 22:39  London Paddington                       -     Cancelled
## 22:52  Ealing Broadway                         -     On time
## 22:52  Southampton Central                     -     On time
## 22:55  Bristol Parkway                         -     On time
## 23:05  Basingstoke                             -     On time
## 23:05  Didcot Parkway                          -     On time
## 23:06  London Paddington                       -     On time
## 23:10  Newbury                                 -     On time
## 23:34  Gatwick Airport                         -     On time
##        via Guildford                           
## 23:48  Didcot Parkway                          -     On time
## 23:54  London Paddington                       -     On time
## 00:02  Bristol Parkway                         -     On time
## 22:17  Ascot                                   -     On time
## 22:32  Ascot                                   -     On time
## 22:47  Ascot                                   -     On time
## 23:02  Ascot                                   -     On time
## 23:17  Ascot                                   -     On time
```
