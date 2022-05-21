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

## Example (Last rendered on 2022-05-21 20:03)

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
## Reading (RDG) Station Board on 2022-05-21 20:03:44
## Time   From                                    Plat  Expected
## 20:46  Swansea                                 10    21:19
## 20:54  Worcester Foregate Street               10A   21:03
## 21:04  Didcot Parkway                          15    On time
## 21:05  Bournemouth                             13B   Delayed
## 21:10  Bristol Temple Meads                    10    On time
## 21:11  London Paddington                       9     On time
## 21:13  London Paddington                       12    On time
## 21:15  Penzance                                11    21:21
## 21:17  London Paddington                       9B    On time
## 21:18  London Waterloo                         6     On time
## 21:22  Basingstoke                             2     On time
## 21:25  Bedwyn                                  12B   On time
## 21:25  Oxford                                  10A   On time
## 21:31  Didcot Parkway                          13    On time
## 21:33  Cheltenham Spa                          -     Cancelled
## 21:33  London Paddington                       14    On time
## 21:36  London Paddington                       12    On time
## 21:39  Manchester Piccadilly                   7B    On time
## 21:40  Newbury                                 1     On time
## 21:43  Penzance                                11    On time
## 21:45  London Paddington                       13    On time
## 21:47  London Waterloo                         5     On time
## 21:49  Swansea                                 10    21:52
## 21:50  Basingstoke                             2     On time
## 21:51  London Paddington                       8     On time
## 21:51  Redhill                                 15B   On time
## 21:54  Worcester Foregate Street               10A   On time
## 21:56  London Paddington                       9     On time
## 21:58  Gatwick Airport                         15    On time
## 22:04  London Paddington                       14    On time
## 22:09  Taunton                                 10    On time
## 22:13  London Paddington                       12    On time
## 22:17  London Paddington                       8     On time
## 22:18  London Waterloo                         4     On time
## 22:19  Basingstoke                             2     On time
## 22:22  Newbury                                 1     On time
## 22:25  London Paddington                       9     On time
## 22:26  Gatwick Airport                         13    On time
## 22:27  Didcot Parkway                          15    On time
## 22:29  Oxford                                  11    On time
## 22:33  London Paddington                       -     Cancelled
## 22:36  Cheltenham Spa                          10A   On time
## 22:41  Manchester Piccadilly                   7     On time
## 22:43  London Paddington                       12    On time
## 22:50  Basingstoke                             2     On time
## 22:50  London Waterloo                         6     On time
## 22:51  London Paddington                       8     On time
## 22:53  London Paddington                       9     On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
## 22:15  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-05-21 20:03:48
## Time   To                                      Plat  Expected
## 20:48  London Paddington                       10    21:20
## 20:56  London Paddington                       10A   21:04
## 21:05  Basingstoke                             2     On time
## 21:10  Newbury                                 7B    On time
## 21:12  London Waterloo                         4     On time
## 21:13  London Paddington                       10    On time
## 21:13  Swansea                                 9     On time
## 21:15  Birmingham New Street                   13B   Delayed
##        via Coventry                            
## 21:15  Ealing Broadway                         15    On time
## 21:16  London Paddington                       11    21:22
## 21:19  Oxford                                  9B    On time
## 21:21  Didcot Parkway                          12    On time
## 21:24  Ealing Broadway                         14    On time
## 21:26  London Paddington                       10A   On time
## 21:33  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:35  Basingstoke                             2     On time
## 21:35  London Paddington                       -     Cancelled
## 21:41  Ealing Broadway                         13    On time
## 21:42  London Waterloo                         6     On time
## 21:45  London Paddington                       11    On time
## 21:51  London Paddington                       10    21:53
## 21:52  Bournemouth                             7B    On time
## 21:52  Ealing Broadway                         14    On time
## 21:53  Oxford                                  8     On time
## 21:56  London Paddington                       10A   On time
## 21:57  Bristol Temple Meads                    9     On time
## 22:05  Basingstoke                             2     On time
## 22:07  Ealing Broadway                         13    On time
## 22:10  Newbury                                 1     On time
## 22:12  London Waterloo                         5     On time
## 22:15  London Paddington                       10    On time
## 22:19  Worcester Shrub Hill                    8     On time
## 22:22  Ealing Broadway                         14    On time
## 22:27  Bristol Parkway                         9     On time
## 22:30  Didcot Parkway                          12    On time
## 22:34  London Paddington                       11    On time
## 22:35  Basingstoke                             2     On time
## 22:39  London Paddington                       10A   On time
## 22:42  London Waterloo                         4     On time
## 22:51  Oxford                                  8     On time
## 22:52  Ealing Broadway                         -     Cancelled
## 22:52  Southampton Central                     7     On time
## 22:55  Bristol Temple Meads                    9     On time
## 23:00  Didcot Parkway                          12    On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
## 23:00  Heathrow Central Bus Stn                BUS   On time
```
