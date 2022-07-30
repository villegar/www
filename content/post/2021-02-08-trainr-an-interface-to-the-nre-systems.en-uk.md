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

## Example (Last rendered on 2022-07-30 20:04)

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
## Reading (RDG) Station Board on 2022-07-30 20:04:18
## Time   From                                    Plat  Expected
## 20:39  Manchester Piccadilly                   12    21:12
## 21:03  London Paddington                       14    21:06
## 21:05  Bournemouth                             13B   21:07
## 21:33  London Paddington                       14    On time
## 21:39  Manchester Piccadilly                   7B    On time
## 22:04  London Paddington                       14    On time
## 22:33  London Paddington                       14    On time
## 22:41  Manchester Piccadilly                   7     On time
## 23:03  London Paddington                       10    On time
## 21:03  Virginia Water                          BUS   On time
## 21:24  Virginia Water                          BUS   On time
## 21:33  Virginia Water                          -     Cancelled
## 21:54  Virginia Water                          BUS   On time
## 22:03  Virginia Water                          -     Cancelled
## 22:24  Virginia Water                          BUS   On time
## 22:33  Virginia Water                          -     Cancelled
## 22:54  Virginia Water                          BUS   On time
## 23:03  Virginia Water                          -     Cancelled
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-07-30 20:04:21
## Time   To                                      Plat  Expected
## 20:52  Bournemouth                             12    21:13
## 21:15  Birmingham New Street                   13B   On time
##        via Coventry                            
## 21:24  London Paddington                       14    On time
## 21:52  Bournemouth                             7B    On time
## 21:52  London Paddington                       14    On time
## 22:22  London Paddington                       14    On time
## 22:52  London Paddington                       14    On time
## 22:52  Southampton Central                     7     On time
## 21:11  Virginia Water                          BUS   On time
## 21:20  Virginia Water                          BUS   On time
## 21:41  Virginia Water                          -     Cancelled
## 21:50  Virginia Water                          BUS   On time
## 22:11  Virginia Water                          -     Cancelled
## 22:20  Virginia Water                          BUS   On time
## 22:41  Virginia Water                          -     Cancelled
## 22:50  Virginia Water                          BUS   On time
```
