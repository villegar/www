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

## Example (Last rendered on 2022-08-14 14:04)

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
## Reading (RDG) Station Board on 2022-08-14 14:04:26
## Time   From                                    Plat  Expected
## 14:40  Manchester Piccadilly                   12    15:05
## 14:43  Swansea                                 10    15:24
## 15:02  London Waterloo                         4     On time
## 15:03  London Paddington                       14    15:06
## 15:05  Bournemouth                             7     15:11
## 15:08  Redhill                                 6     15:13
## 15:10  Didcot Parkway                          15    15:36
## 15:12  Penzance                                11    Delayed
## 15:13  Bristol Temple Meads                    -     Cancelled
## 15:17  London Paddington                       8     On time
## 15:24  Bedwyn                                  3     On time
## 15:25  Oxford                                  10A   On time
## 15:26  London Paddington                       9     On time
## 15:32  London Waterloo                         4     On time
## 15:33  Basingstoke                             2     15:49
## 15:33  London Paddington                       14    On time
## 15:38  Gatwick Airport                         5     On time
## 15:38  Manchester Piccadilly                   7     15:43
## 15:44  Swansea                                 10    15:56
## 15:46  London Paddington                       8B    On time
## 15:47  Salisbury                               1     15:53
## 15:53  London Paddington                       9     On time
## 16:02  London Waterloo                         4     On time
## 16:03  London Paddington                       14    On time
## 16:08  Redhill                                 6     On time
## 16:10  Didcot Parkway                          15    On time
## 16:12  Newbury                                 3     On time
## 16:13  Bristol Temple Meads                    10    On time
## 16:17  London Paddington                       8     On time
## 16:19  London Paddington                       9     On time
## 16:25  Oxford                                  10A   On time
## 16:32  London Waterloo                         4     On time
## 16:33  Basingstoke                             2     On time
## 16:33  London Paddington                       14    On time
## 16:38  Gatwick Airport                         5     On time
## 16:38  Manchester Piccadilly                   13    On time
## 16:41  Swindon                                 11    On time
## 16:44  Swansea                                 10    On time
## 16:46  London Paddington                       9     On time
## 16:47  Salisbury                               1     On time
## 17:02  London Waterloo                         4     On time
## 17:03  London Paddington                       14    On time
## 15:45  Heathrow Central Bus Stn                BUS   On time
## 16:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-08-14 14:04:29
## Time   To                                      Plat  Expected
## 14:46  London Paddington                       10    15:25
## 15:09  Swansea                                 8     On time
## 15:12  Gillingham (Dorset)                     -     Cancelled
## 15:14  Ealing Broadway                         15    15:37
## 15:15  London Paddington                       11    Delayed
## 15:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 15:18  London Paddington                       -     Cancelled
## 15:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 15:24  Ealing Broadway                         14    On time
## 15:24  London Waterloo                         4     On time
## 15:25  London Paddington                       10A   On time
## 15:26  Swindon                                 9     On time
## 15:30  Didcot Parkway                          8     On time
## 15:38  Basingstoke                             2     On time
## 15:41  Redhill                                 6     On time
## 15:43  Bedwyn                                  3     On time
## 15:49  London Paddington                       10    15:57
## 15:50  Oxford                                  8B    On time
## 15:52  Bournemouth                             7     On time
## 15:54  Ealing Broadway                         14    On time
## 15:54  London Waterloo                         4     On time
## 15:55  Bristol Temple Meads                    9     On time
## 16:09  Swansea                                 8     On time
## 16:12  Salisbury                               1     On time
## 16:14  Ealing Broadway                         15    On time
## 16:15  London Paddington                       10    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:20  Swindon                                 9     On time
## 16:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:24  Ealing Broadway                         14    On time
## 16:24  London Waterloo                         4     On time
## 16:25  London Paddington                       10A   On time
## 16:28  Penzance                                7     On time
## 16:30  Didcot Parkway                          8     On time
## 16:38  Basingstoke                             2     On time
## 16:41  Redhill                                 6     On time
## 16:42  London Paddington                       11    On time
## 16:43  Newbury                                 3     On time
## 16:46  London Paddington                       10    On time
## 16:50  Oxford                                  9     On time
## 16:54  Ealing Broadway                         14    On time
## 16:54  London Waterloo                         4     On time
## 16:55  Bristol Temple Meads                    9     On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
```
