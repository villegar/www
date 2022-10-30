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

## Example (Last rendered on 2022-10-30 18:04)

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
## Reading (RDG) Station Board on 2022-10-30 18:04:57
## Time   From                                    Plat  Expected
## 17:44  Swansea                                 11    18:14
## 17:56  Hereford                                10A   18:06
## 18:00  London Paddington                       8B    18:17
## 18:03  London Paddington                       14    18:06
## 18:06  Plymouth                                10    18:09
## 18:07  London Paddington                       8     18:19
## 18:08  London Waterloo                         4     On time
## 18:08  Redhill                                 6     18:13
## 18:12  London Paddington                       9B    On time
## 18:13  Didcot Parkway                          15A   On time
## 18:13  London Paddington                       12B   On time
## 18:21  Newbury                                 1     On time
## 18:25  Oxford                                  10A   On time
## 18:28  London Paddington                       9     18:42
## 18:31  London Paddington                       7     On time
## 18:33  Basingstoke                             2     On time
## 18:33  Cheltenham Spa                          11A   On time
## 18:33  London Paddington                       14    18:36
## 18:35  Virginia Water                          4     On time
## 18:38  Gatwick Airport                         5     On time
## 18:39  Manchester Piccadilly                   12    On time
## 18:40  Bristol Temple Meads                    9     On time
## 18:44  Swansea                                 10    Delayed
## 18:48  London Paddington                       8B    On time
## 18:56  Great Malvern                           10A   On time
## 18:57  London Paddington                       9     On time
## 18:58  Penzance                                11    On time
## 19:00  London Paddington                       7     On time
## 19:03  London Paddington                       14    On time
## 19:05  Eastleigh                               8     On time
## 19:07  London Paddington                       9     On time
## 19:08  London Waterloo                         4     On time
## 19:08  Redhill                                 15    On time
## 19:09  Taunton                                 10    On time
## 19:13  Didcot Parkway                          13A   On time
## 19:13  London Paddington                       12B   On time
## 19:17  London Paddington                       9     On time
## 19:19  Bedwyn                                  1     On time
## 19:25  Oxford                                  10A   On time
## 19:28  London Paddington                       9     On time
## 19:31  London Paddington                       8     On time
## 19:33  London Paddington                       14    On time
## 19:34  Basingstoke                             2     On time
## 19:35  Virginia Water                          6     On time
## 19:38  Gatwick Airport                         5     On time
## 19:39  Manchester Piccadilly                   7B    On time
## 19:40  Paignton                                11    On time
## 19:48  London Paddington                       9B    On time
## 19:48  Swansea                                 10    On time
## 19:56  Hereford                                10    On time
## 19:57  London Paddington                       9     On time
## 19:57  Penzance                                11    On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-30 18:05:03
## Time   To                                      Plat  Expected
## 17:50  London Paddington                       11    18:15
## 17:57  London Paddington                       10A   18:07
## 18:02  Swindon                                 8B    18:19
## 18:10  Swansea                                 8     18:24
## 18:13  London Paddington                       10    On time
## 18:14  Ealing Broadway                         15A   On time
## 18:14  Great Malvern                           9B    On time
## 18:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 18:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:21  Virginia Water                          4     On time
## 18:24  Ealing Broadway                         14    On time
## 18:25  Didcot Parkway                          12B   On time
## 18:27  London Paddington                       10A   On time
## 18:30  Plymouth                                9     18:43
##        via Bristol                             
## 18:33  Penzance                                7     On time
## 18:38  Basingstoke                             2     On time
## 18:41  Redhill                                 6     On time
## 18:43  London Paddington                       11A   On time
## 18:43  Newbury                                 1     On time
## 18:47  London Paddington                       9     On time
## 18:49  Oxford                                  8B    On time
## 18:50  London Paddington                       10    Delayed
## 18:51  London Waterloo                         4     On time
## 18:54  Ealing Broadway                         14    On time
## 18:57  London Paddington                       10A   On time
## 18:59  Weston-super-Mare                       9     On time
## 19:02  London Paddington                       11    On time
## 19:02  Plymouth                                7     On time
## 19:10  Swansea                                 9     On time
## 19:13  London Paddington                       10    On time
## 19:14  Ealing Broadway                         13A   On time
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:18  Hereford                                9     On time
## 19:21  Virginia Water                          4     On time
## 19:24  Ealing Broadway                         14    On time
## 19:25  Didcot Parkway                          12B   On time
## 19:27  London Paddington                       10A   On time
## 19:30  Bristol Temple Meads                    9     On time
## 19:33  Plymouth                                8     On time
## 19:38  Basingstoke                             2     On time
## 19:43  Bedwyn                                  1     On time
## 19:46  London Paddington                       11    On time
## 19:49  Oxford                                  9B    On time
## 19:50  London Paddington                       10    On time
## 19:51  London Waterloo                         6     On time
## 19:52  Eastleigh                               7B    On time
## 19:54  Ealing Broadway                         14    On time
## 19:57  London Paddington                       10    On time
## 19:59  Bristol Temple Meads                    9     On time
## 20:02  London Paddington                       11    On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
```
