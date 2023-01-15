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

## Example (Last rendered on 2023-01-15 18:03)

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
## Reading (RDG) Station Board on 2023-01-15 18:03:34
## Time   From                                    Plat  Expected
## 17:44  Port Talbot Parkway                     10    18:01
## 17:57  Hereford                                10A   18:05
## 18:02  London Waterloo                         4     On time
## 18:03  Abbey Wood                              14    18:05
## 18:06  Plymouth                                10    18:29
## 18:07  London Paddington                       9     18:17
## 18:08  Redhill                                 6     18:11
## 18:12  London Paddington                       9     18:14
## 18:13  Didcot Parkway                          15A   On time
## 18:13  London Paddington                       12B   On time
## 18:21  Newbury                                 1     On time
## 18:23  London Paddington                       9     18:27
## 18:23  Oxford                                  13A   On time
## 18:23  Swindon                                 10    On time
## 18:26  London Paddington                       7     On time
## 18:33  Abbey Wood                              14    On time
## 18:33  Gloucester                              11A   On time
## 18:34  London Waterloo                         4     On time
## 18:38  Gatwick Airport                         5     On time
## 18:39  Stockport                               15    18:42
## 18:40  Bath Spa                                -     Cancelled
## 18:44  Port Talbot Parkway                     10    18:52
## 18:45  London Paddington                       8     On time
## 18:53  London Paddington                       9     On time
## 18:56  Bournemouth                             8B    On time
## 18:56  Great Malvern                           10A   On time
## 18:58  Penzance                                11    On time
## 18:59  London Paddington                       7     On time
## 19:02  London Waterloo                         4     On time
## 19:03  Abbey Wood                              14    On time
## 19:07  London Paddington                       9     On time
## 19:10  Taunton                                 10    On time
## 19:11  Redhill                                 15    On time
## 19:12  London Paddington                       9     On time
## 19:13  Didcot Parkway                          13    On time
## 19:13  London Paddington                       12B   On time
## 19:19  Bedwyn                                  1     On time
## 19:23  London Paddington                       9     On time
## 19:25  Oxford                                  10    On time
## 19:26  London Paddington                       8     On time
## 19:32  London Waterloo                         6     On time
## 19:33  Abbey Wood                              14    On time
## 19:38  Gatwick Airport                         5     On time
## 19:39  London Paddington                       9     On time
## 19:39  Paignton                                11    On time
## 19:39  Stockport                               7     On time
## 19:45  London Paddington                       9     On time
## 19:48  Port Talbot Parkway                     10    On time
## 19:53  London Paddington                       9     On time
## 19:55  Hereford                                10    On time
## 19:57  Penzance                                11    On time
## 20:02  London Waterloo                         4     On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:20  Basingstoke                             BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 19:00  Winchester                              BUS   On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:20  Bramley (Hampshire)                     BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-01-15 18:03:38
## Time   To                                      Plat  Expected
## 17:46  London Paddington                       10    18:03
## 18:01  London Paddington                       10A   18:06
## 18:09  Port Talbot Parkway                     9     18:18
## 18:11  London Paddington                       10    18:30
## 18:14  Ealing Broadway                         15A   On time
## 18:14  Great Malvern                           9     18:15
## 18:15  Stockport                               7     On time
##        via Coventry & Stoke-on-Trent           
## 18:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:24  Abbey Wood                              14    On time
## 18:24  London Paddington                       10    On time
## 18:24  London Waterloo                         4     On time
## 18:25  Didcot Parkway                          12B   On time
## 18:25  Plymouth                                9     18:28
##        via Bristol                             
## 18:26  London Paddington                       13A   On time
## 18:28  Penzance                                7     On time
## 18:33  London Paddington                       11A   On time
## 18:41  London Paddington                       -     Cancelled
## 18:41  Redhill                                 6     On time
## 18:43  Newbury                                 1     On time
## 18:46  Bournemouth                             15    On time
## 18:46  London Paddington                       10    18:53
## 18:48  Oxford                                  8     On time
## 18:54  Abbey Wood                              14    On time
## 18:54  London Waterloo                         4     On time
## 18:55  Bristol Temple Meads                    9     On time
## 19:00  London Paddington                       11    On time
## 19:01  Plymouth                                7     On time
## 19:02  London Paddington                       10A   On time
## 19:09  Port Talbot Parkway                     9     On time
## 19:11  London Paddington                       10    On time
## 19:13  Ealing Broadway                         13    On time
## 19:14  Hereford                                9     On time
## 19:15  Stockport                               8B    On time
##        via Coventry & Stoke-on-Trent           
## 19:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:24  Abbey Wood                              14    On time
## 19:24  London Waterloo                         4     On time
## 19:25  Bath Spa                                9     On time
## 19:25  Didcot Parkway                          12B   On time
## 19:26  London Paddington                       10    On time
## 19:28  Plymouth                                8     On time
## 19:40  Swindon                                 9     On time
## 19:42  London Paddington                       11    On time
## 19:43  Bedwyn                                  1     On time
## 19:48  Oxford                                  9     On time
## 19:50  London Paddington                       10    On time
## 19:54  Abbey Wood                              14    On time
## 19:54  London Waterloo                         6     On time
## 19:55  Bristol Temple Meads                    9     On time
## 19:58  London Paddington                       11    On time
## 20:01  London Paddington                       10    On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:38  Basingstoke                             BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:38  Bramley (Hampshire)                     BUS   On time
## 19:52  Winchester                              BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
```
