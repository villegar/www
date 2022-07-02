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

## Example (Last rendered on 2022-07-02 08:03)

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
## Reading (RDG) Station Board on 2022-07-02 08:03:43
## Time   From                                    Plat  Expected
## 08:47  Bristol Temple Meads                    11    09:05
## 08:54  Hereford                                10    09:00
## 09:01  Didcot Parkway                          15    On time
## 09:03  London Paddington                       14    On time
## 09:03  Plymouth                                11    On time
## 09:07  Bournemouth                             13B   On time
## 09:10  Taunton                                 10    On time
## 09:11  Ascot                                   4     On time
## 09:14  London Paddington                       12    On time
## 09:17  London Paddington                       9B    On time
## 09:25  London Paddington                       9     On time
## 09:25  Newbury                                 11    On time
## 09:25  Oxford                                  10A   On time
## 09:31  Didcot Parkway                          15    On time
## 09:33  Cheltenham Spa                          10A   09:35
## 09:33  London Paddington                       7     On time
## 09:33  London Paddington                       14    On time
## 09:33  Redhill                                 5     On time
## 09:38  Swansea                                 10    On time
## 09:40  Nottingham                              13    On time
## 09:41  Ascot                                   6     On time
## 09:41  London Paddington                       9     On time
## 09:41  Newbury                                 1     On time
## 09:43  London Paddington                       12    On time
## 09:43  Plymouth                                11    09:49
## 09:46  Bristol Temple Meads                    10    On time
## 09:47  London Paddington                       9B    On time
## 09:51  Gatwick Airport                         4     On time
## 09:51  London Paddington                       8B    On time
## 09:54  Hereford                                10    On time
## 09:55  London Paddington                       9     On time
## 09:59  Basingstoke                             2     On time
## 10:01  Didcot Parkway                          15    On time
## 10:02  Plymouth                                11    On time
## 10:03  London Paddington                       14    On time
## 10:10  Exeter St Davids                        10    On time
## 10:11  Ascot                                   5     On time
## 10:13  London Paddington                       12    On time
## 10:14  Worcester Foregate Street               11    On time
## 10:17  Bristol Parkway                         10    On time
## 10:17  London Paddington                       9     On time
## 10:25  London Paddington                       9     On time
## 10:25  Oxford                                  10    On time
## 10:31  Didcot Parkway                          15    On time
## 10:31  Newbury                                 11    On time
## 10:32  Cheltenham Spa                          10A   On time
## 10:33  London Paddington                       14    On time
## 10:33  Redhill                                 4     On time
## 10:34  London Paddington                       7     On time
## 10:37  Swansea                                 11    On time
## 10:41  Ascot                                   6     On time
## 10:41  London Paddington                       8     On time
## 10:41  Manchester Piccadilly                   7     On time
## 10:42  Newbury                                 1     On time
## 10:43  London Paddington                       12    On time
## 10:46  Bristol Temple Meads                    10    On time
## 10:47  London Paddington                       9B    On time
## 10:51  Gatwick Airport                         5     On time
## 10:51  London Paddington                       8B    On time
## 10:54  Great Malvern                           10A   On time
## 10:55  London Paddington                       9     On time
## 10:59  Basingstoke                             2     On time
## 09:45  Heathrow Central Bus Stn                BUS   On time
## 10:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-07-02 08:03:47
## Time   To                                      Plat  Expected
## 08:49  London Paddington                       11    09:09
## 08:57  London Paddington                       10    09:02
## 09:05  London Paddington                       11    On time
## 09:06  Basingstoke                             2     On time
## 09:09  Newbury                                 1     On time
## 09:12  Ascot                                   6     On time
## 09:12  London Paddington                       10    On time
## 09:15  Ealing Broadway                         15    On time
## 09:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 09:20  Great Malvern                           9B    On time
## 09:20  Redhill                                 5     On time
## 09:24  Didcot Parkway                          12    On time
## 09:24  Ealing Broadway                         14    On time
## 09:27  Bristol Temple Meads                    9     On time
## 09:27  London Paddington                       10A   On time
## 09:30  Penzance                                7     On time
## 09:32  London Paddington                       11    On time
## 09:35  London Paddington                       10A   09:35
## 09:35  Newbury                                 7     On time
## 09:40  London Paddington                       10    On time
## 09:42  Ascot                                   4     On time
## 09:43  Swansea                                 9     On time
## 09:45  Ealing Broadway                         15    On time
## 09:45  London Paddington                       11    09:50
## 09:48  London Paddington                       10    On time
## 09:49  Oxford                                  9B    On time
## 09:53  Cheltenham Spa                          8B    On time
## 09:53  Didcot Parkway                          12    On time
## 09:54  Ealing Broadway                         14    On time
## 09:56  London Paddington                       10    On time
## 09:58  Bristol Temple Meads                    9     On time
## 10:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:05  Basingstoke                             2     On time
## 10:05  London Paddington                       11    On time
## 10:12  Ascot                                   6     On time
## 10:12  London Paddington                       10    On time
## 10:12  Newbury                                 1     On time
## 10:15  Ealing Broadway                         15    On time
## 10:15  London Paddington                       11    On time
## 10:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 10:18  London Paddington                       10    On time
## 10:19  Hereford                                9     On time
## 10:20  Redhill                                 4     On time
## 10:23  Didcot Parkway                          12    On time
## 10:24  Ealing Broadway                         14    On time
## 10:27  Bristol Temple Meads                    9     On time
## 10:27  London Paddington                       10    On time
## 10:30  Penzance                                7     On time
## 10:31  London Paddington                       11    On time
## 10:35  London Paddington                       10A   On time
## 10:35  Newbury                                 7     On time
## 10:39  London Paddington                       11    On time
## 10:42  Ascot                                   5     On time
## 10:43  Swansea                                 8     On time
## 10:45  Ealing Broadway                         15    On time
## 10:48  London Paddington                       10    On time
## 10:49  Oxford                                  9B    On time
## 10:51  Bournemouth                             7     On time
## 10:52  Didcot Parkway                          12    On time
## 10:53  Cheltenham Spa                          8B    On time
## 10:54  Ealing Broadway                         14    On time
## 10:56  London Paddington                       10A   On time
## 10:57  Weston-super-Mare                       9     On time
## 11:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 11:01  Paignton                                7     On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
## 11:00  Heathrow Central Bus Stn                BUS   On time
```
