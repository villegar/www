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

## Example (Last rendered on 2022-02-18 10:04)

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
## Reading (RDG) Station Board on 2022-02-18 10:04:02
## Time   From                                    Plat  Expected
## 09:04  Bristol Temple Meads                    10    10:09
## 09:37  Didcot Parkway                          15    09:51
## 09:40  Birmingham New Street                   7     10:16
## 09:45  Bristol Parkway                         10    10:23
## 09:53  Banbury                                 13    10:22
## 09:56  London Paddington                       9     10:09
## 10:00  London Paddington                       -     Cancelled
## 10:01  Plymouth                                -     Cancelled
## 10:05  Didcot Parkway                          13    10:12
## 10:06  Swansea                                 -     Cancelled
## 10:10  London Waterloo                         5     10:16
## 10:11  London Paddington                       9     10:18
## 10:12  Newbury                                 -     Cancelled
## 10:13  London Paddington                       14    10:16
## 10:14  Bristol Temple Meads                    10    10:32
## 10:17  London Paddington                       -     Cancelled
## 10:19  Basingstoke                             2     On time
## 10:23  Oxford                                  -     Cancelled
## 10:25  London Paddington                       -     Cancelled
## 10:28  Cheltenham Spa                          -     Cancelled
## 10:32  Bedwyn                                  -     On time
## 10:33  London Paddington                       -     Cancelled
## 10:35  Newbury                                 -     Cancelled
## 10:36  Didcot Parkway                          15    On time
## 10:39  Bristol Temple Meads                    -     Cancelled
## 10:40  London Waterloo                         6     On time
## 10:41  London Paddington                       -     Cancelled
## 10:43  London Paddington                       14    On time
## 10:45  Bristol Parkway                         11    On time
## 10:45  Redhill                                 4     On time
## 10:46  London Paddington                       -     Cancelled
## 10:49  Newbury                                 -     Cancelled
## 10:52  London Paddington                       -     Cancelled
## 10:53  Gatwick Airport                         -     Cancelled
## 10:54  Great Malvern                           -     Cancelled
## 10:55  Basingstoke                             2     On time
## 10:55  London Paddington                       8     On time
## 10:57  Penzance                                -     Cancelled
## 10:58  Didcot Parkway                          15    On time
## 10:59  London Paddington                       -     Cancelled
## 11:04  Exeter St Davids                        -     Cancelled
## 11:04  Exeter St Davids                        -     11:24
## 11:09  Bristol Temple Meads                    10    On time
## 11:10  London Waterloo                         4     On time
## 11:11  London Paddington                       9     On time
## 11:13  London Paddington                       14    On time
## 11:16  London Paddington                       -     Cancelled
## 11:18  Cardiff Central                         -     Cancelled
## 11:19  Basingstoke                             2     On time
## 11:22  Bedwyn                                  -     Cancelled
## 11:24  Oxford                                  -     Cancelled
## 11:25  London Paddington                       -     Cancelled
## 11:29  Cheltenham Spa                          -     Cancelled
## 11:29  London Paddington                       -     On time
## 11:32  Didcot Parkway                          15    On time
## 11:33  Redhill                                 5     On time
## 11:34  London Paddington                       -     Cancelled
## 11:35  Bedwyn                                  -     On time
## 11:36  Newbury                                 -     Cancelled
## 11:38  Plymouth                                -     Cancelled
## 11:40  Bristol Temple Meads                    -     Cancelled
## 11:40  London Waterloo                         6     On time
## 11:41  Birmingham New Street                   8     On time
## 11:41  London Paddington                       -     Cancelled
## 11:43  London Paddington                       14    On time
## 11:45  Bristol Parkway                         11    On time
## 11:46  London Paddington                       -     Cancelled
## 11:50  Basingstoke                             2     On time
## 11:51  Gatwick Airport                         -     Cancelled
## 11:51  London Paddington                       -     Cancelled
## 11:55  Great Malvern                           -     Cancelled
## 11:55  London Paddington                       9     On time
## 11:59  Didcot Parkway                          15    On time
## 10:21  Heathrow Central Bus Stn                BUS   On time
## 11:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-18 10:04:07
## Time   To                                      Plat  Expected
## 09:06  London Paddington                       10    10:10
## 09:47  London Paddington                       10    10:24
## 09:58  Bristol Temple Meads                    9     10:14
## 10:02  Paignton                                -     Cancelled
## 10:04  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 10:04  London Paddington                       -     Cancelled
## 10:07  Basingstoke                             2     On time
## 10:08  London Paddington                       -     Cancelled
## 10:12  Bedwyn                                  1     On time
## 10:12  London Waterloo                         6     On time
## 10:12  Newbury                                 -     Cancelled
## 10:13  Bristol Parkway                         9     10:19
## 10:13  London Paddington                       -     Cancelled
## 10:17  London Paddington                       10    10:33
## 10:19  Hereford                                -     Cancelled
## 10:20  Redhill                                 5     On time
## 10:22  Ealing Broadway                         14    On time
## 10:23  Didcot Parkway                          15    On time
## 10:26  London Paddington                       -     Cancelled
## 10:27  Bristol Temple Meads                    -     Cancelled
## 10:29  Exeter St Davids                        11    On time
## 10:32  Basingstoke                             2     On time
## 10:34  London Paddington                       -     Cancelled
## 10:38  Bedwyn                                  -     Cancelled
## 10:42  London Paddington                       -     Cancelled
## 10:42  London Waterloo                         5     On time
## 10:43  Cardiff Central                         -     Cancelled
## 10:48  London Paddington                       11    On time
## 10:48  Oxford                                  -     Cancelled
## 10:52  Ealing Broadway                         14    On time
## 10:53  Cheltenham Spa                          -     Cancelled
## 10:53  Didcot Parkway                          13    On time
## 10:57  London Paddington                       -     Cancelled
## 10:58  Bristol Temple Meads                    8     On time
## 11:01  Exeter St Davids                        -     Cancelled
## 11:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 11:04  London Paddington                       -     Cancelled
## 11:04  London Paddington                       -     Cancelled
## 11:04  London Paddington                       -     11:24
## 11:07  Basingstoke                             2     On time
## 11:12  Bedwyn                                  -     On time
## 11:12  Bedwyn                                  -     On time
## 11:12  London Paddington                       10    On time
## 11:12  London Waterloo                         6     On time
## 11:12  Newbury                                 -     Cancelled
## 11:13  Bristol Parkway                         9     On time
## 11:15  Birmingham New Street                   8     On time
##        via Coventry                            
## 11:19  Worcester Shrub Hill                    -     Cancelled
## 11:20  London Paddington                       -     Cancelled
## 11:20  Redhill                                 5     On time
## 11:22  Ealing Broadway                         14    On time
## 11:24  London Paddington                       -     Cancelled
## 11:26  Didcot Parkway                          12    On time
## 11:26  London Paddington                       -     Cancelled
## 11:27  Bristol Temple Meads                    -     Cancelled
## 11:29  Exeter St Davids                        -     On time
## 11:32  Basingstoke                             2     On time
## 11:34  London Paddington                       -     Cancelled
## 11:37  Newbury                                 -     Cancelled
## 11:40  London Paddington                       -     Cancelled
## 11:42  London Paddington                       -     Cancelled
## 11:42  London Waterloo                         4     On time
## 11:43  Cardiff Central                         -     Cancelled
## 11:48  Bedwyn                                  -     Cancelled
## 11:48  London Paddington                       11    On time
## 11:49  Oxford                                  -     Cancelled
## 11:52  Ealing Broadway                         14    On time
## 11:53  Cheltenham Spa                          -     Cancelled
## 11:53  Didcot Parkway                          12    On time
## 11:57  Bristol Temple Meads                    9     On time
## 11:58  London Paddington                       -     Cancelled
## 12:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 11:00  Heathrow Central Bus Stn                BUS   On time
## 12:00  Heathrow Central Bus Stn                BUS   On time
```
