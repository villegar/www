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

## Example (Last rendered on 2023-04-08 12:03)

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
## Reading (RDG) Station Board on 2023-04-08 12:03:43
## Time   From                                    Plat  Expected
## 12:51  Gatwick Airport                         5     13:03
## 13:01  Bournemouth                             13B   13:17
## 13:02  Didcot Parkway                          15    On time
## 13:10  Bristol Temple Meads                    10    13:12
## 13:11  London Paddington                       8     On time
## 13:11  London Paddington                       12    On time
## 13:13  London Waterloo                         4     On time
## 13:15  Penzance                                11    13:23
## 13:17  London Paddington                       -     Cancelled
## 13:25  London Paddington                       8     On time
## 13:27  Didcot Parkway                          10    On time
## 13:33  Cheltenham Spa                          10A   On time
## 13:33  Didcot Parkway                          15    On time
## 13:33  London Paddington                       14    On time
## 13:33  Redhill                                 5     On time
## 13:40  Taunton                                 11A   13:43
## 13:43  London Paddington                       13    On time
## 13:43  London Waterloo                         6     On time
## 13:46  Swansea                                 10    13:49
## 13:47  London Paddington                       8     On time
## 13:51  London Paddington                       8B    On time
## 13:51  Redhill                                 4     On time
## 13:54  Great Malvern                           -     Cancelled
## 13:55  London Paddington                       8     On time
## 14:02  Didcot Parkway                          15    On time
## 14:06  London Paddington                       14    On time
## 14:10  Bristol Temple Meads                    10    On time
## 14:11  London Paddington                       8     On time
## 14:11  London Paddington                       12    On time
## 14:13  London Waterloo                         5     On time
## 14:17  London Paddington                       -     Cancelled
## 14:25  London Paddington                       8     On time
## 14:25  Oxford                                  -     Cancelled
## 14:28  Penzance                                10    On time
## 14:31  Didcot Parkway                          15    On time
## 14:33  London Paddington                       14    On time
## 14:33  Redhill                                 4     On time
## 14:35  Cheltenham Spa                          10    On time
## 14:40  Weston-super-Mare                       11    On time
## 14:43  London Paddington                       12    On time
## 14:43  London Waterloo                         6     On time
## 14:46  Swansea                                 10    On time
## 14:47  London Paddington                       9     On time
## 14:51  Gatwick Airport                         5     15:01
## 14:51  London Paddington                       8     On time
## 14:53  Worcester Foregate Street               -     Cancelled
## 14:55  London Paddington                       8     On time
## 14:56  Didcot Parkway                          7     On time
## 15:02  Bournemouth                             7     On time
## 13:04  Heathrow Central Bus Stn                BUS   On time
## 13:21  Bedwyn                                  BUS   On time
## 13:34  Heathrow Central Bus Stn                BUS   On time
## 13:40  Bramley (Hampshire)                     BUS   On time
## 13:47  Newbury                                 BUS   On time
## 14:00  Newbury                                 BUS   On time
## 14:01  Basingstoke                             BUS   On time
## 14:04  Heathrow Central Bus Stn                BUS   On time
## 14:21  Bedwyn                                  BUS   On time
## 14:34  Heathrow Central Bus Stn                BUS   On time
## 14:40  Bramley (Hampshire)                     BUS   On time
## 14:47  Newbury                                 BUS   On time
## 15:00  Newbury                                 BUS   On time
## 15:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-08 12:03:47
## Time   To                                      Plat  Expected
## 13:01  Didcot Parkway                          13B   13:17
## 13:09  London Waterloo                         6     On time
## 13:09  Penzance                                8     On time
## 13:12  London Paddington                       10    On time
## 13:13  Swansea                                 8     On time
## 13:15  Ealing Broadway                         15    On time
## 13:16  London Paddington                       11    13:27
## 13:19  Worcester Foregate Street               -     Cancelled
## 13:20  Gatwick Airport                         5     On time
##        via Guildford                           
## 13:23  Didcot Parkway                          12    On time
## 13:24  Ealing Broadway                         14    On time
## 13:27  Bristol Temple Meads                    8     On time
## 13:28  London Paddington                       10    On time
## 13:34  Redhill                                 13A   On time
## 13:35  London Paddington                       10A   On time
## 13:39  London Waterloo                         4     On time
## 13:43  London Paddington                       11A   13:43
## 13:45  Ealing Broadway                         15    On time
## 13:49  Didcot Parkway                          8     On time
## 13:50  London Paddington                       10    On time
## 13:53  Cheltenham Spa                          8B    On time
## 13:54  Ealing Broadway                         14    On time
## 13:55  Didcot Parkway                          13    On time
## 13:56  London Paddington                       -     Cancelled
## 13:57  Weston-super-Mare                       8     On time
## 14:09  London Waterloo                         6     On time
## 14:09  Penzance                                8     On time
## 14:12  London Paddington                       10    On time
## 14:13  Swansea                                 8     On time
## 14:15  Ealing Broadway                         15    On time
## 14:19  Great Malvern                           -     Cancelled
## 14:20  Redhill                                 4     On time
## 14:24  Didcot Parkway                          12    On time
## 14:24  Ealing Broadway                         14    On time
## 14:27  Bristol Temple Meads                    8     On time
## 14:27  London Paddington                       -     Cancelled
## 14:32  London Paddington                       10    On time
## 14:38  London Paddington                       10    On time
## 14:39  London Waterloo                         5     On time
## 14:42  London Paddington                       11    On time
## 14:45  Ealing Broadway                         15    On time
## 14:48  London Paddington                       10    On time
## 14:49  Didcot Parkway                          9     On time
## 14:53  Cheltenham Spa                          8     On time
## 14:53  Didcot Parkway                          12    On time
## 14:54  Ealing Broadway                         14    On time
## 14:56  Bournemouth                             7     On time
## 14:56  London Paddington                       -     Cancelled
## 14:57  Weston-super-Mare                       8     On time
## 15:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 13:10  Newbury                                 BUS   On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:38  Bramley (Hampshire)                     BUS   On time
## 13:40  Bedwyn                                  BUS   On time
## 13:44  Newbury                                 BUS   On time
## 13:55  Basingstoke                             BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
## 14:10  Newbury                                 BUS   On time
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:38  Bramley (Hampshire)                     BUS   On time
## 14:40  Bedwyn                                  BUS   On time
## 14:44  Newbury                                 BUS   On time
## 14:55  Winchester                              BUS   On time
## 15:00  Heathrow Airport T3 (Bus)               BUS   On time
```
