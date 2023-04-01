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

## Example (Last rendered on 2023-04-01 20:03)

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
## Reading (RDG) Station Board on 2023-04-01 20:03:51
## Time   From                                    Plat  Expected
## 20:54  Great Malvern                           10A   21:02
## 21:03  Abbey Wood                              14    On time
## 21:04  Didcot Parkway                          15A   On time
## 21:06  Bournemouth                             13B   On time
## 21:10  Bristol Temple Meads                    10    On time
## 21:10  London Paddington                       12B   On time
## 21:11  London Paddington                       -     Cancelled
## 21:13  London Waterloo                         6     On time
## 21:15  Penzance                                11    21:32
## 21:17  London Paddington                       -     Cancelled
## 21:22  Basingstoke                             2     On time
## 21:25  Oxford                                  10A   On time
## 21:27  Bedwyn                                  12B   On time
## 21:31  Didcot Parkway                          13    On time
## 21:33  Abbey Wood                              14    On time
## 21:33  Cheltenham Spa                          -     Cancelled
## 21:36  London Paddington                       12    On time
## 21:40  Manchester Piccadilly                   7B    On time
## 21:40  Newbury                                 1     On time
## 21:42  London Waterloo                         5     On time
## 21:45  London Paddington                       13    On time
## 21:49  Swansea                                 10    22:37
## 21:50  Basingstoke                             2     On time
## 21:51  London Paddington                       8B    On time
## 21:51  Redhill                                 15B   Delayed
## 21:54  Worcester Foregate Street               11A   On time
## 21:56  London Paddington                       9     On time
## 21:58  Gatwick Airport                         -     Cancelled
## 22:03  Abbey Wood                              14    On time
## 22:09  Taunton                                 -     Cancelled
## 22:10  London Paddington                       12    On time
## 22:13  London Waterloo                         4     On time
## 22:17  London Paddington                       8B    On time
## 22:19  Basingstoke                             2     On time
## 22:23  Newbury                                 15    On time
## 22:25  London Paddington                       9     On time
## 22:26  Gatwick Airport                         -     Cancelled
## 22:27  Didcot Parkway                          15    On time
## 22:29  Oxford                                  10    On time
## 22:33  Abbey Wood                              14    On time
## 22:36  Cheltenham Spa                          9     On time
## 22:39  Manchester Piccadilly                   7     On time
## 22:40  London Paddington                       13    On time
## 22:43  London Waterloo                         5     On time
## 22:50  Basingstoke                             12B   On time
## 22:51  London Paddington                       10    On time
## 22:54  London Paddington                       9     On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-01 20:03:58
## Time   To                                      Plat  Expected
## 20:56  London Paddington                       10A   21:03
## 21:05  Basingstoke                             2     On time
## 21:09  London Waterloo                         4     On time
## 21:10  Newbury                                 7B    On time
## 21:13  London Paddington                       10    21:19
## 21:13  Swansea                                 -     Cancelled
## 21:15  Birmingham New Street                   13B   On time
##        via Coventry                            
## 21:15  Ealing Broadway                         15A   On time
## 21:16  London Paddington                       11    21:33
## 21:19  Oxford                                  -     Cancelled
## 21:21  Didcot Parkway                          12B   On time
## 21:24  Abbey Wood                              14    On time
## 21:26  London Paddington                       10A   On time
## 21:33  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:35  Basingstoke                             2     On time
## 21:35  London Paddington                       -     Cancelled
## 21:39  London Waterloo                         6     On time
## 21:41  Ealing Broadway                         13    On time
## 21:51  London Paddington                       10    22:38
## 21:52  Abbey Wood                              14    On time
## 21:52  Bournemouth                             7B    On time
## 21:53  Oxford                                  8B    On time
## 21:56  London Paddington                       11A   On time
## 21:57  Bristol Temple Meads                    9     On time
## 22:05  Basingstoke                             2     On time
## 22:09  London Waterloo                         5     On time
## 22:10  Newbury                                 1     On time
## 22:15  London Paddington                       -     Cancelled
## 22:16  Ealing Broadway                         13    On time
## 22:19  Worcester Shrub Hill                    8B    On time
## 22:22  Abbey Wood                              14    On time
## 22:27  Bristol Parkway                         9     On time
## 22:30  Didcot Parkway                          12    On time
## 22:34  London Paddington                       10    On time
## 22:35  Basingstoke                             2     On time
## 22:39  London Paddington                       9     On time
## 22:39  London Waterloo                         4     On time
## 22:52  Abbey Wood                              14    On time
## 22:52  Southampton Central                     7     On time
## 22:56  Bristol Temple Meads                    9     On time
## 23:01  Didcot Parkway                          13    On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
```
