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

## Example (Last rendered on 2022-12-18 22:07)

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
## Reading (RDG) Station Board on 2022-12-18 22:07:10
## Time   From                                    Plat  Expected
## 21:48  Swansea                                 10    22:12
## 21:53  London Paddington                       9     Delayed
## 22:04  Plymouth                                11    22:19
## 22:07  London Paddington                       9     22:20
## 22:10  London Paddington                       12    On time
## 22:10  Weston-super-Mare                       10    22:16
## 22:12  London Paddington                       9     On time
## 22:13  Didcot Parkway                          13    On time
## 22:24  Newbury                                 13B   Delayed
## 22:32  Basingstoke                             1     On time
## 22:33  Abbey Wood                              14    On time
## 22:37  Henley-on-Thames                        12    On time
## 22:38  London Paddington                       9     On time
## 22:39  Manchester Piccadilly                   8     On time
## 22:45  Gatwick Airport                         -     Cancelled
## 22:49  Swansea                                 10A   On time
## 22:50  Penzance                                13    22:54
## 22:52  Great Malvern                           15A   On time
## 23:04  Abbey Wood                              14    On time
## 23:08  Didcot Parkway                          15    On time
## 23:12  London Paddington                       12    On time
## 23:16  Bedwyn                                  15    On time
## 23:33  London Paddington                       13    On time
## 23:34  London Paddington                       12    On time
## 23:39  Plymouth                                14    23:46
## 23:45  Gatwick Airport                         -     Cancelled
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
## 23:18  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-18 22:07:13
## Time   To                                      Plat  Expected
## 21:50  London Paddington                       10    22:15
## 21:55  Bristol Temple Meads                    9     Delayed
## 22:05  London Paddington                       11    22:20
## 22:09  Swansea                                 9     22:24
## 22:11  London Paddington                       10    22:17
## 22:12  Didcot Parkway                          12    On time
## 22:13  Worcester Shrub Hill                    9     On time
## 22:28  Ealing Broadway                         14    On time
## 22:39  Bristol Temple Meads                    9     On time
## 22:43  Newbury                                 1     On time
## 22:50  London Paddington                       10A   On time
## 22:53  London Paddington                       13    22:55
## 22:54  London Paddington                       15A   On time
## 22:58  Ealing Broadway                         14    On time
## 23:03  Gatwick Airport                         5     On time
##        via Guildford                           
## 23:10  Ealing Broadway                         15    On time
## 23:15  Bristol Parkway                         12    On time
## 23:16  Ealing Broadway                         14    On time
## 23:20  Didcot Parkway                          13    On time
## 23:37  Bristol Temple Meads                    12    On time
## 23:41  London Paddington                       14    23:47
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
```
