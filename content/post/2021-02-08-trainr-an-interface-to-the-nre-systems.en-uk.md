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

## Example (Last rendered on 2023-02-12 22:03)

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
## Reading (RDG) Station Board on 2023-02-12 22:03:24
## Time   From                                    Plat  Expected
## 21:56  Abbey Wood                              14    22:05
## 22:04  Plymouth                                11    On time
## 22:06  London Waterloo                         4     On time
## 22:09  London Paddington                       9     On time
## 22:10  Weston-super-Mare                       11    22:14
## 22:11  London Paddington                       12    On time
## 22:13  Didcot Parkway                          13    22:17
## 22:15  London Paddington                       9     22:23
## 22:24  Henley-on-Thames                        12A   On time
## 22:24  Newbury                                 1     On time
## 22:28  Abbey Wood                              14    On time
## 22:32  Basingstoke                             12A   On time
## 22:36  London Waterloo                         4     On time
## 22:39  London Paddington                       9     On time
## 22:39  Manchester Piccadilly                   8     22:55
## 22:45  Gatwick Airport                         13B   On time
## 22:49  Swansea                                 9A    22:59
## 22:50  Penzance                                10    22:53
## 22:52  Great Malvern                           -     Cancelled
## 22:59  Abbey Wood                              10    On time
## 23:02  London Waterloo                         6     On time
## 23:09  Didcot Parkway                          7     On time
## 23:11  London Paddington                       9     On time
## 23:16  Bedwyn                                  3     On time
## 23:27  London Paddington                       9     On time
## 23:29  London Paddington                       7     On time
## 23:35  London Waterloo                         6     On time
## 23:39  Plymouth                                10A   On time
## 23:45  Gatwick Airport                         8     On time
## 23:46  Newbury                                 1     On time
## 00:02  London Waterloo                         5     On time
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
## Reading (RDG) Station Board on 2023-02-12 22:03:28
## Time   To                                      Plat  Expected
## 22:05  London Paddington                       11    On time
## 22:10  Swansea                                 9     On time
## 22:13  London Paddington                       11    22:15
## 22:16  Didcot Parkway                          12    On time
## 22:16  Worcester Shrub Hill                    9     22:24
## 22:22  Ealing Broadway                         15    On time
## 22:24  Staines                                 4     On time
## 22:43  Newbury                                 1     On time
## 22:44  Bristol Temple Meads                    9     On time
## 22:52  London Paddington                       9A    23:00
## 22:54  London Waterloo                         4     On time
## 22:55  Ealing Broadway                         14    On time
## 22:55  London Paddington                       10    On time
## 22:57  London Paddington                       -     Cancelled
## 23:03  Redhill                                 5     On time
## 23:13  Ealing Broadway                         7     On time
## 23:15  Bristol Parkway                         9     On time
## 23:18  Ealing Broadway                         10    On time
## 23:20  Didcot Parkway                          8     On time
## 23:37  Bristol Temple Meads                    7     On time
## 23:45  London Paddington                       10A   On time
## 23:52  Staines                                 6     On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
```
