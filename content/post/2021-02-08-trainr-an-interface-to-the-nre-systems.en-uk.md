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

## Example (Last rendered on 2023-04-17 18:04)

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
## Reading (RDG) Station Board on 2023-04-17 18:04:41
## Time   From                                    Plat  Expected
## 18:53  London Paddington                       12B   19:01
## 18:57  Abbey Wood                              13    19:03
## 19:04  Basingstoke                             2     On time
## 19:05  Didcot Parkway                          15A   19:09
## 19:09  Gatwick Airport                         4     19:04
## 19:09  London Paddington                       13    On time
## 19:10  Weston-super-Mare                       10    19:14
## 19:11  London Paddington                       9     On time
## 19:14  Abbey Wood                              14    On time
## 19:15  Newbury                                 1     On time
## 19:16  Cardiff Central                         -     Cancelled
## 19:17  London Waterloo                         6     On time
## 19:25  Didcot Parkway                          10A   On time
## 19:26  London Paddington                       8     On time
## 19:28  Didcot Parkway                          15A   On time
## 19:28  London Paddington                       7     On time
## 19:31  Cheltenham Spa                          11A   On time
## 19:33  Redhill                                 4     On time
## 19:34  London Paddington                       12    On time
## 19:35  Basingstoke                             2     On time
## 19:35  London Paddington                       8B    On time
## 19:35  Worcester Foregate Street               10A   On time
## 19:40  Abbey Wood                              13    On time
## 19:41  Bristol Temple Meads                    11    On time
## 19:41  Didcot Parkway                          7B    On time
## 19:41  London Paddington                       9B    On time
## 19:44  Abbey Wood                              14    On time
## 19:44  London Waterloo                         5     On time
## 19:46  Swansea                                 10    On time
## 19:53  London Paddington                       8B    On time
## 19:54  Plymouth                                11    On time
## 19:55  London Paddington                       12B   On time
## 19:56  London Paddington                       9     On time
## 19:58  Didcot Parkway                          15A   On time
## 20:00  Basingstoke                             1     On time
## 20:04  Gatwick Airport                         4     On time
## 20:04  Newbury                                 2     On time
## 20:07  Bournemouth                             8B    On time
## 20:10  Weston-super-Mare                       10    On time
## 20:11  London Paddington                       9     On time
## 20:13  Abbey Wood                              14    On time
## 20:14  London Waterloo                         6     On time
## 20:17  London Paddington                       12B   On time
## 20:24  London Paddington                       9     On time
## 20:26  London Paddington                       8     On time
## 20:32  Cheltenham Spa                          10A   On time
## 20:34  Basingstoke                             2     On time
## 20:34  Didcot Parkway                          13A   On time
## 20:35  Redhill                                 14A   On time
## 20:36  London Paddington                       8     On time
## 20:42  Didcot Parkway                          8     On time
## 20:42  London Waterloo                         4     On time
## 20:43  Abbey Wood                              14    On time
## 20:44  Swansea                                 10    20:46
## 20:45  Newbury                                 1     On time
## 20:46  London Paddington                       12    On time
## 20:51  London Paddington                       7B    On time
## 20:53  Gatwick Airport                         6     On time
## 20:55  London Paddington                       9     On time
## 21:00  Penzance                                10    On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-17 18:04:48
## Time   To                                      Plat  Expected
## 18:57  Didcot Parkway                          12B   19:04
## 19:05  Basingstoke                             3     On time
## 19:09  London Waterloo                         5     On time
## 19:10  Newbury                                 14B   On time
## 19:12  Ealing Broadway                         15A   On time
## 19:13  London Paddington                       10    19:15
## 19:13  Swansea                                 9     On time
## 19:15  Didcot Parkway                          8B    On time
## 19:18  London Paddington                       -     Cancelled
## 19:20  Redhill                                 4     19:30
## 19:25  Basingstoke                             2     On time
## 19:26  London Paddington                       10A   On time
## 19:27  Abbey Wood                              14    On time
## 19:27  Bristol Temple Meads                    8     On time
## 19:29  Plymouth                                7     On time
## 19:34  Didcot Parkway                          12    On time
## 19:34  London Paddington                       11A   On time
## 19:37  Bedwyn                                  8B    On time
## 19:37  Ealing Broadway                         15A   On time
## 19:39  London Waterloo                         6     On time
## 19:40  London Paddington                       10A   On time
## 19:42  Newbury                                 1     On time
## 19:43  London Paddington                       11    On time
## 19:43  Swansea                                 9B    On time
## 19:49  London Paddington                       10    On time
## 19:50  Bournemouth                             7B    On time
## 19:55  Didcot Parkway                          8B    On time
## 19:55  London Paddington                       11    On time
## 19:57  Abbey Wood                              13    On time
## 19:57  Basingstoke                             2     On time
## 19:57  Didcot Parkway                          12B   On time
## 19:58  Weston-super-Mare                       9     On time
## 20:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 20:09  London Waterloo                         5     On time
## 20:10  Newbury                                 2     On time
## 20:12  London Paddington                       10    On time
## 20:13  Ealing Broadway                         15A   On time
## 20:13  Swansea                                 9     On time
## 20:15  Didcot Parkway                          8B    On time
## 20:20  Shalford                                4     On time
## 20:21  Basingstoke                             1     On time
## 20:23  Didcot Parkway                          12B   On time
## 20:27  Abbey Wood                              14    On time
## 20:27  Bristol Temple Meads                    9     On time
## 20:29  Plymouth                                8     On time
## 20:36  London Paddington                       10A   On time
## 20:36  Newbury                                 8     On time
## 20:39  London Waterloo                         6     On time
## 20:45  Ealing Broadway                         13A   On time
## 20:47  London Paddington                       10    On time
## 20:51  Didcot Parkway                          12    On time
## 20:52  Basingstoke                             2     On time
## 20:53  Cheltenham Spa                          7B    On time
## 20:57  Abbey Wood                              14    On time
## 20:57  Weston-super-Mare                       9     On time
## 21:01  Gatwick Airport                         6     On time
##        via Guildford                           
## 21:03  London Paddington                       10    On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
```
