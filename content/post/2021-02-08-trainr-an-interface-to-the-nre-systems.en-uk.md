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

## Example (Last rendered on 2022-10-23 14:08)

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
## Reading (RDG) Station Board on 2022-10-23 14:08:21
## Time   From                                    Plat  Expected
## 13:39  Manchester Piccadilly                   -     15:09
## 14:57  Penzance                                11    15:16
## 15:05  Eastleigh                               -     15:08
## 15:09  Weston-super-Mare                       11    15:12
## 15:10  London Paddington                       14    15:12
## 15:13  Didcot Parkway                          15    On time
## 15:13  London Paddington                       12    15:15
## 15:18  Bedwyn                                  3     15:24
## 15:33  Basingstoke                             2     On time
## 15:35  Ascot                                   4     On time
## 15:38  Gatwick Airport                         5     On time
## 15:39  London Paddington                       14    On time
## 15:39  Manchester Piccadilly                   7     15:42
## 15:40  Bristol Temple Meads                    10    15:52
## 15:41  Exeter St Davids                        11    15:45
## 15:46  Swansea                                 11    On time
## 15:47  Salisbury                               1     On time
## 15:56  Ledbury                                 10    On time
## 15:58  Exeter St Davids                        11    On time
## 16:05  Ascot                                   4     On time
## 16:08  London Paddington                       14    On time
## 16:08  Redhill                                 6     On time
## 16:09  Bristol Temple Meads                    10    On time
## 16:12  Newbury                                 3     On time
## 16:13  Didcot Parkway                          15    On time
## 16:13  London Paddington                       12    On time
## 16:32  Cheltenham Spa                          11    On time
## 16:33  Basingstoke                             2     On time
## 16:35  Ascot                                   4     On time
## 16:38  Gatwick Airport                         5     On time
## 16:39  London Paddington                       14    On time
## 16:39  Manchester Piccadilly                   13    On time
## 16:44  Swansea                                 10    On time
## 16:47  Salisbury                               1     On time
## 16:56  Great Malvern                           10    On time
## 16:58  Penzance                                11    On time
## 17:05  Ascot                                   4     On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-23 14:08:25
## Time   To                                      Plat  Expected
## 13:52  Eastleigh                               -     15:10
## 14:28  Penzance                                12    15:08
## 15:00  London Paddington                       11    15:17
## 15:01  Exeter St Davids                        -     15:23
## 15:10  Swansea                                 -     15:27
## 15:12  Salisbury                               1     On time
## 15:14  Ealing Broadway                         15    On time
## 15:14  Great Malvern                           -     On time
## 15:15  London Paddington                       11    On time
## 15:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 15:18  Gatwick Airport                         15A   On time
##        via Guildford                           
## 15:21  Ascot                                   4     On time
## 15:25  Bristol Temple Meads                    -     On time
## 15:25  Didcot Parkway                          12    On time
## 15:28  Plymouth                                7     15:30
## 15:31  Ealing Broadway                         14    On time
## 15:38  Basingstoke                             2     On time
## 15:41  Redhill                                 6     On time
## 15:43  Bedwyn                                  3     On time
## 15:43  London Paddington                       11    15:46
## 15:45  London Paddington                       10    15:53
## 15:48  London Paddington                       11    On time
## 15:51  Ascot                                   4     On time
## 15:52  Eastleigh                               7     On time
## 15:55  Taunton                                 9     16:13
## 16:00  London Paddington                       11    On time
## 16:01  Ealing Broadway                         14    On time
## 16:02  London Paddington                       10    On time
## 16:10  Swansea                                 8     On time
## 16:12  Salisbury                               1     On time
## 16:14  Ealing Broadway                         15    On time
## 16:14  Ledbury                                 9     On time
## 16:15  London Paddington                       10    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:21  Ascot                                   4     On time
## 16:24  Bristol Temple Meads                    9     On time
## 16:25  Didcot Parkway                          12    On time
## 16:28  Penzance                                7     On time
## 16:31  Ealing Broadway                         14    On time
## 16:38  Basingstoke                             2     On time
## 16:41  Redhill                                 6     On time
## 16:42  London Paddington                       11    On time
## 16:43  Newbury                                 3     On time
## 16:46  London Paddington                       10    On time
## 16:51  Ascot                                   4     On time
## 16:55  Plymouth                                9     On time
##        via Bristol                             
## 17:00  London Paddington                       11    On time
## 17:01  Ealing Broadway                         14    On time
## 17:02  London Paddington                       10    On time
## 17:02  Plymouth                                7     On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
```
