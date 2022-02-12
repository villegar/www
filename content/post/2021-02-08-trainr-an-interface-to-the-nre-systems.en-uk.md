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

## Example (Last rendered on 2022-02-12 04:04)

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
## Reading (RDG) Station Board on 2022-02-12 04:04:24
## Time   From                                    Plat  Expected
## 04:21  London Paddington                       14B   On time
## 05:48  London Paddington                       9B    On time
## 06:03  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-12 04:04:25
## Time   To                                      Plat  Expected
## 04:13  London Paddington                       14A   On time
## 04:54  London Paddington                       14    On time
## 05:08  Newbury                                 13B   On time
## 05:32  Bedwyn                                  7B    On time
## 05:43  Basingstoke                             12B   On time
## 05:44  London Paddington                       15    On time
## 05:50  Oxford                                  9B    On time
## 05:52  London Paddington                       14    On time
## 05:55  Didcot Parkway                          13    On time
## 05:00  Heathrow Central Bus Stn                BUS   On time
## 05:04  Ascot                                   BUS   On time
## 05:15  North Camp                              BUS   On time
## 05:18  Ascot                                   BUS   On time
## 05:34  Ascot                                   BUS   On time
## 05:48  Ascot                                   BUS   On time
## 06:00  Heathrow Central Bus Stn                BUS   On time
```
