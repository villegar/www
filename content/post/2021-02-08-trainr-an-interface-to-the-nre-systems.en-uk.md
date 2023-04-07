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

## Example (Last rendered on 2023-04-07 06:03)

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
## Reading (RDG) Station Board on 2023-04-07 06:03:55
## Time   From                                    Plat  Expected
## 06:59  Bristol Temple Meads                    11    07:01
## 06:59  Didcot Parkway                          13    On time
## 07:06  Southampton Central                     15    07:02
## 07:08  London Paddington                       14    07:10
## 07:11  Didcot Parkway                          13    On time
## 07:11  London Paddington                       9     On time
## 07:11  London Waterloo                         4     07:16
## 07:16  London Paddington                       -     Cancelled
## 07:16  London Paddington                       12    On time
## 07:18  Swansea                                 10    On time
## 07:25  London Paddington                       9     On time
## 07:28  Cheltenham Spa                          10    On time
## 07:33  Didcot Parkway                          10    On time
## 07:33  London Paddington                       14    On time
## 07:34  Gatwick Airport                         5     On time
## 07:38  Bristol Temple Meads                    11    On time
## 07:38  London Paddington                       9     On time
## 07:43  Didcot Parkway                          15    On time
## 07:46  London Paddington                       -     Cancelled
## 07:46  London Waterloo                         6     On time
## 07:47  London Paddington                       12    On time
## 07:49  Swansea                                 11    On time
## 07:51  London Paddington                       9     On time
## 07:54  Hereford                                -     Cancelled
## 07:55  London Paddington                       8     On time
## 07:56  London Paddington                       9     On time
## 08:03  London Paddington                       14    On time
## 08:03  Plymouth                                11    Delayed
## 08:09  Weston-super-Mare                       10    On time
## 08:10  Didcot Parkway                          15    On time
## 08:11  London Paddington                       9     On time
## 08:11  London Waterloo                         4     On time
## 08:14  Redhill                                 5     On time
## 08:14  Worcester Shrub Hill                    -     Cancelled
## 08:16  London Paddington                       -     Cancelled
## 08:16  London Paddington                       12    On time
## 08:18  Swansea                                 10    On time
## 08:25  London Paddington                       9     On time
## 08:26  Cheltenham Spa                          10    On time
## 08:34  Gatwick Airport                         5     On time
## 08:39  Weston-super-Mare                       11    On time
## 08:41  London Paddington                       8     On time
## 08:42  London Waterloo                         6     On time
## 08:43  Didcot Parkway                          -     On time
## 08:43  London Paddington                       14    On time
## 08:44  Didcot Parkway                          13    On time
## 08:46  London Paddington                       9     On time
## 08:49  London Paddington                       12    On time
## 08:51  London Paddington                       9     On time
## 08:51  Swansea                                 10    On time
## 08:55  London Paddington                       8     On time
## 07:02  Newbury                                 BUS   On time
## 07:25  Heathrow Central Bus Stn                BUS   On time
## 07:30  Bedwyn                                  BUS   On time
## 07:37  Basingstoke                             BUS   On time
## 07:57  Heathrow Central Bus Stn                BUS   On time
## 08:00  Winchester                              BUS   On time
## 08:21  Bedwyn                                  BUS   On time
## 08:27  Heathrow Central Bus Stn                BUS   On time
## 08:42  Newbury                                 BUS   On time
## 08:47  Bramley (Hampshire)                     BUS   On time
## 08:55  Newbury                                 BUS   On time
## 09:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-07 06:04:01
## Time   To                                      Plat  Expected
## 07:02  London Paddington                       13    On time
## 07:05  London Paddington                       11    On time
## 07:11  London Waterloo                         6     On time
## 07:13  Swansea                                 9     On time
## 07:15  Didcot Parkway                          15    On time
## 07:17  London Paddington                       13    On time
## 07:18  Great Malvern                           -     Cancelled
## 07:20  London Paddington                       10    On time
## 07:20  Redhill                                 5     On time
## 07:24  Ealing Broadway                         14    On time
## 07:25  Didcot Parkway                          12    On time
## 07:27  Bristol Temple Meads                    9     On time
## 07:31  London Paddington                       10    On time
## 07:37  London Paddington                       10    On time
## 07:39  Cardiff Central                         9     On time
## 07:41  London Paddington                       11    On time
## 07:42  London Waterloo                         4     On time
## 07:46  London Paddington                       15    On time
## 07:49  Oxford                                  -     Cancelled
## 07:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 07:51  Didcot Parkway                          12    On time
## 07:51  London Paddington                       11    On time
## 07:53  Cheltenham Spa                          9     On time
## 07:54  Ealing Broadway                         14    On time
## 07:56  London Paddington                       -     Cancelled
## 07:57  Penzance                                8     On time
## 08:00  Bristol Temple Meads                    9     On time
## 08:10  London Paddington                       11    Delayed
## 08:11  London Waterloo                         6     On time
## 08:13  Swansea                                 9     On time
## 08:14  London Paddington                       10    On time
## 08:17  London Paddington                       15    On time
## 08:17  London Paddington                       -     Cancelled
## 08:19  Great Malvern                           -     Cancelled
## 08:20  London Paddington                       10    On time
## 08:20  Redhill                                 5     On time
## 08:24  Ealing Broadway                         14    On time
## 08:26  Didcot Parkway                          12    On time
## 08:27  Bristol Temple Meads                    9     On time
## 08:29  London Paddington                       10    On time
## 08:41  London Paddington                       11    On time
## 08:42  London Waterloo                         4     On time
## 08:43  Cardiff Central                         8     On time
## 08:47  London Paddington                       13    On time
## 08:48  Didcot Parkway                          9     On time
## 08:51  Bournemouth                             -     On time
## 08:53  Cheltenham Spa                          9     On time
## 08:53  Didcot Parkway                          12    On time
## 08:54  Ealing Broadway                         14    On time
## 08:54  London Paddington                       10    On time
## 08:57  Bristol Temple Meads                    8     On time
## 09:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 07:10  Newbury                                 BUS   On time
## 07:30  Heathrow Airport T3 (Bus)               BUS   On time
## 07:38  Bramley (Hampshire)                     BUS   On time
## 07:40  Bedwyn                                  BUS   On time
## 08:00  Heathrow Airport T3 (Bus)               BUS   On time
## 08:00  Winchester                              BUS   On time
## 08:10  Newbury                                 BUS   On time
## 08:30  Basingstoke                             BUS   On time
## 08:30  Heathrow Airport T3 (Bus)               BUS   On time
## 08:38  Bramley (Hampshire)                     BUS   On time
## 08:40  Bedwyn                                  BUS   On time
## 08:44  Newbury                                 BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
## 09:00  Winchester                              BUS   On time
```
