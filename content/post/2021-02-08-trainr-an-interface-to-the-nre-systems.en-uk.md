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

## Example (Last rendered on 2022-05-03 22:04)

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
## Reading (RDG) Station Board on 2022-05-03 22:04:41
## Time   From                                    Plat  Expected
## 22:32  Cheltenham Spa                          10    23:09
## 23:12  London Waterloo                         5     23:18
## 23:12  Totnes                                  15A   23:23
## 23:13  London Paddington                       13    On time
## 23:15  London Paddington                       14    23:17
## 23:17  London Paddington                       12    On time
## 23:18  Gatwick Airport                         6     On time
## 23:22  Didcot Parkway                          15    On time
## 23:27  Basingstoke                             15B   On time
## 23:27  London Paddington                       12B   On time
## 23:35  Oxford                                  15A   On time
## 23:43  London Paddington                       14    On time
## 23:45  London Waterloo                         5     On time
## 23:46  Didcot Parkway                          15    On time
## 23:49  Basingstoke                             13B   23:54
## 23:51  Birmingham New Street                   14B   On time
## 23:57  London Paddington                       12B   On time
## 00:03  London Paddington                       14    On time
## 00:11  London Waterloo                         6     On time
## 00:17  Gatwick Airport                         15B   On time
## 00:23  London Paddington                       13    On time
## 00:31  Basingstoke                             13B   On time
## 00:40  Henley-on-Thames                        14    On time
## 00:41  Oxford                                  13A   On time
## 00:48  London Paddington                       13    On time
## 23:35  Heathrow Central Bus Stn                BUS   On time
## 00:05  Bedwyn                                  BUS   On time
## 00:35  Heathrow Central Bus Stn                BUS   On time
## 00:46  Newbury                                 BUS   On time
## 01:03  Bedwyn                                  BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-05-03 22:04:44
## Time   To                                      Plat  Expected
## 22:35  London Paddington                       10    23:10
## 23:19  London Paddington                       15A   23:24
## 23:19  Neath                                   12    On time
## 23:23  Ealing Broadway                         15    On time
## 23:28  Oxford                                  12B   On time
## 23:32  Didcot Parkway                          14    On time
## 23:33  Gatwick Airport                         4     On time
##        via Guildford                           
## 23:34  Basingstoke                             12B   On time
## 23:38  London Paddington                       15A   On time
## 23:52  Ascot                                   5     On time
## 00:05  Bristol Temple Meads                    14    On time
## 00:08  Oxford                                  12B   On time
## 00:18  London Paddington                       13    On time
## 00:26  Didcot Parkway                          13    On time
## 00:43  London Paddington                       13A   On time
## 00:49  Penzance                                15    On time
## 23:13  Bedwyn                                  BUS   On time
## 00:17  Newbury                                 BUS   On time
```
