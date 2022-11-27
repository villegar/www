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

## Example (Last rendered on 2022-11-27 22:03)

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
## Reading (RDG) Station Board on 2022-11-27 22:03:57
## Time   From                                    Plat  Expected
## 21:49  Swansea                                 15    22:02
## 21:55  Great Malvern                           13    22:06
## 22:03  Abbey Wood                              14    On time
## 22:05  Plymouth                                11    22:25
## 22:06  London Paddington                       7     22:13
## 22:10  London Paddington                       12B   On time
## 22:12  London Paddington                       7     On time
## 22:13  Didcot Parkway                          13    On time
## 22:17  Weston-super-Mare                       15    On time
## 22:24  Newbury                                 1     On time
## 22:25  London Waterloo                         4     On time
## 22:27  London Paddington                       7     On time
## 22:33  Abbey Wood                              14    On time
## 22:33  Basingstoke                             13    On time
## 22:39  Manchester Piccadilly                   7     23:01
## 22:50  Plymouth                                13    22:52
## 22:52  Great Malvern                           15A   On time
## 22:58  London Waterloo                         6     On time
## 23:04  Abbey Wood                              14    On time
## 23:08  Didcot Parkway                          15A   On time
## 23:10  London Paddington                       7     On time
## 23:16  Bedwyn                                  15    On time
## 23:18  Carmarthen                              12A   On time
## 23:25  London Waterloo                         6     On time
## 23:33  London Paddington                       13    On time
## 23:35  London Paddington                       7     On time
## 23:35  Plymouth                                15    23:38
## 23:46  Newbury                                 1     On time
## 23:58  London Waterloo                         6     On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:38  Guildford                               BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
## 23:08  Guildford                               BUS   On time
## 23:18  Heathrow Central Bus Stn                BUS   On time
## 23:50  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-27 22:04:02
## Time   To                                      Plat  Expected
## 21:50  London Paddington                       15    22:04
## 21:57  London Paddington                       13    22:07
## 22:09  Swansea                                 7     22:14
## 22:12  London Paddington                       11    22:26
## 22:14  Worcester Shrub Hill                    7     On time
## 22:18  Didcot Parkway                          12B   On time
## 22:20  London Paddington                       15    On time
## 22:21  London Waterloo                         6     On time
## 22:28  Ealing Broadway                         14    On time
## 22:30  Bristol Temple Meads                    7     On time
## 22:43  Newbury                                 1     On time
## 22:53  London Paddington                       13    22:53
## 22:54  London Paddington                       15A   On time
## 22:56  London Waterloo                         4     On time
## 22:58  Ealing Broadway                         14    On time
## 23:10  Ealing Broadway                         15A   On time
## 23:15  Bristol Parkway                         7     On time
## 23:20  Didcot Parkway                          13A   On time
## 23:20  London Paddington                       12A   On time
## 23:37  Bristol Temple Meads                    7     On time
## 23:37  London Paddington                       15    23:39
## 23:40  Ealing Broadway                         14    Delayed
## 22:25  Guildford                               BUS   On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
## 23:03  Gatwick Airport                         BUS   On time
##        via Guildford                           
## 23:48  Chippenham                              BUS   On time
```
