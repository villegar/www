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

## Example (Last rendered on 2023-04-08 18:03)

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
## Reading (RDG) Station Board on 2023-04-08 18:03:49
## Time   From                                    Plat  Expected
## 19:01  Bournemouth                             13B   19:16
## 19:01  Didcot Parkway                          15    On time
## 19:03  London Paddington                       14    19:07
## 19:10  Bristol Temple Meads                    10    19:17
## 19:11  London Paddington                       8     On time
## 19:12  London Paddington                       12    On time
## 19:13  London Waterloo                         5     On time
## 19:15  Penzance                                11    19:50
## 19:17  London Paddington                       -     Cancelled
## 19:26  Didcot Parkway                          10    On time
## 19:27  London Paddington                       8     On time
## 19:31  Didcot Parkway                          15    On time
## 19:32  Redhill                                 6     On time
## 19:33  London Paddington                       14    On time
## 19:38  London Paddington                       8     On time
## 19:40  Weston-super-Mare                       10    On time
## 19:43  London Paddington                       12    On time
## 19:43  London Waterloo                         4     On time
## 19:46  Swansea                                 11    19:48
## 19:47  London Paddington                       10    On time
## 19:49  London Paddington                       8     On time
## 19:51  Gatwick Airport                         5     On time
## 19:51  London Paddington                       7     On time
## 19:54  Great Malvern                           -     Cancelled
## 19:55  London Paddington                       8B    On time
## 20:01  Didcot Parkway                          15    On time
## 20:03  London Paddington                       14    On time
## 20:10  Bristol Temple Meads                    11    On time
## 20:10  London Paddington                       12    On time
## 20:11  London Paddington                       8     On time
## 20:13  London Waterloo                         6     On time
## 20:15  Plymouth                                11    On time
## 20:17  London Paddington                       -     Cancelled
## 20:25  Oxford                                  -     Cancelled
## 20:30  London Paddington                       8     On time
## 20:31  Didcot Parkway                          15    On time
## 20:33  Cheltenham Spa                          11A   On time
## 20:33  London Paddington                       14    On time
## 20:35  Redhill                                 5     On time
## 20:40  London Paddington                       12    On time
## 20:41  London Waterloo                         4     On time
## 20:42  London Paddington                       8     On time
## 20:43  Didcot Parkway                          7     On time
## 20:46  Swansea                                 10    On time
## 20:47  London Paddington                       9     On time
## 20:54  Great Malvern                           -     Cancelled
## 20:55  London Paddington                       9     On time
## 20:58  Gatwick Airport                         15    On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:21  Bedwyn                                  BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:40  Bramley (Hampshire)                     BUS   On time
## 19:47  Newbury                                 BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
## 20:00  Newbury                                 BUS   On time
## 20:01  Basingstoke                             BUS   On time
## 20:21  Bedwyn                                  BUS   On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:40  Bramley (Hampshire)                     BUS   On time
## 20:47  Newbury                                 BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
## 21:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-08 18:03:57
## Time   To                                      Plat  Expected
## 19:09  London Waterloo                         6     On time
## 19:12  London Paddington                       10    19:18
## 19:13  Swansea                                 8     On time
## 19:15  Ealing Broadway                         15    On time
## 19:19  Hereford                                -     Cancelled
## 19:20  Gatwick Airport                         4     On time
##        via Guildford                           
## 19:20  London Paddington                       11    19:51
## 19:23  Didcot Parkway                          12    On time
## 19:24  Ealing Broadway                         14    On time
## 19:27  Plymouth                                8     On time
## 19:28  London Paddington                       10    On time
## 19:30  Bristol Temple Meads                    8     On time
## 19:39  London Waterloo                         5     On time
## 19:42  London Paddington                       10    On time
## 19:44  Swansea                                 8     On time
## 19:45  Ealing Broadway                         15    On time
## 19:48  London Paddington                       11    19:48
## 19:51  Didcot Parkway                          8     On time
## 19:53  Cheltenham Spa                          7     On time
## 19:54  Ealing Broadway                         14    On time
## 19:55  Didcot Parkway                          12    On time
## 19:56  London Paddington                       -     Cancelled
## 19:58  Taunton                                 8B    On time
## 20:01  Redhill                                 6     On time
## 20:05  Didcot Parkway                          13    On time
## 20:09  London Waterloo                         4     On time
## 20:12  London Paddington                       11    On time
## 20:13  Swansea                                 8     On time
## 20:17  London Paddington                       11    On time
## 20:19  Great Malvern                           -     Cancelled
## 20:20  Ealing Broadway                         15    On time
## 20:20  London Paddington                       10    On time
## 20:23  Didcot Parkway                          12    On time
## 20:24  Ealing Broadway                         14    On time
## 20:27  London Paddington                       -     Cancelled
## 20:29  Plymouth                                7     On time
## 20:32  Bristol Temple Meads                    8     On time
## 20:32  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:35  London Paddington                       11A   On time
## 20:39  London Waterloo                         6     On time
## 20:44  Swindon                                 8     On time
## 20:45  Ealing Broadway                         15    On time
## 20:48  London Paddington                       10    On time
## 20:49  Didcot Parkway                          9     On time
## 20:53  Didcot Parkway                          12    On time
## 20:54  Ealing Broadway                         14    On time
## 20:56  London Paddington                       -     Cancelled
## 20:56  Southampton Central                     7     On time
## 20:57  Exeter St Davids                        9     On time
##        via Bristol                             
## 19:10  Newbury                                 BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:38  Bramley (Hampshire)                     BUS   On time
## 19:40  Bedwyn                                  BUS   On time
## 19:55  Basingstoke                             BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 20:10  Newbury                                 BUS   On time
## 20:38  Bramley (Hampshire)                     BUS   On time
## 20:40  Bedwyn                                  BUS   On time
## 20:55  Winchester                              BUS   On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
```
