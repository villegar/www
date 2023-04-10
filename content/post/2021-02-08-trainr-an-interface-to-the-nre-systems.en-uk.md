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

## Example (Last rendered on 2023-04-10 14:04)

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
## Reading (RDG) Station Board on 2023-04-10 14:04:16
## Time   From                                    Plat  Expected
## 14:59  Didcot Parkway                          15    On time
## 15:06  Bournemouth                             8B    15:02
## 15:06  London Paddington                       14    On time
## 15:09  Bristol Temple Meads                    10    On time
## 15:11  London Paddington                       9     On time
## 15:11  London Waterloo                         4     On time
## 15:15  Cardiff Central                         11    15:18
## 15:17  London Paddington                       12    On time
## 15:20  Penzance                                10    15:43
## 15:25  Didcot Parkway                          11A   On time
## 15:25  London Paddington                       9     On time
## 15:30  Cheltenham Spa                          10A   On time
## 15:33  London Paddington                       14    On time
## 15:33  Redhill                                 5     On time
## 15:35  Didcot Parkway                          15    On time
## 15:39  Bristol Temple Meads                    11    On time
## 15:41  London Paddington                       9     On time
## 15:41  London Waterloo                         6     On time
## 15:43  London Paddington                       12    On time
## 15:44  Swansea                                 10    Delayed
## 15:46  London Paddington                       9B    Delayed
## 15:51  Gatwick Airport                         4     On time
## 15:51  London Paddington                       9B    On time
## 15:56  London Paddington                       9     On time
## 16:00  London Paddington                       9     On time
## 16:03  London Paddington                       13    On time
## 16:07  Didcot Parkway                          15    On time
## 16:09  Bristol Temple Meads                    10    On time
## 16:11  London Paddington                       9     On time
## 16:11  London Waterloo                         4     On time
## 16:16  Cardiff Central                         11A   On time
## 16:16  London Paddington                       9     On time
## 16:21  London Paddington                       12    On time
## 16:25  London Paddington                       9     On time
## 16:29  Cheltenham Spa                          11A   On time
## 16:31  Didcot Parkway                          15    On time
## 16:33  Plymouth                                10    On time
## 16:33  Redhill                                 5     On time
## 16:36  London Paddington                       13    On time
## 16:39  Bristol Temple Meads                    11    On time
## 16:41  Didcot Parkway                          15B   On time
## 16:41  London Paddington                       9     On time
## 16:42  London Paddington                       12B   On time
## 16:45  Swansea                                 10    On time
## 16:46  London Paddington                       9B    On time
## 16:48  London Waterloo                         6     On time
## 16:53  Didcot Parkway                          10    On time
## 16:53  London Paddington                       9B    On time
## 16:56  London Paddington                       8     On time
## 16:59  London Paddington                       9     On time
## 17:03  Gatwick Airport                         5     On time
## 17:03  London Paddington                       14    On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
## 15:21  Bedwyn                                  BUS   On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
## 15:40  Bramley (Hampshire)                     BUS   On time
## 15:47  Newbury                                 BUS   On time
## 16:00  Newbury                                 BUS   On time
## 16:01  Basingstoke                             BUS   On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:21  Bedwyn                                  BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 16:40  Bramley (Hampshire)                     BUS   On time
## 16:47  Newbury                                 BUS   On time
## 17:00  Newbury                                 BUS   On time
## 17:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-10 14:04:23
## Time   To                                      Plat  Expected
## 15:11  London Waterloo                         6     On time
## 15:12  Ealing Broadway                         15    On time
## 15:13  London Paddington                       10    On time
## 15:13  Swansea                                 9     On time
## 15:15  Didcot Parkway                          8B    On time
## 15:18  London Paddington                       11    15:18
## 15:20  London Paddington                       10    15:43
## 15:20  Redhill                                 5     On time
## 15:23  Didcot Parkway                          12    On time
## 15:24  Ealing Broadway                         14    On time
## 15:27  Bristol Temple Meads                    9     On time
## 15:27  London Paddington                       11A   On time
## 15:34  London Paddington                       10A   On time
## 15:42  Ealing Broadway                         15    On time
## 15:42  London Waterloo                         4     On time
## 15:43  Cardiff Central                         9     On time
## 15:43  London Paddington                       11    On time
## 15:45  London Paddington                       10    Delayed
## 15:48  Worcester Foregate Street               9B    Delayed
## 15:51  Didcot Parkway                          12    On time
## 15:53  Cheltenham Spa                          9B    On time
## 15:54  Ealing Broadway                         14    On time
## 15:58  Weston-super-Mare                       9     On time
## 16:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 16:04  Penzance                                9     On time
## 16:12  Ealing Broadway                         15    On time
## 16:12  London Paddington                       10    On time
## 16:12  London Waterloo                         6     On time
## 16:13  Swansea                                 9     On time
## 16:18  Didcot Parkway                          9     On time
## 16:18  London Paddington                       11A   On time
## 16:20  Redhill                                 5     On time
## 16:24  Ealing Broadway                         13    On time
## 16:25  Didcot Parkway                          12    On time
## 16:27  Bristol Temple Meads                    9     On time
## 16:32  London Paddington                       11A   On time
## 16:37  London Paddington                       10    On time
## 16:38  Ealing Broadway                         15    On time
## 16:41  London Waterloo                         4     On time
## 16:42  London Paddington                       11    On time
## 16:43  Swansea                                 9     On time
## 16:47  London Paddington                       10    On time
## 16:48  Didcot Parkway                          9B    On time
## 16:50  Didcot Parkway                          12B   On time
## 16:53  Bournemouth                             15B   On time
## 16:54  Ealing Broadway                         13    On time
## 16:55  Cheltenham Spa                          9B    On time
## 16:57  London Paddington                       10    On time
## 16:59  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:00  Taunton                                 8     On time
## 17:02  Penzance                                9     On time
## 15:10  Newbury                                 -     On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:38  Bramley (Hampshire)                     BUS   On time
## 15:40  Bedwyn                                  BUS   On time
## 15:44  Newbury                                 BUS   On time
## 15:55  Basingstoke                             BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
## 16:10  Newbury                                 BUS   On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:38  Bramley (Hampshire)                     BUS   On time
## 16:40  Bedwyn                                  BUS   On time
## 16:44  Newbury                                 BUS   On time
## 16:55  Winchester                              BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
```
