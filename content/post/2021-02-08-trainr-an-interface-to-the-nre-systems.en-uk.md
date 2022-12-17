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

## Example (Last rendered on 2022-12-17 12:04)

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
## Reading (RDG) Station Board on 2022-12-17 12:04:09
## Time   From                                    Plat  Expected
## 11:46  London Paddington                       9B    12:08
## 11:51  Bristol Parkway                         10A   12:21
## 12:09  London Paddington                       14    On time
## 12:10  Bristol Temple Meads                    10    12:15
## 12:14  London Paddington                       9B    12:25
## 12:24  Oxford                                  10    On time
## 12:25  London Paddington                       9     On time
## 12:39  London Paddington                       14    On time
## 12:39  Manchester Piccadilly                   7     On time
## 12:40  Bristol Temple Meads                    10    12:42
## 12:46  London Paddington                       9     On time
## 12:47  Bristol Parkway                         10    Delayed
## 12:51  Basingstoke                             2     On time
## 12:54  London Paddington                       9     On time
## 13:01  Didcot Parkway                          15    On time
## 13:05  Southampton Central                     13B   On time
## 13:09  London Paddington                       14    On time
## 13:10  Bristol Temple Meads                    10    13:22
## 13:14  London Paddington                       9B    On time
## 13:24  Oxford                                  10    On time
## 13:25  London Paddington                       9     On time
## 13:39  London Paddington                       14    On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:39  Plymouth                                10    On time
## 13:46  London Paddington                       9     On time
## 13:50  Bristol Parkway                         10    14:06
## 13:56  London Paddington                       9     On time
## 13:58  Basingstoke                             2     On time
## 14:03  Didcot Parkway                          15    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-17 12:04:13
## Time   To                                      Plat  Expected
## 11:49  Oxford                                  9B    12:09
## 11:55  London Paddington                       10A   12:22
## 12:07  Manchester Piccadilly                   12    On time
## 12:12  London Paddington                       10    12:16
## 12:14  Bristol Parkway                         9B    12:25
## 12:26  London Paddington                       10    On time
## 12:27  Bristol Temple Meads                    9     On time
## 12:27  Ealing Broadway                         14    On time
## 12:32  Basingstoke                             2     On time
## 12:42  London Paddington                       10    12:42
## 12:48  London Paddington                       10    Delayed
## 12:49  Oxford                                  9     On time
## 12:52  Southampton Central                     7     On time
## 12:57  Bristol Temple Meads                    9     On time
## 12:57  Didcot Parkway                          15    On time
## 12:57  Ealing Broadway                         14    On time
## 13:12  London Paddington                       10    13:23
## 13:14  Bristol Parkway                         9B    On time
## 13:15  Birmingham New Street                   13B   On time
##        via Coventry                            
## 13:26  London Paddington                       10    On time
## 13:27  Basingstoke                             2     On time
## 13:27  Bristol Temple Meads                    9     On time
## 13:27  Ealing Broadway                         14    On time
## 13:42  London Paddington                       10    On time
## 13:48  Oxford                                  9     On time
## 13:55  Didcot Parkway                          15    On time
## 13:55  London Paddington                       10    14:07
## 13:57  Ealing Broadway                         14    On time
## 13:58  Plymouth                                9     On time
##        via Bristol
```
