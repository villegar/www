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

## Example (Last rendered on 2023-02-20 04:03)

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
## Reading (RDG) Station Board on 2023-02-20 04:03:33
## Time   From                                    Plat  Expected
## 04:05  Penzance                                14    On time
## 04:21  London Paddington                       13    On time
## 04:38  Didcot Parkway                          13A   On time
## 05:35  Didcot Parkway                          15    On time
## 05:36  Theale                                  7     On time
## 05:38  London Paddington                       9     On time
## 05:46  Oxford                                  11    On time
## 05:47  London Paddington                       9     On time
## 05:58  Bristol Temple Meads                    11    On time
## 05:58  London Paddington                       9     On time
## 05:13  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-20 04:03:38
## Time   To                                      Plat  Expected
## 04:32  Gatwick Airport                         15    On time
##        via Guildford                           
## 04:35  London Paddington                       13    On time
## 04:58  Redhill                                 15    On time
## 05:08  London Paddington                       15    On time
## 05:12  Theale                                  8     On time
## 05:19  Basingstoke                             12B   On time
## 05:31  Gatwick Airport                         15    On time
##        via Guildford                           
## 05:36  Ealing Broadway                         15    On time
## 05:39  London Waterloo                         5     On time
## 05:39  Oxford                                  9     On time
## 05:40  Basingstoke                             13    On time
## 05:48  London Paddington                       11    On time
## 05:49  Swansea                                 9     On time
## 05:50  Didcot Parkway                          13    On time
## 05:50  Theale                                  7     On time
## 05:55  Redhill                                 15A   On time
## 06:00  Abbey Wood                              14    On time
## 06:00  London Paddington                       11    On time
## 06:00  Worcester Shrub Hill                    9     On time
##        via Gloucester                          
## 05:00  Heathrow Airport T3 (Bus)               BUS   On time
## 05:30  Heathrow Airport T3 (Bus)               BUS   On time
## 06:00  Heathrow Airport T3 (Bus)               BUS   On time
```
