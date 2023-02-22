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

## Example (Last rendered on 2023-02-22 06:03)

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
## Reading (RDG) Station Board on 2023-02-22 06:03:24
## Time   From                                    Plat  Expected
## 06:00  Maidenhead                              -     Cancelled
## 06:05  Southampton Central                     8     On time
## 06:08  London Paddington                       9     On time
## 06:13  Didcot Parkway                          15    On time
## 06:14  Staines                                 5     On time
## 06:16  London Paddington                       13    On time
## 06:16  London Paddington                       9B    On time
## 06:25  Cheltenham Spa                          10A   On time
## 06:31  Bristol Temple Meads                    10    On time
## 06:41  London Paddington                       14    On time
## 06:45  London Paddington                       12    On time
## 06:48  London Waterloo                         6     On time
## 06:48  Neath                                   10    On time
## 06:51  Gatwick Airport                         5     On time
## 06:53  Worcester Shrub Hill                    10    On time
## 06:59  Bristol Temple Meads                    11    On time
## 07:00  London Paddington                       14    On time
## 07:09  Hereford                                10    On time
## 07:10  Abbey Wood                              12    On time
## 07:11  London Waterloo                         4     On time
## 07:18  Swansea                                 10    On time
## 07:27  Abbey Wood                              13    On time
## 07:28  Cheltenham Spa                          10    On time
## 07:46  London Waterloo                         -     On time
## 07:49  Swansea                                 11    On time
## 07:54  Hereford                                11    On time
## 06:13  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-22 06:03:29
## Time   To                                      Plat  Expected
## 05:55  Redhill                                 15A   06:03
## 06:00  Abbey Wood                              -     Cancelled
## 06:10  Penzance                                9     On time
##        via Bristol                             
## 06:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 06:18  Great Malvern                           9B    On time
## 06:20  London Paddington                       15    On time
## 06:28  London Paddington                       10A   On time
## 06:34  London Paddington                       10    On time
## 06:50  London Paddington                       10    On time
## 06:55  Didcot Parkway                          12    On time
## 06:56  London Paddington                       10    On time
## 07:02  London Paddington                       11    On time
## 07:12  London Paddington                       10    On time
## 07:20  London Paddington                       10    On time
## 07:31  London Paddington                       10    On time
## 07:51  London Paddington                       11    On time
## 07:56  London Paddington                       11    On time
```
