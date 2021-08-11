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

## Example (Last rendered on 2021-08-11 12:03)

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
## Reading (RDG) Station Board on 2021-08-11 12:03:19
## Time   From                                    Plat  Expected
## 12:33  Redhill                                 5     Delayed
## 12:59  Penzance                                11    13:07
## 13:00  London Paddington                       7     13:04
## 13:05  Bournemouth                             8     On time
## 13:09  Bristol Parkway                         10    On time
## 13:11  London Paddington                       9     On time
## 13:11  London Waterloo                         4     On time
## 13:13  London Paddington                       14    On time
## 13:14  London Paddington                       -     On time
## 13:16  London Paddington                       9     On time
## 13:18  Basingstoke                             -     On time
## 13:24  Newbury                                 -     On time
## 13:24  Oxford                                  -     On time
## 13:25  London Paddington                       -     On time
## 13:27  London Paddington                       -     13:41
## 13:31  Didcot Parkway                          -     On time
## 13:31  London Paddington                       -     On time
## 13:33  Redhill                                 -     On time
## 13:36  Newbury                                 -     On time
## 13:39  Bath Spa                                -     13:42
## 13:40  Manchester Piccadilly                   -     On time
## 13:42  London Waterloo                         -     On time
## 13:42  Paignton                                -     On time
## 13:43  London Paddington                       -     On time
## 13:44  Swansea                                 -     On time
## 13:46  London Paddington                       -     On time
## 13:51  Gatwick Airport                         -     On time
## 13:51  London Paddington                       -     On time
## 13:54  Great Malvern                           -     On time
## 13:55  Basingstoke                             -     On time
## 13:56  London Paddington                       -     On time
## 14:02  Penzance                                -     On time
## 14:09  Bristol Parkway                         -     On time
## 14:11  London Paddington                       -     On time
## 14:11  London Waterloo                         -     On time
## 14:13  London Paddington                       -     On time
## 14:14  London Paddington                       -     On time
## 14:16  London Paddington                       -     On time
## 14:19  Basingstoke                             -     On time
## 14:22  Newbury                                 -     On time
## 14:24  Oxford                                  -     On time
## 14:25  London Paddington                       -     On time
## 14:27  London Paddington                       -     On time
## 14:29  Cheltenham Spa                          -     On time
## 14:31  Didcot Parkway                          -     On time
## 14:32  London Paddington                       -     On time
## 14:33  Redhill                                 -     On time
## 14:40  Bath Spa                                -     On time
## 14:40  Manchester Piccadilly                   -     On time
## 14:40  Newbury                                 -     On time
## 14:41  London Waterloo                         -     On time
## 14:43  London Paddington                       -     On time
## 14:43  Newbury                                 -     On time
## 14:45  Swansea                                 -     On time
## 14:46  London Paddington                       -     On time
## 14:49  Basingstoke                             -     On time
## 14:51  Gatwick Airport                         -     On time
## 14:51  London Paddington                       -     On time
## 14:55  London Paddington                       -     On time
## 14:55  Worcester Shrub Hill                    -     On time
## 15:00  London Paddington                       -     On time
## 13:21  Heathrow Central Bus Stn                -     On time
## 14:21  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-08-11 12:03:23
## Time   To                                      Plat  Expected
## 13:01  Exeter St Davids                        7     13:05
## 13:04  London Paddington                       11    13:08
## 13:07  Basingstoke                             3     On time
## 13:12  London Waterloo                         6     On time
## 13:12  Newbury                                 1     On time
## 13:13  Swansea                                 9     On time
## 13:14  London Paddington                       10    On time
## 13:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 13:18  Worcester Foregate Street               9     On time
## 13:20  Redhill                                 -     On time
## 13:22  Ealing Broadway                         -     On time
## 13:23  Didcot Parkway                          -     On time
## 13:26  London Paddington                       -     On time
## 13:27  Bath Spa                                -     On time
## 13:29  Penzance                                -     13:42
## 13:31  London Paddington                       -     On time
## 13:32  Basingstoke                             -     On time
## 13:37  Newbury                                 -     On time
## 13:38  Ealing Broadway                         -     On time
## 13:41  London Paddington                       -     13:43
## 13:42  London Paddington                       -     On time
## 13:42  London Waterloo                         -     On time
## 13:48  London Paddington                       -     On time
## 13:48  Oxford                                  -     On time
## 13:50  Newbury                                 -     On time
## 13:52  Ealing Broadway                         -     On time
## 13:53  Cheltenham Spa                          -     On time
## 13:57  London Paddington                       -     On time
## 13:58  Bristol Parkway                         -     On time
## 14:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 14:04  London Paddington                       -     On time
## 14:07  Basingstoke                             -     On time
## 14:11  London Paddington                       -     On time
## 14:12  London Waterloo                         -     On time
## 14:12  Newbury                                 -     On time
## 14:13  Swansea                                 -     On time
## 14:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 14:18  Great Malvern                           -     On time
## 14:20  Redhill                                 -     On time
## 14:22  Ealing Broadway                         -     On time
## 14:24  London Paddington                       -     On time
## 14:25  Didcot Parkway                          -     On time
## 14:27  Bath Spa                                -     On time
## 14:27  London Paddington                       -     On time
## 14:29  Penzance                                -     On time
## 14:32  Basingstoke                             -     On time
## 14:35  London Paddington                       -     On time
## 14:37  Newbury                                 -     On time
## 14:42  London Waterloo                         -     On time
## 14:43  London Paddington                       -     On time
## 14:45  Ealing Broadway                         -     On time
## 14:48  London Paddington                       -     On time
## 14:49  Bournemouth                             -     On time
## 14:49  Oxford                                  -     On time
## 14:52  Ealing Broadway                         -     On time
## 14:53  Cheltenham Spa                          -     On time
## 14:57  Bristol Parkway                         -     On time
## 14:57  London Paddington                       -     On time
## 15:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 15:02  Plymouth                                -     On time
## 14:00  Heathrow Central Bus Stn                -     On time
## 15:00  Heathrow Central Bus Stn                -     On time
```
