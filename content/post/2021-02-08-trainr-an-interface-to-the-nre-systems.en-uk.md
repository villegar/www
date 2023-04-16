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

## Example (Last rendered on 2023-04-16 16:03)

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
## Reading (RDG) Station Board on 2023-04-16 16:03:56
## Time   From                                    Plat  Expected
## 15:28  Penzance                                11    17:39
## 16:53  Bournemouth                             13B   17:16
## 16:54  London Paddington                       8     16:58
## 17:02  London Waterloo                         4     On time
## 17:07  London Paddington                       7     17:09
## 17:09  Weston-super-Mare                       10    17:14
## 17:10  Redhill                                 6     On time
## 17:13  Didcot Parkway                          15A   On time
## 17:13  London Paddington                       12B   On time
## 17:15  London Paddington                       9     On time
## 17:24  London Paddington                       9     On time
## 17:28  Abbey Wood                              14    On time
## 17:28  Penzance                                11    On time
## 17:35  Virginia Water                          4     On time
## 17:38  Gatwick Airport                         5     On time
## 17:39  Bristol Temple Meads                    10    On time
## 17:44  Carmarthen                              11    On time
## 17:57  Didcot Parkway                          10A   On time
## 17:57  London Paddington                       8B    On time
## 17:58  Abbey Wood                              14    On time
## 18:02  London Waterloo                         4     On time
## 18:06  Plymouth                                10    On time
## 18:07  London Paddington                       8     On time
## 18:10  Redhill                                 6     On time
## 18:13  Didcot Parkway                          15A   On time
## 18:13  London Paddington                       12B   On time
## 18:14  Plymouth                                11    On time
## 18:15  London Paddington                       9     On time
## 18:26  London Paddington                       9     On time
## 18:28  Abbey Wood                              14    On time
## 18:30  Cardiff Central                         13    On time
## 18:33  Cheltenham Spa                          10A   On time
## 18:35  Virginia Water                          4     On time
## 18:38  Gatwick Airport                         5     On time
## 18:39  Didcot Parkway                          13A   On time
## 18:40  Bristol Temple Meads                    11    On time
## 18:44  Swansea                                 10    On time
## 18:54  London Paddington                       9     On time
## 18:56  Didcot Parkway                          10    On time
## 19:02  London Waterloo                         4     On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
## 17:23  Bramley (Hampshire)                     BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:18  Bedwyn                                  BUS   On time
## 18:23  Basingstoke                             BUS   On time
## 18:30  Newbury                                 BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 18:51  Newbury                                 BUS   On time
## 19:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-16 16:04:00
## Time   To                                      Plat  Expected
## 15:35  London Paddington                       11    17:40
## 16:55  Plymouth                                8     17:02
##        via Bristol                             
## 17:03  Penzance                                9     On time
## 17:10  Swansea                                 7     On time
## 17:14  Ealing Broadway                         15A   On time
## 17:14  London Paddington                       10    17:15
## 17:15  Didcot Parkway                          13B   17:17
## 17:16  Didcot Parkway                          9     On time
## 17:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:23  Abbey Wood                              14    On time
## 17:24  Virginia Water                          4     On time
## 17:25  Bristol Temple Meads                    9     On time
## 17:25  Didcot Parkway                          12B   On time
## 17:35  London Paddington                       11    On time
## 17:41  Redhill                                 6     On time
## 17:44  London Paddington                       10    On time
## 17:47  London Paddington                       11    On time
## 17:53  Abbey Wood                              14    On time
## 17:54  London Waterloo                         4     On time
## 17:55  Weston-super-Mare                       9B    On time
## 18:00  Cheltenham Spa                          8B    On time
## 18:01  London Paddington                       10A   On time
## 18:10  Swansea                                 8     On time
## 18:14  Ealing Broadway                         15A   On time
## 18:14  London Paddington                       10    On time
## 18:16  Didcot Parkway                          9     On time
## 18:17  London Paddington                       11    On time
## 18:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:23  Abbey Wood                              14    On time
## 18:24  Virginia Water                          4     On time
## 18:25  Didcot Parkway                          12B   On time
## 18:25  Penzance                                8     On time
## 18:28  Bristol Temple Meads                    9     On time
## 18:35  London Paddington                       10A   On time
## 18:41  Redhill                                 6     On time
## 18:44  London Paddington                       11    On time
## 18:46  Bournemouth                             13A   On time
## 18:47  London Paddington                       10    On time
## 18:53  Abbey Wood                              14    On time
## 18:54  London Waterloo                         4     On time
## 18:55  Weston-super-Mare                       9     On time
## 19:01  London Paddington                       10    On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:38  Bramley (Hampshire)                     BUS   On time
## 17:43  Bedwyn                                  BUS   On time
## 17:52  Winchester                              BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:38  Basingstoke                             BUS   On time
## 18:40  Newbury                                 BUS   On time
## 18:43  Newbury                                 BUS   On time
## 18:52  Basingstoke                             BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
```
