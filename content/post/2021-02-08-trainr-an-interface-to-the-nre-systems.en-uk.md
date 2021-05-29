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

## Example (Last rendered on 2021-05-29 20:37)

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
## Reading (RDG) Station Board on 2021-05-29 20:37:15
## Time   From                                    Plat  Expected
## 21:33  Cheltenham Spa                          10    On time
## 21:39  Manchester Piccadilly                   7B    On time
## 21:40  Newbury                                 1     On time
## 21:41  London Waterloo                         5     On time
## 21:43  London Paddington                       14    On time
## 21:43  Penzance                                11    21:58
## 21:44  London Paddington                       12    On time
## 21:50  Basingstoke                             2     On time
## 21:50  Swansea                                 10    On time
## 21:52  Redhill                                 15B   On time
## 21:54  Moreton-in-Marsh                        11    On time
## 21:57  Gatwick Airport                         15B   On time
## 22:09  Taunton                                 10    On time
## 22:11  London Waterloo                         -     Cancelled
## 22:13  London Paddington                       14    On time
## 22:17  London Paddington                       8     On time
## 22:23  Newbury                                 12A   On time
## 22:25  Gatwick Airport                         15B   On time
## 22:25  London Paddington                       9     On time
## 22:32  Oxford                                  14    On time
## 22:36  Cheltenham Spa                          10    On time
## 22:41  London Waterloo                         6     On time
## 22:41  Manchester Piccadilly                   8B    On time
## 22:43  London Paddington                       14    On time
## 22:44  London Paddington                       13    On time
## 22:50  Basingstoke                             12B   On time
## 22:52  London Paddington                       10    On time
## 22:55  London Paddington                       9     On time
## 23:01  Didcot Parkway                          15    On time
## 23:02  Redhill                                 5     On time
## 23:04  Moreton-in-Marsh                        14    On time
## 23:11  London Waterloo                         4     On time
## 23:11  Penzance                                13    On time
## 23:13  London Paddington                       14    On time
## 23:14  Newbury                                 12B   On time
## 23:29  London Paddington                       13    On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-29 20:37:17
## Time   To                                      Plat  Expected
## 21:35  Basingstoke                             2     On time
## 21:35  London Paddington                       10    On time
## 21:42  London Waterloo                         6     On time
## 21:45  London Paddington                       11    21:59
## 21:51  London Paddington                       10    On time
## 21:52  Bournemouth                             7B    On time
## 21:52  Ealing Broadway                         14    On time
## 21:56  London Paddington                       11    On time
## 21:57  Didcot Parkway                          12    On time
## 22:10  Newbury                                 1     On time
## 22:12  London Waterloo                         5     On time
## 22:15  Ealing Broadway                         15    On time
## 22:15  London Paddington                       10    On time
## 22:19  Moreton-in-Marsh                        8     On time
## 22:22  Ealing Broadway                         14    On time
## 22:27  Bristol Parkway                         9     On time
## 22:34  London Paddington                       14    On time
## 22:35  Basingstoke                             2     On time
## 22:39  London Paddington                       10    On time
## 22:42  London Waterloo                         -     Cancelled
## 22:52  Ealing Broadway                         14    On time
## 22:52  Southampton Central                     8B    On time
## 22:57  Bristol Parkway                         9     On time
## 23:05  Basingstoke                             12B   On time
## 23:05  Didcot Parkway                          13    On time
## 23:06  London Paddington                       14    On time
## 23:10  Newbury                                 12A   On time
## 23:13  London Paddington                       13    On time
## 23:15  London Waterloo                         6     On time
## 23:34  Redhill                                 15A   On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
