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

## Example (Last rendered on 2023-02-16 22:03)

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
## Reading (RDG) Station Board on 2023-02-16 22:03:10
## Time   From                                    Plat  Expected
## 22:00  Paignton                                11    22:17
## 22:05  Didcot Parkway                          15A   On time
## 22:07  London Paddington                       13    On time
## 22:08  Exeter St Davids                        10A   22:17
## 22:11  Abbey Wood                              14    On time
## 22:11  London Paddington                       9     22:15
## 22:14  Newbury                                 1     On time
## 22:15  London Paddington                       12B   On time
## 22:16  London Paddington                       -     Cancelled
## 22:20  Newbury                                 11A   On time
## 22:25  Oxford                                  12A   On time
## 22:26  London Paddington                       9     On time
## 22:32  Cheltenham Spa                          10    On time
## 22:39  Manchester Piccadilly                   7B    On time
## 22:40  Abbey Wood                              14    On time
## 22:40  Basingstoke                             2     On time
## 22:43  London Paddington                       9B    On time
## 22:43  Swansea                                 10    On time
## 22:45  London Paddington                       12B   On time
## 22:47  Didcot Parkway                          15    On time
## 22:52  Salisbury                               3     On time
## 22:55  London Paddington                       9     On time
## 22:58  London Paddington                       7B    On time
## 22:59  Worcester Foregate Street               -     Cancelled
## 23:03  Basingstoke                             2     On time
## 23:09  Abbey Wood                              13    On time
## 23:11  Penzance                                15    On time
## 23:13  London Paddington                       7     On time
## 23:13  Newbury                                 3     On time
## 23:18  London Paddington                       8     On time
## 23:21  Didcot Parkway                          13    On time
## 23:27  Basingstoke                             3     On time
## 23:27  London Paddington                       -     Cancelled
## 23:35  Oxford                                  14A   On time
## 23:46  Didcot Parkway                          15    On time
## 23:49  Manchester Piccadilly                   7     On time
## 23:52  Basingstoke                             3     On time
## 22:05  Guildford                               BUS   On time
## 22:08  Bracknell                               BUS   On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:21  Guildford                               BUS   On time
## 22:23  Bracknell                               BUS   On time
## 22:38  Bracknell                               BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
## 22:53  Bracknell                               BUS   On time
## 23:05  Guildford                               BUS   On time
## 23:08  Bracknell                               BUS   On time
## 23:18  Heathrow Central Bus Stn                BUS   On time
## 23:21  Guildford                               BUS   On time
## 23:24  Bracknell                               BUS   On time
## 23:38  Bracknell                               BUS   On time
## 23:53  Bracknell                               -     Cancelled
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-16 22:03:15
## Time   To                                      Plat  Expected
## 22:05  Basingstoke                             3     On time
## 22:05  London Paddington                       11    22:18
## 22:08  Ealing Broadway                         15A   On time
## 22:10  London Paddington                       10A   22:18
## 22:10  Newbury                                 1     On time
## 22:13  Swansea                                 9     22:16
## 22:18  Didcot Parkway                          12B   On time
## 22:18  Worcester Shrub Hill                    -     Cancelled
## 22:20  London Paddington                       11A   On time
## 22:26  London Paddington                       12A   On time
## 22:27  Abbey Wood                              14    On time
## 22:27  Plymouth                                9     On time
##        via Bristol                             
## 22:29  Basingstoke                             2     On time
## 22:35  London Paddington                       10    On time
## 22:45  Oxford                                  9B    On time
## 22:46  London Paddington                       10    On time
## 22:47  Didcot Parkway                          12B   On time
## 22:49  Southampton Central                     7B    On time
## 22:52  Basingstoke                             2     On time
## 22:57  Abbey Wood                              14    On time
## 22:59  Bristol Temple Meads                    9     On time
## 23:01  Bedwyn                                  7B    On time
## 23:01  London Paddington                       -     Cancelled
## 23:13  London Paddington                       15    On time
## 23:19  Swansea                                 8     On time
## 23:22  Ealing Broadway                         13    On time
## 23:28  Worcestershire Parkway                  -     Cancelled
## 23:32  Didcot Parkway                          7     On time
## 23:34  Basingstoke                             2     On time
## 23:38  London Paddington                       14A   On time
## 22:09  Bracknell                               BUS   On time
## 22:17  Guildford                               BUS   On time
## 22:24  Bracknell                               BUS   On time
## 22:39  Bracknell                               BUS   On time
## 22:41  Guildford                               BUS   On time
## 22:54  Bracknell                               BUS   On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
## 23:09  Bracknell                               BUS   On time
## 23:24  Bracknell                               BUS   On time
## 23:33  Gatwick Airport                         BUS   On time
##        via Guildford                           
## 23:52  Ascot                                   BUS   On time
```
