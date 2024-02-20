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

## Example (Last rendered on 2024-02-20 23:15)

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
## Reading (RDG) Station Board on 2024-02-20 23:16:00.243855
## Time   From                                    Plat  Expected
## 23:11  Penzance                                15    On time
## 23:13  Newbury                                 3     23:15
## 23:17  Didcot Parkway                          13    On time
## 23:18  London Paddington                       12B   23:13
## 23:21  Gatwick Airport                         15A   On time
## 23:25  Basingstoke                             15    On time
## 23:25  London Paddington                       14    On time
## 23:28  London Paddington                       13B   On time
## 23:34  Oxford                                  13A   On time
## 23:40  Abbey Wood                              14    On time
## 23:41  London Waterloo                         5     On time
## 23:47  Didcot Parkway                          15A   On time
## 23:49  Basingstoke                             13    On time
## 23:50  Birmingham New Street                   7     On time
## 23:52  Bristol Temple Meads                    15    On time
## 00:02  London Paddington                       13    00:05
## 00:08  Newbury                                 13    On time
## 00:17  Gatwick Airport                         13    On time
## 00:23  London Paddington                       12    On time
## 00:31  Basingstoke                             13B   On time
## 00:41  Henley-on-Thames                        14    On time
## 00:41  London Waterloo                         6     On time
## 00:43  Gatwick Airport                         4     On time
## 00:47  London Paddington                       13    On time
## 01:04  London Waterloo                         5     On time
## 01:09  Oxford                                  14    On time
## 23:15  Heathrow Airport T3 (Bus)               BUS   On time
## 00:15  Heathrow Airport T3 (Bus)               BUS   On time
## 01:03  Bedwyn                                  BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-02-20 23:16:03.380874
## Time   To                                      Plat  Expected
## 23:14  London Paddington                       15    On time
## 23:17  Ealing Broadway                         14    On time
## 23:27  Swansea                                 14    On time
## 23:30  Moreton-in-Marsh                        13B   On time
## 23:33  Gatwick Airport                         4     On time
##        via Guildford                           
## 23:34  Basingstoke                             2     On time
## 23:34  Didcot Parkway                          12B   On time
## 23:36  London Paddington                       13A   On time
## 23:48  London Paddington                       15A   On time
## 23:52  Ascot                                   5     On time
## 23:55  London Paddington                       15    On time
## 00:04  Bristol Temple Meads                    13    00:06
## 00:07  Oxford                                  12B   On time
## 00:17  Newbury                                 2     On time
## 00:18  London Paddington                       15A   On time
## 00:26  Didcot Parkway                          12    On time
## 01:12  London Paddington                       14    On time
## 01:15  London Paddington                       13A   On time
## 01:15  Oxford                                  12B   On time
```
