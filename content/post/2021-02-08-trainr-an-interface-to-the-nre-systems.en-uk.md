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

## Example (Last rendered on 2022-11-19 14:06)

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
## Reading (RDG) Station Board on 2022-11-19 14:06:26
## Time   From                                    Plat  Expected
## 14:09  London Paddington                       9     14:21
## 14:09  Plymouth                                11    On time
## 14:17  London Paddington                       9B    On time
## 14:17  London Waterloo                         6     On time
## 14:23  London Paddington                       7     On time
## 14:33  London Paddington                       14    On time
## 14:33  Redhill                                 5     On time
## 14:40  Bristol Temple Meads                    10    14:47
## 14:40  Manchester Piccadilly                   7     On time
## 14:46  London Waterloo                         6     On time
## 14:50  Swansea                                 11    On time
## 14:52  Basingstoke                             2     On time
## 14:53  Worcester Foregate Street               10    On time
## 14:55  London Paddington                       9     On time
## 14:59  Didcot Parkway                          15    On time
## 15:01  Plymouth                                11    15:08
## 15:03  London Paddington                       14    On time
## 15:05  Bournemouth                             13B   On time
## 15:09  London Paddington                       8     On time
## 15:16  London Waterloo                         6     On time
## 15:17  London Paddington                       9     On time
## 15:27  London Paddington                       7     On time
## 15:33  London Paddington                       14    On time
## 15:33  Redhill                                 5     On time
## 15:38  London Paddington                       9     On time
## 15:40  Bristol Temple Meads                    10    On time
## 15:40  Manchester Piccadilly                   13    On time
## 15:46  London Waterloo                         6     On time
## 15:50  Swansea                                 11    On time
## 15:51  Basingstoke                             2     On time
## 15:53  Hereford                                10    On time
## 15:55  London Paddington                       9     On time
## 16:00  Didcot Parkway                          15    On time
## 16:01  Plymouth                                11    On time
## 16:03  London Paddington                       14    On time
## 14:34  Heathrow Central Bus Stn                BUS   On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-19 14:06:30
## Time   To                                      Plat  Expected
## 14:09  London Waterloo                         6     On time
## 14:11  Swansea                                 9     14:22
## 14:12  London Paddington                       11    On time
## 14:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 14:19  Great Malvern                           9B    On time
## 14:20  Redhill                                 5     On time
## 14:24  London Paddington                       14    On time
## 14:25  Plymouth                                7     On time
## 14:37  Basingstoke                             2     On time
## 14:39  London Waterloo                         6     On time
## 14:42  London Paddington                       10    14:48
## 14:52  London Paddington                       11    On time
## 14:53  Bournemouth                             7     On time
## 14:54  London Paddington                       14    On time
## 14:55  Didcot Parkway                          15    On time
## 14:56  London Paddington                       10    On time
## 14:57  Bristol Temple Meads                    9     On time
## 15:05  London Paddington                       11    15:09
## 15:09  London Waterloo                         6     On time
## 15:11  Swansea                                 8     On time
## 15:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 15:19  Worcester Shrub Hill                    9     On time
## 15:20  Redhill                                 5     On time
## 15:24  London Paddington                       14    On time
## 15:29  Plymouth                                7     On time
## 15:37  Basingstoke                             2     On time
## 15:39  London Waterloo                         6     On time
## 15:40  Bristol Parkway                         9     On time
## 15:43  London Paddington                       10    On time
## 15:51  Didcot Parkway                          15    On time
## 15:52  London Paddington                       11    On time
## 15:54  London Paddington                       14    On time
## 15:57  Bristol Temple Meads                    9     On time
## 15:58  London Paddington                       10    On time
## 16:05  London Paddington                       11    On time
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:00  Heathrow Airport T3 (Bus)               BUS   On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
```
