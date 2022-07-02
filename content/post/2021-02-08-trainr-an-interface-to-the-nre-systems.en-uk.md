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

## Example (Last rendered on 2022-07-02 22:03)

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
## Reading (RDG) Station Board on 2022-07-02 22:03:56
## Time   From                                    Plat  Expected
## 23:03  London Paddington                       10    23:06
## 23:04  Hereford                                13A   23:30
## 23:04  Redhill                                 5     23:06
## 23:10  Newbury                                 8     On time
## 23:11  Ascot                                   4     On time
## 23:11  Penzance                                11    On time
## 23:16  London Paddington                       7A    On time
## 23:26  Didcot Parkway                          8B    On time
## 23:29  London Paddington                       9     23:33
## 23:32  Oxford                                  10    On time
## 23:36  London Paddington                       9     On time
## 23:41  Ascot                                   6     On time
## 23:47  London Paddington                       7     On time
## 23:51  Bristol Temple Meads                    10    00:32
## 23:55  London Paddington                       8     On time
## 00:02  Gatwick Airport                         6     On time
## 00:08  Basingstoke                             1     On time
## 00:10  Newbury                                 3     On time
## 00:11  Ascot                                   6     On time
## 00:11  London Paddington                       8     On time
## 00:12  Didcot Parkway                          7     On time
## 00:25  London Paddington                       8     On time
## 00:43  Ascot                                   6     On time
## 00:45  Gatwick Airport                         8     On time
## 23:15  Heathrow Central Bus Stn                BUS   On time
## 00:15  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-07-02 22:03:58
## Time   To                                      Plat  Expected
## 23:05  Basingstoke                             2     On time
## 23:06  London Paddington                       13A   23:31
## 23:10  Newbury                                 1     On time
## 23:13  London Paddington                       11    On time
## 23:15  Ascot                                   6     On time
## 23:17  Ealing Broadway                         9     On time
## 23:21  Ealing Broadway                         10    On time
## 23:32  Oxford                                  9     23:34
## 23:34  Gatwick Airport                         5     On time
##        via Guildford                           
## 23:34  London Paddington                       10    On time
## 23:48  Didcot Parkway                          7     On time
## 23:52  Ascot                                   6     On time
## 23:55  London Paddington                       10    00:33
## 00:05  Bristol Temple Meads                    8     On time
## 00:12  Oxford                                  8     On time
## 00:18  Newbury                                 1     On time
## 00:19  London Paddington                       7     On time
```
