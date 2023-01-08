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

## Example (Last rendered on 2023-01-08 22:03)

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
## Reading (RDG) Station Board on 2023-01-08 22:03:33
## Time   From                                    Plat  Expected
## 22:03  Abbey Wood                              14    On time
## 22:04  Plymouth                                11    On time
## 22:07  London Paddington                       7     On time
## 22:10  London Paddington                       12    On time
## 22:12  London Paddington                       9     22:14
## 22:13  Didcot Parkway                          13    On time
## 22:24  Newbury                                 1     On time
## 22:28  Weston-super-Mare                       11A   On time
## 22:33  Abbey Wood                              14    On time
## 22:33  Basingstoke                             13B   On time
## 22:35  Virginia Water                          4     On time
## 22:36  Swansea                                 10    On time
## 22:37  Henley-on-Thames                        13    On time
## 22:38  London Paddington                       7     On time
## 22:39  Manchester Piccadilly                   8     On time
## 22:45  Gatwick Airport                         15B   On time
## 22:50  Penzance                                13    On time
## 22:52  Great Malvern                           15    On time
## 22:58  London Waterloo                         4     On time
## 23:04  Abbey Wood                              14    On time
## 23:08  Didcot Parkway                          15    On time
## 23:14  Bedwyn                                  15    On time
## 23:33  London Paddington                       13    On time
## 23:34  London Paddington                       12    On time
## 23:35  Carmarthen                              15A   On time
## 23:35  Virginia Water                          4     On time
## 23:45  Gatwick Airport                         15    On time
## 23:46  Newbury                                 14    On time
## 23:52  Plymouth                                15    On time
## 23:58  London Waterloo                         4     On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:35  Chippenham                              BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
## 22:55  Swindon                                 BUS   On time
## 23:18  Heathrow Central Bus Stn                BUS   On time
## 23:35  Chippenham                              BUS   On time
## 23:55  Swindon                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-01-08 22:03:37
## Time   To                                      Plat  Expected
## 22:05  London Paddington                       11    On time
## 22:10  Swansea                                 7     On time
## 22:12  Didcot Parkway                          12    On time
## 22:13  Worcester Shrub Hill                    9     22:15
## 22:24  Virginia Water                          4     On time
## 22:28  Ealing Broadway                         14    On time
## 22:30  London Paddington                       11A   On time
## 22:40  Bristol Temple Meads                    7     On time
## 22:42  London Paddington                       10    On time
## 22:43  Newbury                                 1     On time
## 22:51  London Waterloo                         4     On time
## 22:53  London Paddington                       13    On time
## 22:54  London Paddington                       15    On time
## 22:58  Ealing Broadway                         14    On time
## 23:03  Gatwick Airport                         5     On time
##        via Guildford                           
## 23:10  Ealing Broadway                         15    On time
## 23:16  Ealing Broadway                         14    On time
## 23:20  Didcot Parkway                          13    On time
## 23:38  Bristol Temple Meads                    12    On time
## 23:41  London Paddington                       15A   On time
## 23:52  Virginia Water                          4     On time
## 23:54  London Paddington                       15    On time
## 22:47  Chippenham                              BUS   On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
## 23:50  Chippenham                              BUS   On time
```
