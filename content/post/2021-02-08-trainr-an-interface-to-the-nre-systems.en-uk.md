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

## Example (Last rendered on 2023-04-10 18:03)

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
## Reading (RDG) Station Board on 2023-04-10 18:03:49
## Time   From                                    Plat  Expected
## 18:42  London Paddington                       9     Delayed
## 18:53  London Paddington                       8     19:00
## 18:53  London Paddington                       12    Delayed
## 18:59  London Paddington                       7     19:25
## 19:03  London Paddington                       13    19:06
## 19:05  Didcot Parkway                          15A   19:01
## 19:09  Gatwick Airport                         14    On time
## 19:10  Weston-super-Mare                       10    19:14
## 19:11  Bournemouth                             8B    19:23
## 19:18  Cardiff Central                         10    On time
## 19:20  London Waterloo                         5     On time
## 19:20  Penzance                                11    On time
## 19:23  Didcot Parkway                          10    On time
## 19:26  London Paddington                       8     19:36
## 19:28  Didcot Parkway                          15A   On time
## 19:31  Cheltenham Spa                          11A   On time
## 19:33  Redhill                                 4     19:42
## 19:34  London Paddington                       12    On time
## 19:38  London Paddington                       13    On time
## 19:39  Bristol Temple Meads                    10    On time
## 19:47  Swansea                                 10    On time
## 19:48  London Waterloo                         5     On time
## 19:51  London Paddington                       9B    On time
## 19:53  London Paddington                       7B    On time
## 19:55  London Paddington                       12    On time
## 19:56  London Paddington                       9     On time
## 19:58  Didcot Parkway                          15A   On time
## 20:00  Plymouth                                11    On time
## 20:03  London Paddington                       14    On time
## 20:03  London Paddington                       9     On time
## 20:04  Gatwick Airport                         4     On time
## 20:10  Weston-super-Mare                       10    On time
## 20:11  London Paddington                       9     On time
## 20:11  London Waterloo                         6     On time
## 20:17  London Paddington                       12B   On time
## 20:24  London Paddington                       9     On time
## 20:32  Cheltenham Spa                          10A   On time
## 20:33  London Paddington                       14    On time
## 20:34  Didcot Parkway                          13A   On time
## 20:35  Redhill                                 15    On time
## 20:41  London Waterloo                         4     On time
## 20:42  Didcot Parkway                          8B    On time
## 20:44  Swansea                                 10    On time
## 20:46  London Paddington                       12    On time
## 20:51  London Paddington                       7B    On time
## 20:53  Gatwick Airport                         6     On time
## 20:55  London Paddington                       9     On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:21  Bedwyn                                  BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:40  Bramley (Hampshire)                     BUS   On time
## 19:47  Newbury                                 BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
## 20:00  Newbury                                 BUS   On time
## 20:00  Winchester                              BUS   On time
## 20:21  Bedwyn                                  BUS   On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:40  Bramley (Hampshire)                     BUS   On time
## 20:47  Newbury                                 -     Cancelled
## 20:55  Heathrow Central Bus Stn                BUS   On time
## 21:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-10 18:03:57
## Time   To                                      Plat  Expected
## 18:43  Swansea                                 9     Delayed
## 18:57  Didcot Parkway                          12    Delayed
## 19:00  Weston-super-Mare                       9B    19:06
## 19:01  Plymouth                                7     19:26
## 19:12  Ealing Broadway                         15A   On time
## 19:12  London Waterloo                         6     On time
## 19:13  London Paddington                       10    19:15
## 19:13  Swansea                                 9B    19:17
## 19:15  Didcot Parkway                          8B    19:24
## 19:20  London Paddington                       10    On time
## 19:20  Redhill                                 15A   On time
## 19:24  Ealing Broadway                         13A   On time
## 19:24  London Paddington                       11    On time
## 19:27  Bristol Temple Meads                    8     19:37
## 19:27  London Paddington                       10    On time
## 19:34  Didcot Parkway                          12    On time
## 19:34  London Paddington                       11A   On time
## 19:37  Ealing Broadway                         15A   On time
## 19:41  London Paddington                       10    On time
## 19:42  London Waterloo                         5     On time
## 19:43  Swansea                                 9B    On time
## 19:50  London Paddington                       10    On time
## 19:53  Worcester Shrub Hill                    9B    On time
##        via Gloucester                          
## 19:54  Ealing Broadway                         13A   On time
## 19:55  Didcot Parkway                          7B    On time
## 19:57  Didcot Parkway                          12    On time
## 20:00  Weston-super-Mare                       9     On time
## 20:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 20:02  London Paddington                       11    On time
## 20:05  Plymouth                                9     On time
## 20:12  London Paddington                       10    On time
## 20:12  London Waterloo                         5     On time
## 20:13  Ealing Broadway                         15A   On time
## 20:13  Swansea                                 9     On time
## 20:20  Shalford                                4     On time
## 20:23  Didcot Parkway                          12B   On time
## 20:24  Ealing Broadway                         14A   On time
## 20:27  Bristol Temple Meads                    9     On time
## 20:36  London Paddington                       10A   On time
## 20:41  London Waterloo                         6     On time
## 20:45  Ealing Broadway                         13A   On time
## 20:47  London Paddington                       10    On time
## 20:51  Didcot Parkway                          12    On time
## 20:53  Cheltenham Spa                          7B    On time
## 20:54  Ealing Broadway                         14A   On time
## 20:57  Weston-super-Mare                       9     On time
## 21:01  Gatwick Airport                         6     On time
##        via Guildford                           
## 19:10  Newbury                                 BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:38  Bramley (Hampshire)                     BUS   On time
## 19:40  Bedwyn                                  BUS   On time
## 19:55  Winchester                              BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 20:10  Newbury                                 BUS   On time
## 20:38  Bramley (Hampshire)                     BUS   On time
## 20:40  Bedwyn                                  BUS   On time
## 20:55  Basingstoke                             BUS   On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
```
