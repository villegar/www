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

## Example (Last rendered on 2023-04-16 18:59)

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
## Reading (RDG) Station Board on 2023-04-16 18:59:06
## Time   From                                    Plat  Expected
## 19:28  Penzance                                11    20:02
## 19:49  Carmarthen                              11    19:54
## 19:57  Didcot Parkway                          10A   On time
## 19:59  Abbey Wood                              14    On time
## 20:02  London Waterloo                         4     On time
## 20:07  London Paddington                       8     20:09
## 20:11  Bristol Temple Meads                    10    On time
## 20:11  Redhill                                 15    On time
## 20:13  Didcot Parkway                          13A   On time
## 20:14  Penzance                                11    20:17
## 20:15  London Paddington                       9B    On time
## 20:19  London Paddington                       12B   On time
## 20:26  London Paddington                       9     On time
## 20:28  Abbey Wood                              14    On time
## 20:35  Virginia Water                          4     On time
## 20:38  Gatwick Airport                         5     On time
## 20:39  Didcot Parkway                          14A   On time
## 20:49  Swansea                                 11    On time
## 20:54  London Paddington                       9     On time
## 20:57  Bournemouth                             8B    21:02
## 20:58  Abbey Wood                              14    On time
## 20:58  Didcot Parkway                          10A   On time
## 21:02  London Waterloo                         4     On time
## 21:07  London Paddington                       9     On time
## 21:11  Redhill                                 15B   On time
## 21:11  Taunton                                 10    On time
## 21:12  London Paddington                       12B   On time
## 21:13  Didcot Parkway                          13A   On time
## 21:15  London Paddington                       9B    On time
## 21:27  London Paddington                       7B    On time
## 21:27  Penzance                                11    On time
## 21:28  Abbey Wood                              14    On time
## 21:35  Virginia Water                          4     On time
## 21:40  Gatwick Airport                         15    On time
## 21:49  Swansea                                 10    On time
## 21:54  London Paddington                       9     On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
## 20:14  Bedwyn                                  BUS   On time
## 20:23  Basingstoke                             BUS   On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:51  Newbury                                 BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
## 21:00  Winchester                              BUS   On time
## 21:23  Bramley (Hampshire)                     BUS   On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-16 18:59:11
## Time   To                                      Plat  Expected
## 19:35  London Paddington                       11    20:03
## 19:56  London Paddington                       11    19:58
## 20:01  London Paddington                       10A   On time
## 20:09  Swansea                                 8     20:10
## 20:12  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:14  Ealing Broadway                         13A   On time
## 20:14  London Paddington                       10    On time
## 20:16  Didcot Parkway                          9B    On time
## 20:17  London Paddington                       11    20:17
## 20:24  Abbey Wood                              14    On time
## 20:24  Virginia Water                          4     On time
## 20:25  Didcot Parkway                          12B   On time
## 20:28  Plymouth                                9     On time
## 20:46  Southampton Central                     14A   On time
## 20:54  Abbey Wood                              14    On time
## 20:54  London Waterloo                         4     On time
## 20:55  Weston-super-Mare                       9     On time
## 20:56  London Paddington                       11    On time
## 21:01  London Paddington                       10A   On time
## 21:09  Swansea                                 9     On time
## 21:12  Didcot Parkway                          8B    On time
## 21:13  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:14  Ealing Broadway                         13A   On time
## 21:14  London Paddington                       10    On time
## 21:15  Didcot Parkway                          12B   On time
## 21:16  Didcot Parkway                          9B    On time
## 21:24  Ealing Broadway                         14    On time
## 21:24  Virginia Water                          4     On time
## 21:30  Exeter St Davids                        7B    On time
## 21:34  London Paddington                       11    On time
## 21:54  Ealing Broadway                         14    On time
## 21:54  London Waterloo                         4     On time
## 21:55  Bristol Temple Meads                    9     On time
## 21:56  London Paddington                       10    On time
## 21:58  London Paddington                       11A   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 20:38  Bramley (Hampshire)                     BUS   On time
## 20:43  Newbury                                 BUS   On time
## 20:52  Basingstoke                             BUS   On time
## 20:52  Winchester                              BUS   On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
## 21:38  Bramley (Hampshire)                     BUS   On time
## 21:43  Bedwyn                                  BUS   On time
## 21:52  Winchester                              BUS   On time
```
