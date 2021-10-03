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

## Example (Last rendered on 2021-10-03 22:03)

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
## Reading (RDG) Station Board on 2021-10-03 22:03:31
## Time   From                                    Plat  Expected
## 22:45  Gatwick Airport                         15B   Delayed
## 22:52  Great Malvern                           11A   23:05
## 23:03  London Paddington                       14    On time
## 23:06  London Paddington                       13    On time
## 23:08  Didcot Parkway                          15    On time
## 23:13  London Paddington                       12    On time
## 23:17  Bedwyn                                  14    On time
## 23:30  Penzance                                15    23:38
## 23:32  London Paddington                       12    On time
## 23:33  London Paddington                       14    On time
## 23:35  Plymouth                                13    On time
## 23:41  Gatwick Airport                         15    On time
## 23:46  Newbury                                 13    On time
## 00:12  London Paddington                       13    On time
## 00:17  London Paddington                       12    On time
## 00:23  Didcot Parkway                          15    On time
## 00:49  Gatwick Airport                         15    On time
## 00:50  Didcot Parkway                          14    On time
## 00:52  London Paddington                       13    On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
## 23:15  Virginia Water                          BUS   On time
## 23:45  Virginia Water                          BUS   On time
## 00:03  Heathrow Central Bus Stn                BUS   On time
## 00:15  Virginia Water                          BUS   On time
## 00:45  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-10-03 22:03:34
## Time   To                                      Plat  Expected
## 22:54  London Paddington                       11A   23:06
## 23:03  Gatwick Airport                         6     On time
##        via Guildford                           
## 23:10  Ealing Broadway                         15    On time
## 23:15  Bristol Parkway                         12    On time
## 23:20  Didcot Parkway                          13    On time
## 23:32  London Paddington                       15    23:39
## 23:35  Swindon                                 12    On time
## 23:37  London Paddington                       13    On time
## 00:19  Bristol Temple Meads                    12    On time
## 00:24  Didcot Parkway                          13    On time
## 00:24  Ealing Broadway                         15    On time
## 00:51  Penzance                                12    On time
## 00:54  London Paddington                       14    On time
```
