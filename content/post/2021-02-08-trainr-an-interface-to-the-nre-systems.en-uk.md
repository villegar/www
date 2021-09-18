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

## Example (Last rendered on 2021-09-18 22:03)

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
## Reading (RDG) Station Board on 2021-09-18 22:03:49
## Time   From                                    Plat  Expected
## 22:32  Oxford                                  11A   23:01
## 22:44  London Paddington                       7     On time
## 22:55  London Paddington                       8     23:00
## 23:04  Hereford                                11A   23:12
## 23:10  Newbury                                 12B   On time
## 23:11  Penzance                                -     Cancelled
## 23:14  London Paddington                       14    On time
## 23:14  London Waterloo                         4     On time
## 23:37  London Paddington                       13    On time
## 23:45  London Paddington                       10    On time
## 23:46  London Paddington                       7     On time
## 23:46  London Waterloo                         6     On time
## 23:52  Basingstoke                             12    On time
## 23:52  Taunton                                 10    On time
## 00:02  London Paddington                       9     On time
## 00:08  Basingstoke                             12    On time
## 00:08  Didcot Parkway                          10    On time
## 00:10  Newbury                                 1     On time
## 00:14  London Waterloo                         6     On time
## 00:22  London Paddington                       14    On time
## 00:29  London Paddington                       15    On time
## 00:44  London Waterloo                         4     On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
## 23:05  Guildford                               BUS   On time
## 23:45  Guildford                               BUS   On time
## 23:59  Guildford                               BUS   On time
## 00:03  Heathrow Central Bus Stn                BUS   On time
## 00:50  Guildford                               BUS   On time
## 01:00  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-09-18 22:03:51
## Time   To                                      Plat  Expected
## 22:34  London Paddington                       11A   23:06
## 22:57  Bristol Parkway                         8     23:03
## 23:05  Basingstoke                             2     On time
## 23:05  Didcot Parkway                          7     On time
## 23:06  London Paddington                       11A   23:13
## 23:10  Newbury                                 1     On time
## 23:15  London Paddington                       -     Cancelled
## 23:15  London Waterloo                         6     On time
## 23:48  Didcot Parkway                          7     On time
## 23:52  Staines                                 6     On time
## 23:54  London Paddington                       10    On time
## 00:03  Bristol Parkway                         9     On time
## 00:19  Slough                                  10    On time
## 00:20  Newbury                                 -     Cancelled
## 23:35  Gatwick Airport                         BUS   On time
##        via Guildford
```
