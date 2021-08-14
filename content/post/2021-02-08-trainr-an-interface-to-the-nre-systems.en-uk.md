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

## Example (Last rendered on 2021-08-14 12:03)

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
## Reading (RDG) Station Board on 2021-08-14 12:03:26
## Time   From                                    Plat  Expected
## 12:59  Penzance                                11    13:09
## 13:02  Didcot Parkway                          15    On time
## 13:05  Bournemouth                             13B   13:07
## 13:10  Bristol Parkway                         10    13:34
## 13:11  London Paddington                       9     On time
## 13:11  London Waterloo                         4     On time
## 13:13  London Paddington                       14    On time
## 13:17  London Paddington                       9     On time
## 13:21  Newbury                                 11    On time
## 13:25  London Paddington                       9     13:44
## 13:26  Oxford                                  10    On time
## 13:31  Cheltenham Spa                          11A   On time
## 13:33  London Paddington                       7     On time
## 13:33  Redhill                                 5     On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:40  Bath Spa                                -     Cancelled
## 13:42  London Waterloo                         6     On time
## 13:42  Newbury                                 15    On time
## 13:43  London Paddington                       14    On time
## 13:44  London Paddington                       13    On time
## 13:44  Paignton                                -     Cancelled
## 13:46  Carmarthen                              10    On time
## 13:47  London Paddington                       9     On time
## 13:51  Gatwick Airport                         4     Delayed
## 13:51  London Paddington                       8     On time
## 13:53  Basingstoke                             2     On time
## 13:54  Great Malvern                           10A   On time
## 13:55  London Paddington                       -     Cancelled
## 13:59  Penzance                                11    14:01
## 14:05  Didcot Parkway                          13    On time
## 14:10  Bristol Parkway                         10    On time
## 14:11  London Paddington                       9     On time
## 14:11  London Waterloo                         5     On time
## 14:13  London Paddington                       14    On time
## 14:17  London Paddington                       9     On time
## 14:23  Newbury                                 11    On time
## 14:25  London Paddington                       9     On time
## 14:25  Oxford                                  10    On time
## 14:33  Cheltenham Spa                          11    On time
## 14:33  London Paddington                       7     On time
## 14:33  Redhill                                 4     On time
## 14:40  Bath Spa                                10    On time
## 14:40  Manchester Piccadilly                   7     On time
## 14:41  London Waterloo                         6     On time
## 14:42  Newbury                                 15    On time
## 14:43  London Paddington                       14    On time
## 14:44  London Paddington                       12    On time
## 14:46  Swansea                                 -     Cancelled
## 14:47  London Paddington                       9     On time
## 14:51  Basingstoke                             2     On time
## 14:51  Gatwick Airport                         5     On time
## 14:51  London Paddington                       -     Cancelled
## 14:53  Worcester Foregate Street               10    On time
## 14:55  London Paddington                       9     On time
## 13:21  Heathrow Central Bus Stn                BUS   On time
## 14:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-08-14 12:03:29
## Time   To                                      Plat  Expected
## 13:01  Paignton                                -     Cancelled
## 13:05  London Paddington                       11    13:10
## 13:10  Newbury                                 8A    On time
## 13:12  London Paddington                       10    13:35
## 13:12  London Waterloo                         6     On time
## 13:13  Swansea                                 9     On time
## 13:15  Ealing Broadway                         15    On time
## 13:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 13:19  Worcester Foregate Street               9     On time
## 13:20  Redhill                                 5     On time
## 13:22  Ealing Broadway                         14    On time
## 13:25  London Paddington                       11    On time
## 13:27  Bath Spa                                9     13:45
## 13:28  London Paddington                       10    On time
## 13:30  Penzance                                7     13:47
## 13:35  London Paddington                       11A   On time
## 13:35  Newbury                                 7     On time
## 13:36  Gatwick Airport                         5     On time
##        via Guildford                           
## 13:38  Basingstoke                             2     On time
## 13:42  London Paddington                       -     Cancelled
## 13:42  London Waterloo                         4     On time
## 13:46  London Paddington                       -     Cancelled
## 13:48  London Paddington                       10    On time
## 13:49  Oxford                                  9     On time
## 13:52  Ealing Broadway                         14    On time
## 13:53  Cheltenham Spa                          8     On time
## 13:55  Didcot Parkway                          13    On time
## 13:56  London Paddington                       10A   On time
## 13:57  Bristol Temple Meads                    -     Cancelled
## 14:05  London Paddington                       11    On time
## 14:11  Newbury                                 15    On time
## 14:12  London Paddington                       10    On time
## 14:12  London Waterloo                         6     On time
## 14:13  Swansea                                 9     On time
## 14:15  Ealing Broadway                         13    On time
## 14:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 14:19  Great Malvern                           9     On time
## 14:20  Redhill                                 4     On time
## 14:22  Ealing Broadway                         14    On time
## 14:24  London Paddington                       11    On time
## 14:27  Bath Spa                                9     On time
## 14:27  London Paddington                       10    On time
## 14:29  Penzance                                7     On time
## 14:34  Newbury                                 7     On time
## 14:35  London Paddington                       11    On time
## 14:37  Basingstoke                             2     On time
## 14:42  London Paddington                       10    On time
## 14:42  London Waterloo                         5     On time
## 14:48  London Paddington                       -     Cancelled
## 14:49  Oxford                                  9     On time
## 14:52  Bournemouth                             7     On time
## 14:52  Ealing Broadway                         14    On time
## 14:53  Cheltenham Spa                          -     Cancelled
## 14:53  Didcot Parkway                          12    On time
## 14:56  London Paddington                       10    On time
## 14:57  Bristol Parkway                         9     On time
## 15:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 15:01  Plymouth                                -     Cancelled
## 14:00  Heathrow Central Bus Stn                BUS   On time
## 15:00  Heathrow Central Bus Stn                BUS   On time
```
