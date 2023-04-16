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

## Example (Last rendered on 2023-04-16 14:03)

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
## Reading (RDG) Station Board on 2023-04-16 14:03:42
## Time   From                                    Plat  Expected
## 14:14  Penzance                                11    15:46
## 14:53  Bournemouth                             13B   On time
## 14:59  Abbey Wood                              14    15:06
## 14:59  Didcot Parkway                          15A   On time
## 15:02  London Waterloo                         4     On time
## 15:07  London Paddington                       7     On time
## 15:09  Weston-super-Mare                       11    15:14
## 15:10  Redhill                                 6     On time
## 15:13  Didcot Parkway                          15A   On time
## 15:13  London Paddington                       12B   On time
## 15:15  London Paddington                       9B    On time
## 15:24  London Paddington                       9     On time
## 15:28  Abbey Wood                              14    15:30
## 15:28  Penzance                                11    17:21
## 15:35  Virginia Water                          4     On time
## 15:38  Gatwick Airport                         5     On time
## 15:45  Swansea                                 11A   15:48
## 15:54  London Paddington                       8     On time
## 15:56  Didcot Parkway                          10    On time
## 15:58  Abbey Wood                              14    On time
## 16:02  London Waterloo                         4     On time
## 16:07  London Paddington                       8     On time
## 16:10  Bristol Temple Meads                    10A   On time
## 16:10  Redhill                                 6     On time
## 16:13  Didcot Parkway                          15A   On time
## 16:13  London Paddington                       12B   On time
## 16:14  Plymouth                                11    On time
## 16:15  London Paddington                       9     On time
## 16:24  London Paddington                       9     On time
## 16:28  Abbey Wood                              12    On time
## 16:32  Cheltenham Spa                          10A   On time
## 16:35  Virginia Water                          4     On time
## 16:38  Gatwick Airport                         5     On time
## 16:39  Bristol Temple Meads                    11    On time
## 16:39  Didcot Parkway                          13A   On time
## 16:45  Swansea                                 10    On time
## 16:54  London Paddington                       8     On time
## 16:56  Didcot Parkway                          10    On time
## 16:59  Abbey Wood                              14    On time
## 17:02  London Waterloo                         4     On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
## 15:23  Bramley (Hampshire)                     BUS   On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:18  Bedwyn                                  BUS   On time
## 16:23  Basingstoke                             BUS   On time
## 16:25  Newbury                                 BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 16:44  Newbury                                 BUS   On time
## 17:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-16 14:03:48
## Time   To                                      Plat  Expected
## 14:17  London Paddington                       11    15:47
## 15:01  London Paddington                       15A   15:03
## 15:03  Plymouth                                9     On time
## 15:10  Swansea                                 7     On time
## 15:14  Ealing Broadway                         15A   On time
## 15:14  London Paddington                       11    15:15
## 15:15  Didcot Parkway                          13B   On time
## 15:16  Didcot Parkway                          9B    On time
## 15:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 15:23  Abbey Wood                              14    On time
## 15:24  Virginia Water                          4     On time
## 15:25  Bristol Temple Meads                    9     On time
## 15:25  Didcot Parkway                          12B   On time
## 15:35  London Paddington                       11    17:22
## 15:41  Redhill                                 6     On time
## 15:47  London Paddington                       11A   15:49
## 15:53  Abbey Wood                              14    On time
## 15:54  London Waterloo                         4     On time
## 15:55  Taunton                                 8     On time
## 16:01  London Paddington                       10    On time
## 16:03  Penzance                                9     On time
## 16:10  Swansea                                 8     On time
## 16:14  Ealing Broadway                         15A   On time
## 16:14  London Paddington                       10A   On time
## 16:16  Didcot Parkway                          9     On time
## 16:17  London Paddington                       11    On time
## 16:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:23  Abbey Wood                              14    On time
## 16:24  Virginia Water                          4     On time
## 16:25  Bristol Temple Meads                    9     On time
## 16:25  Didcot Parkway                          12B   On time
## 16:35  London Paddington                       10A   On time
## 16:41  Redhill                                 6     On time
## 16:44  London Paddington                       11    On time
## 16:46  Bournemouth                             13A   On time
## 16:47  London Paddington                       10    On time
## 16:53  Abbey Wood                              12    On time
## 16:54  London Waterloo                         4     On time
## 16:55  Plymouth                                8     On time
##        via Bristol                             
## 17:01  London Paddington                       10    On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:38  Bramley (Hampshire)                     BUS   On time
## 15:43  Bedwyn                                  BUS   On time
## 15:52  Winchester                              BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:38  Basingstoke                             BUS   On time
## 16:40  Newbury                                 BUS   On time
## 16:43  Newbury                                 BUS   On time
## 16:52  Basingstoke                             BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
```
