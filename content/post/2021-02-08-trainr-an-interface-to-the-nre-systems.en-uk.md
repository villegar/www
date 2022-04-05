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

## Example (Last rendered on 2022-04-05 10:03)

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
## Reading (RDG) Station Board on 2022-04-05 10:03:44
## Time   From                                    Plat  Expected
## 10:45  Redhill                                 4     Delayed
## 10:52  London Paddington                       9     10:57
## 10:57  Penzance                                11    11:00
## 10:58  Didcot Parkway                          15A   On time
## 10:59  London Paddington                       7     11:01
## 11:06  Bournemouth                             8B    On time
## 11:09  Bristol Temple Meads                    10    On time
## 11:11  London Paddington                       9     On time
## 11:11  London Waterloo                         4     On time
## 11:13  London Paddington                       14    On time
## 11:16  London Paddington                       12B   On time
## 11:16  London Paddington                       9     On time
## 11:18  Cardiff Central                         11A   11:21
## 11:19  Basingstoke                             2     On time
## 11:22  Bedwyn                                  11A   On time
## 11:24  Oxford                                  10    On time
## 11:25  London Paddington                       9     On time
## 11:27  London Paddington                       8     On time
## 11:29  Cheltenham Spa                          11    11:31
## 11:32  Didcot Parkway                          -     On time
## 11:33  Redhill                                 5     On time
## 11:34  London Paddington                       -     On time
## 11:36  Newbury                                 -     On time
## 11:38  Plymouth                                -     On time
## 11:40  Bristol Temple Meads                    -     11:43
## 11:41  London Paddington                       9     On time
## 11:41  London Waterloo                         6     On time
## 11:41  Manchester Piccadilly                   -     On time
## 11:43  London Paddington                       -     On time
## 11:44  London Paddington                       -     On time
## 11:45  Swansea                                 11    On time
## 11:46  London Paddington                       -     On time
## 11:50  Basingstoke                             2     On time
## 11:51  Gatwick Airport                         -     On time
## 11:51  London Paddington                       -     On time
## 11:55  Great Malvern                           -     On time
## 11:55  London Paddington                       -     On time
## 11:59  Didcot Parkway                          -     On time
## 12:01  Penzance                                -     On time
## 12:09  Bristol Temple Meads                    -     On time
## 12:11  London Paddington                       -     On time
## 12:11  London Waterloo                         -     On time
## 12:13  London Paddington                       -     On time
## 12:14  London Paddington                       -     On time
## 12:16  London Paddington                       -     On time
## 12:18  Basingstoke                             -     On time
## 12:22  Bedwyn                                  -     On time
## 12:24  Oxford                                  -     On time
## 12:25  London Paddington                       -     On time
## 12:27  London Paddington                       -     On time
## 12:29  Cheltenham Spa                          -     On time
## 12:33  Didcot Parkway                          -     On time
## 12:33  London Paddington                       -     On time
## 12:33  Redhill                                 -     On time
## 12:40  Bristol Temple Meads                    -     On time
## 12:41  London Paddington                       -     On time
## 12:41  London Waterloo                         -     On time
## 12:42  Manchester Piccadilly                   -     On time
## 12:42  Newbury                                 -     On time
## 12:43  London Paddington                       -     On time
## 12:44  London Paddington                       -     On time
## 12:45  Swansea                                 -     On time
## 12:46  London Paddington                       -     On time
## 12:49  Basingstoke                             -     On time
## 12:51  Gatwick Airport                         -     On time
## 12:51  London Paddington                       -     On time
## 12:54  Great Malvern                           -     On time
## 12:54  London Paddington                       -     On time
## 12:57  London Paddington                       -     On time
## 11:26  Heathrow Central Bus Stn                BUS   On time
## 12:01  Heathrow Central Bus Stn                -     On time
## 12:36  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-04-05 10:03:50
## Time   To                                      Plat  Expected
## 10:53  Cheltenham Spa                          9     11:02
## 11:01  Exeter St Davids                        7     11:03
## 11:01  Gatwick Airport                         4     Delayed
##        via Guildford                           
## 11:04  London Paddington                       11    On time
## 11:07  Basingstoke                             2     On time
## 11:12  London Paddington                       10    On time
## 11:12  London Waterloo                         6     On time
## 11:12  Newbury                                 1     On time
## 11:13  Swansea                                 9     On time
## 11:15  Ealing Broadway                         15A   On time
## 11:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 11:19  Worcester Shrub Hill                    9     On time
## 11:20  London Paddington                       11A   11:22
## 11:20  Redhill                                 5     On time
## 11:21  Ealing Broadway                         14    On time
## 11:24  London Paddington                       11A   On time
## 11:26  Didcot Parkway                          12B   On time
## 11:26  London Paddington                       10    On time
## 11:27  Bristol Temple Meads                    9     On time
## 11:29  Plymouth                                8     On time
## 11:32  Basingstoke                             2     On time
## 11:34  London Paddington                       11    On time
## 11:36  Ealing Broadway                         -     On time
## 11:37  Newbury                                 -     On time
## 11:40  London Paddington                       -     On time
## 11:42  London Paddington                       -     11:44
## 11:42  London Waterloo                         4     On time
## 11:43  Cardiff Central                         9     On time
## 11:48  Bedwyn                                  3     On time
## 11:48  London Paddington                       11    On time
## 11:49  Oxford                                  -     On time
## 11:52  Ealing Broadway                         -     On time
## 11:53  Cheltenham Spa                          -     On time
## 11:53  Didcot Parkway                          -     On time
## 11:57  Bristol Temple Meads                    -     On time
## 11:58  London Paddington                       -     On time
## 12:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 12:04  London Paddington                       -     On time
## 12:07  Basingstoke                             -     On time
## 12:12  Ealing Broadway                         -     On time
## 12:12  London Paddington                       -     On time
## 12:12  London Waterloo                         -     On time
## 12:12  Newbury                                 -     On time
## 12:13  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 12:13  Swansea                                 -     On time
## 12:18  Hereford                                -     On time
## 12:20  Redhill                                 -     On time
## 12:22  Ealing Broadway                         -     On time
## 12:23  Didcot Parkway                          -     On time
## 12:24  London Paddington                       -     On time
## 12:26  London Paddington                       -     On time
## 12:27  Bristol Temple Meads                    -     On time
## 12:29  Penzance                                -     On time
## 12:32  Basingstoke                             -     On time
## 12:34  London Paddington                       -     On time
## 12:37  Bedwyn                                  -     On time
## 12:38  Ealing Broadway                         -     On time
## 12:42  London Paddington                       -     On time
## 12:42  London Waterloo                         -     On time
## 12:43  Cardiff Central                         -     On time
## 12:47  London Paddington                       -     On time
## 12:49  Oxford                                  -     On time
## 12:52  Bournemouth                             -     On time
## 12:52  Ealing Broadway                         -     On time
## 12:53  Cheltenham Spa                          -     On time
## 12:53  Didcot Parkway                          -     On time
## 12:57  Bristol Temple Meads                    -     On time
## 12:57  London Paddington                       -     On time
## 13:01  Exeter St Davids                        -     On time
## 13:01  Gatwick Airport                         -     On time
##        via Guildford                           
## 11:15  Heathrow Central Bus Stn                BUS   On time
## 11:50  Heathrow Central Bus Stn                BUS   On time
## 12:25  Heathrow Central Bus Stn                -     On time
## 13:00  Heathrow Central Bus Stn                -     On time
```
