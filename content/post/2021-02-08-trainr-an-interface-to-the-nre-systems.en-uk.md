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

## Example (Last rendered on 2022-01-09 22:03)

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
## Reading (RDG) Station Board on 2022-01-09 22:03:19
## Time   From                                    Plat  Expected
## 21:37  London Paddington                       7B    22:04
## 21:40  London Paddington                       9B    22:07
## 22:05  Plymouth                                11    22:23
## 22:07  London Paddington                       7     22:27
## 22:13  Didcot Parkway                          13    On time
## 22:13  London Paddington                       9     22:25
## 22:14  London Paddington                       12    22:18
## 22:17  London Paddington                       14    On time
## 22:25  Newbury                                 1     On time
## 22:28  Swansea                                 11    22:52
## 22:34  Basingstoke                             12    On time
## 22:34  London Paddington                       14    22:38
## 22:36  Bristol Temple Meads                    11    On time
## 22:39  Manchester Piccadilly                   8     On time
## 22:51  Penzance                                13    On time
## 22:54  Great Malvern                           15    On time
## 23:08  Didcot Parkway                          15    On time
## 23:14  Bedwyn                                  15    23:20
## 23:14  London Paddington                       14    On time
## 23:18  Carmarthen                              12    23:29
## 23:30  London Paddington                       12    On time
## 23:32  London Paddington                       14    On time
## 23:46  Newbury                                 13    On time
## 23:59  Plymouth                                14    00:20
## 22:02  Guildford                               BUS   On time
## 22:03  Bracknell                               BUS   On time
## 22:03  Heathrow Central Bus Stn                BUS   On time
## 22:05  Swindon                                 BUS   On time
## 22:19  Bracknell                               BUS   On time
## 22:33  Bracknell                               BUS   On time
## 22:35  Swindon                                 BUS   On time
## 22:45  Guildford                               BUS   On time
## 22:49  Bracknell                               BUS   On time
## 23:03  Bracknell                               BUS   On time
## 23:03  Heathrow Central Bus Stn                BUS   On time
## 23:08  Guildford                               BUS   On time
## 23:13  Swindon                                 BUS   On time
## 23:19  Bracknell                               BUS   On time
## 23:33  Bracknell                               BUS   On time
## 23:49  Bracknell                               BUS   On time
## 23:52  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-09 22:03:21
## Time   To                                      Plat  Expected
## 21:42  Bristol Temple Meads                    7B    22:05
## 21:48  Oxford                                  9B    22:08
## 22:12  Swansea                                 7     22:28
## 22:14  Worcester Shrub Hill                    9     22:26
## 22:15  Didcot Parkway                          12    22:19
## 22:16  London Paddington                       11    22:35
## 22:25  Ealing Broadway                         14    On time
## 22:30  Bristol Temple Meads                    7     On time
## 22:30  London Paddington                       11    22:53
## 22:44  Newbury                                 1     On time
## 22:45  London Paddington                       11    On time
## 22:53  London Paddington                       13    On time
## 22:54  London Paddington                       15    On time
## 22:59  Ealing Broadway                         14    On time
## 23:10  Ealing Broadway                         15    On time
## 23:20  Didcot Parkway                          13    On time
## 23:20  London Paddington                       12    23:30
## 23:36  Bristol Temple Meads                    12    On time
## 00:01  London Paddington                       14    00:21
## 22:14  Guildford                               BUS   On time
## 22:16  Bracknell                               BUS   On time
## 22:20  Swindon                                 BUS   On time
## 22:31  Bracknell                               BUS   On time
## 22:37  Chippenham                              BUS   On time
## 22:54  Bracknell                               BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
## 23:03  Gatwick Airport                         BUS   On time
##        via Guildford                           
## 23:40  Chippenham                              BUS   On time
```
