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

## Example (Last rendered on 2022-04-05 22:03)

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
## Reading (RDG) Station Board on 2022-04-05 22:03:35
## Time   From                                    Plat  Expected
## 22:59  Worcester Foregate Street               -     On time
## 23:03  Basingstoke                             -     On time
## 23:11  Penzance                                -     On time
## 23:12  London Waterloo                         -     23:20
## 23:13  London Paddington                       -     On time
## 23:14  London Paddington                       -     On time
## 23:16  Gatwick Airport                         -     On time
## 23:17  London Paddington                       -     On time
## 23:22  Didcot Parkway                          -     On time
## 23:22  Newbury                                 -     On time
## 23:27  London Paddington                       -     On time
## 23:28  Basingstoke                             -     On time
## 23:35  Oxford                                  -     On time
## 23:41  London Waterloo                         -     On time
## 23:43  London Paddington                       -     On time
## 23:46  Didcot Parkway                          -     On time
## 23:49  Basingstoke                             -     On time
## 23:50  Birmingham New Street                   -     On time
## 23:57  London Paddington                       -     On time
## 00:03  London Paddington                       -     On time
## 00:08  Bedwyn                                  -     Cancelled
## 00:11  London Waterloo                         -     On time
## 00:17  Gatwick Airport                         -     On time
## 00:23  London Paddington                       -     On time
## 00:31  Basingstoke                             -     On time
## 00:40  Henley-on-Thames                        -     On time
## 00:41  London Waterloo                         -     On time
## 00:41  Oxford                                  -     On time
## 00:44  Gatwick Airport                         -     On time
## 00:48  London Paddington                       -     On time
## 23:35  Heathrow Central Bus Stn                -     On time
## 00:35  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-04-05 22:03:37
## Time   To                                      Plat  Expected
## 23:01  London Paddington                       -     On time
## 23:02  London Waterloo                         -     On time
## 23:03  Bedwyn                                  -     On time
## 23:19  London Paddington                       -     On time
## 23:19  Swansea                                 -     On time
## 23:23  Ealing Broadway                         -     On time
## 23:28  Oxford                                  -     On time
## 23:32  Didcot Parkway                          -     On time
## 23:33  Gatwick Airport                         -     On time
##        via Guildford                           
## 23:34  Basingstoke                             -     On time
## 23:38  London Paddington                       -     On time
## 23:52  Ascot                                   -     On time
## 00:05  Bristol Temple Meads                    -     On time
## 00:08  Oxford                                  -     On time
## 00:17  Newbury                                 -     On time
## 00:18  London Paddington                       -     On time
## 00:26  Didcot Parkway                          -     On time
## 00:43  London Paddington                       -     On time
## 00:49  Penzance                                -     On time
## 00:16  Chippenham                              -     On time
```
