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

## Example (Last rendered on 2022-06-24 08:07)

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
## Reading (RDG) Station Board on 2022-06-24 08:07:39
## Time   From                                    Plat  Expected
## 07:54  Oxford                                  15A   08:43
## 09:04  Redhill                                 5     09:08
## 09:11  London Paddington                       9     On time
## 09:11  Oxford                                  10    09:14
## 09:13  London Paddington                       14    On time
## 09:16  London Paddington                       9     Delayed
## 09:19  Bristol Parkway                         10    On time
## 09:26  London Paddington                       13    On time
## 09:27  London Paddington                       7     On time
## 09:33  Clapham Junction                        4     On time
## 09:37  Didcot Parkway                          12    On time
## 09:38  London Paddington                       14    On time
## 09:39  Bristol Temple Meads                    10    On time
## 09:41  London Paddington                       9     Delayed
## 09:45  Swansea                                 10    09:49
## 09:46  Basingstoke                             2     On time
## 09:53  Banbury                                 13    On time
## 09:55  Newbury                                 1     On time
## 09:55  Worcester Shrub Hill                    10A   On time
## 09:56  London Paddington                       9     On time
## 10:03  London Waterloo                         4     On time
## 10:06  Swansea                                 10    On time
## 10:07  London Paddington                       14    On time
## 10:08  Didcot Parkway                          12    On time
## 10:11  London Paddington                       9     On time
## 10:18  London Paddington                       9B    On time
## 10:33  Clapham Junction                        4     On time
## 10:36  Didcot Parkway                          13    On time
## 10:39  London Paddington                       14    On time
## 10:40  Bristol Temple Meads                    10    On time
## 10:41  London Paddington                       9     On time
## 10:43  Newbury                                 1     On time
## 10:45  Birmingham New Street                   7     On time
## 10:45  Redhill                                 5     On time
## 10:45  Swansea                                 10    On time
## 10:54  Great Malvern                           10A   On time
## 10:55  London Paddington                       8     On time
## 10:56  Basingstoke                             2     On time
## 10:58  Didcot Parkway                          13    On time
## 10:58  Plymouth                                11    On time
## 11:03  London Waterloo                         4     On time
## 09:06  Heathrow Central Bus Stn                BUS   On time
## 09:41  Heathrow Central Bus Stn                BUS   On time
## 10:16  Heathrow Central Bus Stn                BUS   On time
## 10:51  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-06-24 08:07:43
## Time   To                                      Plat  Expected
## 09:13  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:13  Newbury                                 3     On time
## 09:13  Swansea                                 9     On time
## 09:18  Great Malvern                           9     Delayed
## 09:20  London Paddington                       10    On time
## 09:20  Redhill                                 5     On time
## 09:23  Didcot Parkway                          15    On time
## 09:24  London Waterloo                         4     On time
## 09:27  Ealing Broadway                         14    On time
## 09:29  Newquay                                 7     On time
## 09:32  Basingstoke                             2     On time
## 09:42  London Paddington                       10    On time
## 09:43  Cardiff Central                         9     Delayed
## 09:47  London Paddington                       10    09:50
## 09:54  London Waterloo                         4     On time
## 09:55  Didcot Parkway                          12    On time
## 09:57  Ealing Broadway                         14    On time
## 09:57  London Paddington                       10A   On time
## 09:58  Bristol Temple Meads                    9     On time
## 10:03  Castle Cary                             9     On time
## 10:08  London Paddington                       10    On time
## 10:12  Newbury                                 1     On time
## 10:13  Swansea                                 9     On time
## 10:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 10:19  Hereford                                9B    On time
## 10:20  Redhill                                 15    On time
## 10:23  Didcot Parkway                          12    On time
## 10:24  London Waterloo                         4     On time
## 10:27  Ealing Broadway                         14    On time
## 10:29  Penzance                                7     On time
## 10:32  Basingstoke                             2     On time
## 10:42  London Paddington                       10    On time
## 10:43  Cardiff Central                         9     On time
## 10:48  London Paddington                       10    On time
## 10:53  Bournemouth                             7     On time
## 10:53  Didcot Parkway                          13    On time
## 10:54  London Waterloo                         4     On time
## 10:57  Ealing Broadway                         14    On time
## 10:57  London Paddington                       10A   On time
## 10:58  Bristol Temple Meads                    8     On time
## 11:04  London Paddington                       11    On time
## 09:30  Heathrow Central Bus Stn                BUS   On time
## 10:05  Heathrow Central Bus Stn                BUS   On time
## 10:40  Heathrow Central Bus Stn                BUS   On time
```
