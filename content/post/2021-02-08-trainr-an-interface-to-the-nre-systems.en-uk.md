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

## Example (Last rendered on 2023-04-16 08:04)

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
## Reading (RDG) Station Board on 2023-04-16 08:04:06
## Time   From                                    Plat  Expected
## 09:02  London Waterloo                         4     On time
## 09:08  Didcot Parkway                          14A   On time
## 09:13  London Paddington                       -     Cancelled
## 09:15  London Paddington                       12B   On time
## 09:24  London Paddington                       7     On time
## 09:25  Swindon                                 11    On time
## 09:28  London Paddington                       14    On time
## 09:35  Virginia Water                          4     On time
## 09:38  Bristol Parkway                         11    On time
## 09:41  Gatwick Airport                         13    On time
## 09:56  London Paddington                       7     On time
## 09:58  Didcot Parkway                          15    On time
## 09:58  London Paddington                       12    On time
## 09:59  Didcot Parkway                          10    On time
## 10:03  London Waterloo                         4     On time
## 10:09  Weston-super-Mare                       10    On time
## 10:10  Redhill                                 6     On time
## 10:14  London Paddington                       9     On time
## 10:15  London Paddington                       13    On time
## 10:25  Cardiff Central                         11    On time
## 10:29  London Paddington                       12    On time
## 10:35  Virginia Water                          4     On time
## 10:38  Gatwick Airport                         5     On time
## 10:39  Didcot Parkway                          15    On time
## 10:42  London Paddington                       9     On time
## 10:47  Exeter St Davids                        11    On time
## 10:53  Bristol Parkway                         10    On time
## 10:54  London Paddington                       8     On time
## 10:58  Didcot Parkway                          11    On time
## 10:59  London Paddington                       14    On time
## 11:03  London Waterloo                         4     On time
## 09:04  Heathrow Central Bus Stn                BUS   On time
## 09:17  Newbury                                 BUS   On time
## 09:23  Basingstoke                             BUS   On time
## 09:34  Heathrow Central Bus Stn                BUS   On time
## 09:45  Newbury                                 BUS   On time
## 10:00  Basingstoke                             BUS   On time
## 10:04  Heathrow Central Bus Stn                BUS   On time
## 10:34  Heathrow Central Bus Stn                BUS   On time
## 10:39  Newbury                                 BUS   On time
## 10:53  Bramley (Hampshire)                     BUS   On time
## 11:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-16 08:04:12
## Time   To                                      Plat  Expected
## 08:53  Abbey Wood                              14    09:04
## 09:10  Ealing Broadway                         14A   On time
## 09:14  Didcot Parkway                          15A   On time
## 09:15  Didcot Parkway                          8B    On time
## 09:18  Didcot Parkway                          12B   On time
## 09:21  Gatwick Airport                         13A   On time
##        via Guildford                           
## 09:23  Abbey Wood                              12    On time
## 09:24  Virginia Water                          4     On time
## 09:30  London Paddington                       11    On time
## 09:35  Weston-super-Mare                       7     On time
## 09:41  Redhill                                 13    On time
## 09:45  London Paddington                       11    On time
## 09:53  Abbey Wood                              14    On time
## 09:54  London Waterloo                         4     On time
## 09:56  Penzance                                9     On time
## 09:59  London Paddington                       10    On time
## 10:00  Carmarthen                              7     On time
## 10:14  Ealing Broadway                         15    On time
## 10:14  London Paddington                       10    On time
## 10:16  Didcot Parkway                          9     On time
## 10:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:23  Abbey Wood                              12    On time
## 10:24  Virginia Water                          4     On time
## 10:26  Didcot Parkway                          13    On time
## 10:27  London Paddington                       11    On time
## 10:41  Redhill                                 6     On time
## 10:43  Bristol Parkway                         9     On time
## 10:46  Bournemouth                             15    On time
## 10:48  London Paddington                       11    On time
## 10:53  Abbey Wood                              12    On time
## 10:54  London Waterloo                         4     On time
## 10:55  Weston-super-Mare                       8     On time
## 10:56  London Paddington                       10    On time
## 10:58  London Paddington                       11    On time
## 11:03  Plymouth                                9     On time
## 09:08  Basingstoke                             BUS   On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:43  Bedwyn                                  BUS   On time
## 09:52  Winchester                              BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:38  Basingstoke                             BUS   On time
## 10:40  Newbury                                 BUS   On time
## 10:43  Newbury                                 BUS   On time
## 10:52  Basingstoke                             BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
```
