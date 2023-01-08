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

## Example (Last rendered on 2023-01-08 10:03)

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
## Reading (RDG) Station Board on 2023-01-08 10:03:34
## Time   From                                    Plat  Expected
## 09:58  Virginia Water                          4     10:03
## 10:00  London Paddington                       8B    10:02
## 10:03  London Paddington                       14    On time
## 10:06  Southampton Central                     12B   On time
## 10:08  Redhill                                 6     10:10
## 10:12  London Paddington                       9     On time
## 10:16  London Paddington                       7     On time
## 10:16  London Paddington                       13    On time
## 10:18  Bedwyn                                  12    On time
## 10:21  Weston-super-Mare                       11    10:32
## 10:26  London Paddington                       7     On time
## 10:32  Basingstoke                             2     On time
## 10:33  London Paddington                       14    On time
## 10:35  Virginia Water                          4     On time
## 10:38  Gatwick Airport                         5     On time
## 10:38  London Paddington                       7     On time
## 10:39  Birmingham New Street                   13    On time
## 10:45  London Paddington                       8     On time
## 10:46  Oxford                                  15    On time
## 10:47  Salisbury                               1     On time
## 10:50  Cardiff Central                         11    11:15
## 10:56  Worcester Shrub Hill                    10A   11:10
## 10:58  London Waterloo                         4     On time
## 10:59  London Paddington                       7     On time
## 11:03  London Paddington                       14    On time
## 11:06  Bournemouth                             8     On time
## 11:08  Redhill                                 6     On time
## 11:12  London Paddington                       9     On time
## 11:15  London Paddington                       12    On time
## 11:16  London Paddington                       7     On time
## 11:19  Bedwyn                                  1     On time
## 11:23  Bristol Temple Meads                    11    On time
## 11:25  Oxford                                  10    On time
## 11:26  London Paddington                       7     On time
## 11:33  Abbey Wood                              14    On time
## 11:33  Basingstoke                             2     On time
## 11:34  Plymouth                                11    On time
## 11:35  Virginia Water                          4     On time
## 11:38  Gatwick Airport                         5     On time
## 11:38  London Paddington                       8     On time
## 11:39  Birmingham New Street                   7B    On time
## 11:39  Swansea                                 10    On time
## 11:45  London Paddington                       9     On time
## 11:47  Salisbury                               1     On time
## 11:56  Great Malvern                           10    On time
## 11:58  London Waterloo                         4     On time
## 11:58  Plymouth                                11    On time
## 10:04  Heathrow Central Bus Stn                BUS   On time
## 10:10  Oxford                                  BUS   On time
## 10:34  Chippenham                              BUS   On time
## 10:34  Heathrow Central Bus Stn                BUS   On time
## 11:00  Swindon                                 BUS   On time
## 11:04  Heathrow Central Bus Stn                BUS   On time
## 11:34  Heathrow Central Bus Stn                BUS   On time
## 11:50  Chippenham                              BUS   On time
## 12:00  Swindon                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-01-08 10:03:39
## Time   To                                      Plat  Expected
## 10:02  Oxford                                  8B    10:03
## 10:12  Salisbury                               1     On time
## 10:13  Hereford                                9     On time
## 10:14  Ealing Broadway                         15    On time
## 10:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 10:19  Swansea                                 7     On time
## 10:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:24  Abbey Wood                              14    On time
## 10:24  Virginia Water                          4     On time
## 10:25  London Paddington                       11    10:33
## 10:26  Didcot Parkway                          13    On time
## 10:28  Penzance                                7     On time
## 10:37  Basingstoke                             2     On time
## 10:41  Redhill                                 6     On time
## 10:42  Bristol Temple Meads                    7     On time
## 10:45  Newbury                                 3     On time
## 10:48  Oxford                                  8     On time
## 10:51  London Waterloo                         4     On time
## 10:54  Abbey Wood                              14    On time
## 10:55  London Paddington                       11    11:16
## 10:57  London Paddington                       10A   11:11
## 11:02  Paignton                                7     On time
## 11:14  Ealing Broadway                         12    On time
## 11:14  Great Malvern                           9     On time
## 11:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 11:19  Carmarthen                              7     On time
## 11:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:24  Abbey Wood                              14    On time
## 11:24  Virginia Water                          4     On time
## 11:25  London Paddington                       11    On time
## 11:26  Didcot Parkway                          12    On time
## 11:27  London Paddington                       10    On time
## 11:28  Plymouth                                7     On time
## 11:35  London Paddington                       11    On time
## 11:37  Basingstoke                             2     On time
## 11:41  Redhill                                 6     On time
## 11:42  Bristol Temple Meads                    8     On time
## 11:42  London Paddington                       10    On time
## 11:45  Bedwyn                                  1     On time
## 11:48  Oxford                                  9     On time
## 11:51  London Waterloo                         4     On time
## 11:52  Bournemouth                             7B    On time
## 11:54  Abbey Wood                              14    On time
## 11:59  London Paddington                       11    On time
## 12:02  London Paddington                       10    On time
## 10:08  Swindon                                 BUS   On time
## 10:18  Chippenham                              BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
## 11:05  Swindon                                 BUS   On time
## 11:15  Chippenham                              BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
```
