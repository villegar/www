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

## Example (Last rendered on 2022-02-20 22:04)

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
## Reading (RDG) Station Board on 2022-02-20 22:04:29
## Time   From                                    Plat  Expected
## 20:58  Exeter St Davids                        11    22:14
## 21:11  Bristol Temple Meads                    10    22:10
## 21:29  London Paddington                       7     22:16
## 21:39  Manchester Piccadilly                   8     22:14
## 21:53  London Paddington                       9     22:09
## 21:57  Great Malvern                           -     Cancelled
## 22:05  Exeter St Davids                        -     Cancelled
## 22:06  London Paddington                       -     Cancelled
## 22:09  Bristol Temple Meads                    10    22:53
## 22:10  Guildford                               5     On time
## 22:12  London Paddington                       -     Cancelled
## 22:13  Didcot Parkway                          13    22:17
## 22:14  London Paddington                       14    On time
## 22:19  London Waterloo                         -     Cancelled
## 22:24  London Paddington                       -     Cancelled
## 22:24  Newbury                                 1     Delayed
## 22:33  London Paddington                       14    On time
## 22:34  Basingstoke                             12    22:43
## 22:39  Manchester Piccadilly                   8     On time
## 22:49  Carmarthen                              -     Cancelled
## 22:49  London Waterloo                         -     Cancelled
## 22:50  Exeter St Davids                        11    23:08
## 22:54  Great Malvern                           -     Cancelled
## 23:08  Didcot Parkway                          8     On time
## 23:10  Guildford                               5     On time
## 23:10  London Paddington                       10    On time
## 23:12  London Paddington                       -     Cancelled
## 23:14  Bedwyn                                  3     23:16
## 23:17  London Waterloo                         -     Cancelled
## 23:32  London Paddington                       9     On time
## 23:35  Bristol Temple Meads                    11    23:57
## 23:41  London Paddington                       10    On time
## 23:46  Newbury                                 1     On time
## 23:49  London Waterloo                         -     Cancelled
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
## 00:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-20 22:04:33
## Time   To                                      Plat  Expected
## 20:59  London Paddington                       11    22:17
## 21:14  London Paddington                       10    22:11
## 21:31  Exeter St Davids                        7     22:17
## 21:52  Southampton Central                     8     22:15
## 21:55  Bristol Temple Meads                    9     22:10
## 22:00  London Paddington                       -     Cancelled
## 22:10  Swansea                                 -     Cancelled
## 22:12  London Paddington                       10    22:54
## 22:13  Worcester Shrub Hill                    -     Cancelled
## 22:15  Guildford                               15A   On time
## 22:15  London Paddington                       -     Cancelled
## 22:16  Didcot Parkway                          12    On time
## 22:25  Bristol Temple Meads                    -     Cancelled
## 22:25  Ealing Broadway                         14    On time
## 22:25  London Waterloo                         -     Cancelled
## 22:44  Newbury                                 1     On time
## 22:52  London Paddington                       -     Cancelled
## 22:55  London Paddington                       -     Cancelled
## 22:56  London Waterloo                         -     Cancelled
## 22:57  Ealing Broadway                         14    On time
## 23:02  London Paddington                       11    23:15
## 23:03  Guildford                               5     On time
## 23:12  Ealing Broadway                         8     On time
## 23:17  Bristol Parkway                         -     Cancelled
## 23:20  Didcot Parkway                          7     On time
## 23:35  Bristol Temple Meads                    9     On time
## 23:40  London Paddington                       11    23:58
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
