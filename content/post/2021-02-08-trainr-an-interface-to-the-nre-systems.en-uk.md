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

## Example (Last rendered on 2023-01-21 22:03)

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
## Reading (RDG) Station Board on 2023-01-21 22:03:34
## Time   From                                    Plat  Expected
## 21:56  London Paddington                       9     22:03
## 22:03  Abbey Wood                              14    22:05
## 22:09  Taunton                                 10    On time
## 22:10  London Paddington                       15B   On time
## 22:17  London Paddington                       8B    On time
## 22:19  Basingstoke                             2     On time
## 22:22  Newbury                                 11    On time
## 22:25  London Paddington                       9     On time
## 22:27  Didcot Parkway                          15    On time
## 22:29  Oxford                                  10    On time
## 22:33  Abbey Wood                              14    22:39
## 22:36  Gloucester                              9     On time
## 22:39  Manchester Piccadilly                   7     On time
## 22:40  London Paddington                       13    On time
## 22:50  Basingstoke                             12    On time
## 22:51  London Paddington                       10    On time
## 22:54  London Paddington                       -     Cancelled
## 23:03  Abbey Wood                              14    On time
## 23:04  Hereford                                15    On time
## 23:10  London Paddington                       13    On time
## 23:11  Penzance                                15    On time
## 23:14  Newbury                                 12B   On time
## 23:24  Basingstoke                             12A   On time
## 23:26  Didcot Parkway                          14    On time
## 23:28  London Paddington                       13    On time
## 23:34  Abbey Wood                              14    On time
## 23:46  London Paddington                       12    On time
## 23:54  Taunton                                 15    On time
## 23:57  Basingstoke                             14B   On time
## 22:06  Bracknell                               BUS   On time
## 22:08  Guildford                               BUS   On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:22  Bracknell                               BUS   On time
## 22:35  Bracknell                               BUS   On time
## 22:48  Guildford                               BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
## 22:52  Bracknell                               BUS   On time
## 23:05  Bracknell                               BUS   On time
## 23:18  Heathrow Central Bus Stn                BUS   On time
## 23:22  Bracknell                               BUS   On time
## 23:35  Bracknell                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-01-21 22:03:37
## Time   To                                      Plat  Expected
## 21:57  Bristol Temple Meads                    9     22:05
## 22:05  Basingstoke                             2     On time
## 22:10  Newbury                                 1     On time
## 22:15  London Paddington                       10    On time
## 22:16  Ealing Broadway                         13    On time
## 22:19  Worcester Shrub Hill                    8B    On time
## 22:22  Abbey Wood                              14    On time
## 22:27  Bristol Parkway                         9     On time
## 22:30  Didcot Parkway                          15B   On time
## 22:34  London Paddington                       10    On time
## 22:35  Basingstoke                             2     On time
## 22:39  London Paddington                       9     On time
## 22:52  Abbey Wood                              14    On time
## 22:52  Southampton Central                     7     On time
## 22:56  Bristol Temple Meads                    -     Cancelled
## 23:01  Didcot Parkway                          13    On time
## 23:05  Basingstoke                             12    On time
## 23:06  London Paddington                       15    On time
## 23:10  Newbury                                 12B   On time
## 23:13  London Paddington                       15    On time
## 23:17  Ealing Broadway                         15    On time
## 23:22  Ealing Broadway                         14    On time
## 23:48  Didcot Parkway                          12    On time
## 23:56  London Paddington                       15    On time
## 22:12  Bracknell                               BUS   On time
## 22:25  Bracknell                               BUS   On time
## 22:32  Guildford                               BUS   On time
## 22:42  Bracknell                               BUS   On time
## 22:55  Bracknell                               BUS   On time
## 22:55  Guildford                               BUS   On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
## 23:12  Bracknell                               BUS   On time
## 23:40  Gatwick Airport                         BUS   On time
##        via Guildford                           
## 23:52  Staines                                 BUS   On time
```
