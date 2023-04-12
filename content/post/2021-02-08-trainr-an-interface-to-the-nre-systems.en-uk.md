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

## Example (Last rendered on 2023-04-12 10:03)

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
## Reading (RDG) Station Board on 2023-04-12 10:03:50
## Time   From                                    Plat  Expected
## 10:55  London Paddington                       8     11:01
## 10:57  Penzance                                11    11:07
## 10:58  Didcot Parkway                          15A   On time
## 10:59  London Paddington                       7     11:03
## 11:06  Bournemouth                             8B    On time
## 11:09  Abbey Wood                              -     Cancelled
## 11:09  Bristol Temple Meads                    10    11:14
## 11:11  London Paddington                       9     11:15
## 11:11  London Waterloo                         4     On time
## 11:15  London Paddington                       12    11:17
## 11:18  Cardiff Central                         10    On time
## 11:19  Basingstoke                             2     On time
## 11:25  London Paddington                       9     On time
## 11:26  Didcot Parkway                          10    On time
## 11:27  London Paddington                       8B    On time
## 11:30  Cheltenham Spa                          11A   11:34
## 11:30  Didcot Parkway                          15A   On time
## 11:33  London Paddington                       7B    On time
## 11:33  Redhill                                 5     On time
## 11:36  Newbury                                 3     On time
## 11:38  Plymouth                                11    11:42
## 11:40  Abbey Wood                              -     Cancelled
## 11:40  Bristol Temple Meads                    10    On time
## 11:41  Didcot Parkway                          8     On time
## 11:41  London Paddington                       9     On time
## 11:43  London Waterloo                         6     On time
## 11:44  London Paddington                       13B   On time
## 11:46  London Paddington                       9     On time
## 11:46  Swansea                                 11    11:50
## 11:50  Basingstoke                             2     On time
## 11:51  Gatwick Airport                         5     On time
## 11:51  London Paddington                       7B    On time
## 11:55  London Paddington                       9     On time
## 11:59  Didcot Parkway                          15A   On time
## 12:02  Penzance                                11A   12:49
## 12:09  Abbey Wood                              14    12:15
## 12:09  Bristol Temple Meads                    10    On time
## 12:11  London Paddington                       9B    On time
## 12:11  London Waterloo                         4     On time
## 12:14  Cardiff Central                         11    On time
## 12:14  London Paddington                       12B   On time
## 12:18  Basingstoke                             2     On time
## 12:22  Newbury                                 11    On time
## 12:24  Didcot Parkway                          10    On time
## 12:25  London Paddington                       9     On time
## 12:27  London Paddington                       7     On time
## 12:29  Cheltenham Spa                          11A   On time
## 12:33  Didcot Parkway                          15A   On time
## 12:33  London Paddington                       7B    On time
## 12:33  Redhill                                 5     On time
## 12:39  Abbey Wood                              14    On time
## 12:40  Bristol Temple Meads                    11    On time
## 12:41  Didcot Parkway                          7B    On time
## 12:41  London Paddington                       9B    On time
## 12:42  Newbury                                 1     On time
## 12:43  London Waterloo                         6     On time
## 12:45  Swansea                                 10    On time
## 12:46  London Paddington                       9     On time
## 12:46  Newbury                                 11    On time
## 12:48  London Paddington                       12    On time
## 12:49  Basingstoke                             2     On time
## 12:51  Gatwick Airport                         4     On time
## 12:51  London Paddington                       8B    On time
## 12:54  London Paddington                       9     On time
## 12:57  London Paddington                       7B    On time
## 11:04  Heathrow Central Bus Stn                BUS   On time
## 11:34  Heathrow Central Bus Stn                BUS   On time
## 12:04  Heathrow Central Bus Stn                BUS   On time
## 12:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-12 10:03:55
## Time   To                                      Plat  Expected
## 10:57  Abbey Wood                              14    Delayed
## 10:58  Bristol Temple Meads                    8     11:03
## 11:01  Exeter St Davids                        7     11:04
## 11:04  London Paddington                       11    11:08
## 11:07  Basingstoke                             2     On time
## 11:09  London Waterloo                         6     On time
## 11:11  Ealing Broadway                         15A   On time
## 11:12  London Paddington                       10    11:15
## 11:12  Newbury                                 7     On time
## 11:13  Swansea                                 9     11:16
## 11:15  Didcot Parkway                          8B    On time
## 11:20  London Paddington                       10    On time
## 11:20  Redhill                                 5     On time
## 11:26  Didcot Parkway                          12    On time
## 11:27  Abbey Wood                              -     Cancelled
## 11:27  Bristol Temple Meads                    9     On time
## 11:29  London Paddington                       10    On time
## 11:29  Plymouth                                8B    On time
## 11:32  Basingstoke                             2     On time
## 11:34  London Paddington                       11A   11:34
## 11:37  Newbury                                 7B    On time
## 11:39  London Waterloo                         4     On time
## 11:40  Ealing Broadway                         15A   On time
## 11:41  London Paddington                       11    11:43
## 11:43  Cardiff Central                         9     On time
## 11:43  London Paddington                       10    On time
## 11:48  London Paddington                       11    11:51
## 11:49  Didcot Parkway                          9     On time
## 11:53  Cheltenham Spa                          7B    On time
## 11:53  Didcot Parkway                          13B   On time
## 11:57  Abbey Wood                              14    On time
## 11:57  Bristol Temple Meads                    9     On time
## 12:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 12:04  London Paddington                       11A   12:50
## 12:07  Basingstoke                             2     On time
## 12:09  Ealing Broadway                         15A   On time
## 12:09  London Waterloo                         6     On time
## 12:12  London Paddington                       10    On time
## 12:12  Newbury                                 3     On time
## 12:13  Swansea                                 9B    On time
## 12:16  Didcot Parkway                          8B    On time
## 12:16  London Paddington                       11    On time
## 12:20  Redhill                                 5     On time
## 12:23  Didcot Parkway                          12B   On time
## 12:24  London Paddington                       11    On time
## 12:26  London Paddington                       10    On time
## 12:27  Abbey Wood                              14    On time
## 12:27  Bristol Temple Meads                    9     On time
## 12:29  Penzance                                7     On time
## 12:32  Basingstoke                             2     On time
## 12:34  London Paddington                       11A   On time
## 12:37  Newbury                                 7B    On time
## 12:39  London Waterloo                         4     On time
## 12:40  Ealing Broadway                         15A   On time
## 12:43  Cardiff Central                         9B    On time
## 12:43  London Paddington                       11    On time
## 12:47  London Paddington                       10    On time
## 12:49  Didcot Parkway                          9     On time
## 12:52  Bournemouth                             7B    On time
## 12:53  Cheltenham Spa                          8B    On time
## 12:53  Didcot Parkway                          12    On time
## 12:54  London Paddington                       11    On time
## 12:57  Abbey Wood                              14    On time
## 12:58  Bristol Temple Meads                    9     On time
## 13:01  Exeter St Davids                        7B    On time
## 13:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
```
