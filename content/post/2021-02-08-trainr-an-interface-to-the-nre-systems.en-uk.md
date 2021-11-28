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

## Example (Last rendered on 2021-11-28 22:03)

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
## Reading (RDG) Station Board on 2021-11-28 22:03:14
## Time   From                                    Plat  Expected
## 21:54  London Paddington                       9B    22:11
## 21:59  Great Malvern                           11A   21:56
## 21:59  London Paddington                       8     22:13
## 22:01  London Paddington                       9     22:14
## 22:05  Plymouth                                7     22:10
## 22:09  Weston-super-Mare                       10    22:13
## 22:13  London Paddington                       14    22:23
## 22:17  Slough                                  12    On time
## 22:24  Newbury                                 1     On time
## 22:25  Didcot Parkway                          13    On time
## 22:28  London Paddington                       9     On time
## 22:39  Manchester Piccadilly                   -     Cancelled
## 22:40  London Paddington                       14    22:42
## 22:43  Swansea                                 10    22:49
## 22:45  Gatwick Airport                         15B   On time
## 22:47  Great Malvern                           11    On time
## 22:51  Penzance                                10    23:04
## 23:08  Didcot Parkway                          15    On time
## 23:10  London Paddington                       14    On time
## 23:11  London Paddington                       7     On time
## 23:12  London Paddington                       13    On time
## 23:17  Bedwyn                                  14    On time
## 23:34  London Paddington                       7     On time
## 23:34  Plymouth                                10    23:45
## 23:41  London Paddington                       14    On time
## 23:43  Gatwick Airport                         -     Cancelled
## 23:46  Newbury                                 1     On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 22:18  Basingstoke                             BUS   On time
## 22:26  Staines                                 BUS   On time
## 22:56  Staines                                 BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
## 23:18  Basingstoke                             BUS   On time
## 23:25  Banbury                                 BUS   On time
## 23:26  Staines                                 BUS   On time
## 23:56  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-11-28 22:03:16
## Time   To                                      Plat  Expected
## 21:56  Oxford                                  9B    22:12
## 22:00  Bristol Temple Meads                    8     22:14
## 22:06  Ealing Broadway                         14    On time
## 22:07  London Paddington                       11A   On time
## 22:09  Swansea                                 9     22:15
## 22:12  London Paddington                       7     On time
## 22:17  Didcot Parkway                          12    On time
## 22:19  London Paddington                       10    On time
## 22:27  Ealing Broadway                         13    On time
## 22:30  Worcester Shrub Hill                    9     On time
## 22:36  Ealing Broadway                         14    On time
## 22:44  Newbury                                 1     On time
## 22:45  London Paddington                       10    22:50
## 22:49  London Paddington                       11    On time
## 23:00  London Paddington                       10    23:05
## 23:03  Gatwick Airport                         5     On time
##        via Guildford                           
## 23:06  Ealing Broadway                         14    On time
## 23:10  Ealing Broadway                         15    On time
## 23:15  Bristol Parkway                         7     On time
## 23:21  Didcot Parkway                          13    On time
## 23:37  Bristol Temple Meads                    7     On time
## 23:45  London Paddington                       10    23:45
## 22:27  Staines                                 BUS   On time
## 22:54  Staines                                 BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
