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

## Example (Last rendered on 2021-03-20 22:08)

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
## Reading (RDG) Station Board on 2021-03-20 22:08:20
## Time   From                                    Plat  Expected
## 22:05  Didcot Parkway                          15    On time
## 22:08  Weston-super-Mare                       10    22:05
## 22:15  London Paddington                       14    On time
## 22:16  London Paddington                       8B    On time
## 22:22  Newbury                                 1     On time
## 22:28  London Paddington                       9     On time
## 22:36  Cheltenham Spa                          10A   On time
## 22:41  Manchester Piccadilly                   8B    On time
## 22:45  London Paddington                       14    On time
## 22:46  London Paddington                       12    On time
## 22:50  London Paddington                       10    On time
## 22:57  Basingstoke                             2     On time
## 22:58  London Paddington                       9     On time
## 23:01  Didcot Parkway                          15    On time
## 23:04  Hereford                                13A   On time
## 23:10  Newbury                                 7B    On time
## 23:15  London Paddington                       10    On time
## 23:38  London Paddington                       8     On time
## 23:45  London Paddington                       9     On time
## 23:46  London Paddington                       7     On time
## 23:51  Taunton                                 11    On time
## 00:01  London Paddington                       8     On time
## 00:06  Basingstoke                             8     On time
## 22:16  Wokingham                               BUS   On time
## 22:23  Wokingham                               BUS   On time
## 22:29  Wokingham                               BUS   On time
## 23:00  Wokingham                               BUS   On time
## 23:03  Wokingham                               BUS   On time
## 23:13  Wokingham                               BUS   On time
## 23:23  Wokingham                               BUS   On time
## 23:29  Wokingham                               BUS   On time
## 00:03  Wokingham                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-20 22:08:22
## Time   To                                      Plat  Expected
## 22:09  London Paddington                       10    On time
## 22:10  Newbury                                 1     On time
## 22:15  Ealing Broadway                         15    On time
## 22:18  Worcester Shrub Hill                    8B    On time
## 22:30  Bristol Parkway                         9     On time
## 22:33  Ealing Broadway                         14    On time
## 22:39  London Paddington                       10A   On time
## 22:52  Southampton Central                     8B    On time
## 23:00  Bristol Parkway                         9     On time
## 23:01  Ealing Broadway                         14    On time
## 23:05  Basingstoke                             2     On time
## 23:05  Didcot Parkway                          12    On time
## 23:06  London Paddington                       13A   On time
## 23:10  Newbury                                 1     On time
## 23:48  Didcot Parkway                          7     On time
## 23:54  London Paddington                       11    On time
## 00:02  Bristol Parkway                         8     On time
## 22:14  Wokingham                               BUS   On time
## 22:20  Wokingham                               BUS   On time
## 22:39  Wokingham                               BUS   On time
## 22:45  Wokingham                               BUS   On time
## 23:15  Wokingham                               BUS   On time
## 23:20  Wokingham                               BUS   On time
## 23:34  Wokingham                               BUS   On time
## 23:52  Wokingham                               BUS   On time
```
