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

## Example (Last rendered on 2022-12-17 10:04)

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
## Reading (RDG) Station Board on 2022-12-17 10:04:04
## Time   From                                    Plat  Expected
## 09:40  Bristol Temple Meads                    10    10:02
## 09:56  London Paddington                       9     10:07
## 09:58  Bristol Parkway                         10A   10:16
## 10:09  London Paddington                       14    On time
## 10:10  Bristol Temple Meads                    10    10:43
## 10:14  London Paddington                       9B    10:19
## 10:23  Oxford                                  11    On time
## 10:25  London Paddington                       9     10:49
## 10:39  London Paddington                       14    On time
## 10:40  Plymouth                                10A   10:53
## 10:44  Birmingham New Street                   7     On time
## 10:46  London Paddington                       9     On time
## 10:53  Bristol Parkway                         11A   11:09
## 10:55  London Paddington                       8     On time
## 10:56  Basingstoke                             2     On time
## 11:03  Didcot Parkway                          15    On time
## 11:05  Southampton Central                     8     On time
## 11:09  London Paddington                       14    11:17
## 11:10  Bristol Temple Meads                    10    Delayed
## 11:14  London Paddington                       9B    On time
## 11:24  Oxford                                  10    On time
## 11:25  London Paddington                       9     On time
## 11:39  London Paddington                       14    On time
## 11:41  Plymouth                                10    On time
## 11:46  London Paddington                       9     On time
## 11:47  Manchester Piccadilly                   8     On time
## 11:50  Basingstoke                             2     On time
## 11:51  Bristol Parkway                         10    12:06
## 11:55  London Paddington                       9     On time
## 11:59  Didcot Parkway                          15    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-17 10:04:08
## Time   To                                      Plat  Expected
## 09:43  London Paddington                       10    10:04
## 09:58  Plymouth                                9     10:08
##        via Bristol                             
## 09:59  London Paddington                       10A   10:17
## 10:12  London Paddington                       10    10:44
## 10:12  Manchester Piccadilly                   7B    On time
## 10:14  Bristol Parkway                         9B    10:21
## 10:26  London Paddington                       11    On time
## 10:27  Bristol Temple Meads                    9     10:50
## 10:27  Ealing Broadway                         14    On time
## 10:32  Basingstoke                             2     On time
## 10:42  London Paddington                       10A   10:54
## 10:48  Oxford                                  9     On time
## 10:50  Didcot Parkway                          15    On time
## 10:52  Southampton Central                     7     On time
## 10:55  London Paddington                       11A   11:10
## 10:57  Bristol Temple Meads                    8     On time
## 10:57  Ealing Broadway                         14    On time
## 11:12  London Paddington                       10    Delayed
## 11:14  Bristol Parkway                         9B    On time
## 11:16  Birmingham New Street                   8     On time
##        via Coventry                            
## 11:26  London Paddington                       10    On time
## 11:27  Bristol Temple Meads                    9     On time
## 11:27  Ealing Broadway                         14    On time
## 11:32  Basingstoke                             2     On time
## 11:43  London Paddington                       10    On time
## 11:49  Oxford                                  9     On time
## 11:53  Didcot Parkway                          15    On time
## 11:55  London Paddington                       10    12:07
## 11:57  Ealing Broadway                         14    On time
## 11:57  Plymouth                                9     On time
##        via Bristol
```
