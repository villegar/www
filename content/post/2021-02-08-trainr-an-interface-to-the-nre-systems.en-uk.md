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

## Example (Last rendered on 2021-07-17 18:17)

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
## Reading (RDG) Station Board on 2021-07-17 18:17:05
## Time   From                                    Plat  Expected
## 18:54  Moreton-in-Marsh                        11A   19:12
## 18:59  Penzance                                11    20:27
## 19:01  Didcot Parkway                          15    On time
## 19:07  Bournemouth                             13    On time
## 19:11  London Paddington                       9B    On time
## 19:17  London Paddington                       9     19:20
## 19:25  London Paddington                       9     On time
## 19:25  Oxford                                  10    On time
## 19:26  Newbury                                 15    On time
## 19:27  London Paddington                       7     On time
## 19:28  Ascot                                   5     On time
## 19:32  Redhill                                 6     On time
## 19:36  London Paddington                       8     On time
## 19:39  Manchester Piccadilly                   13    19:45
## 19:40  Newbury                                 1     On time
## 19:40  Weston-super-Mare                       10    On time
## 19:43  London Paddington                       14    On time
## 19:44  London Paddington                       12    On time
## 19:44  Penzance                                11    20:50
## 19:46  Carmarthen                              10    19:48
## 19:47  London Paddington                       9B    On time
## 19:48  Ascot                                   4     On time
## 19:51  Basingstoke                             2     On time
## 19:51  Gatwick Airport                         5     On time
## 19:51  London Paddington                       8     On time
## 19:54  Great Malvern                           10A   20:02
## 19:55  London Paddington                       -     Cancelled
## 20:01  Didcot Parkway                          15    On time
## 20:02  Paignton                                11    20:09
## 20:10  Bristol Temple Meads                    10    On time
## 20:11  London Paddington                       8B    20:24
## 20:13  London Paddington                       14    On time
## 20:17  London Paddington                       9B    On time
## 20:18  Newbury                                 11    On time
## 20:25  London Paddington                       -     Cancelled
## 20:25  Oxford                                  10A   On time
## 20:27  London Paddington                       7     On time
## 20:28  Ascot                                   6     On time
## 20:34  Cheltenham Spa                          -     Cancelled
## 20:36  Redhill                                 5     On time
## 20:39  Manchester Piccadilly                   7     On time
## 20:42  Newbury                                 1     On time
## 20:43  London Paddington                       14    On time
## 20:44  London Paddington                       12    On time
## 20:46  Swansea                                 10    On time
## 20:47  London Paddington                       9     On time
## 20:48  Ascot                                   4     On time
## 20:50  Basingstoke                             2     On time
## 20:54  Great Malvern                           10A   On time
## 20:55  Gatwick Airport                         14B   On time
## 20:55  London Paddington                       9B    On time
## 21:01  Didcot Parkway                          15    On time
## 21:05  Bournemouth                             13B   On time
## 21:10  Bristol Temple Meads                    -     Cancelled
## 21:11  London Paddington                       9     On time
## 21:13  London Paddington                       14    On time
## 21:15  Penzance                                11    21:26
## 19:19  Heathrow Central Bus Stn                BUS   On time
## 20:13  Heathrow Central Bus Stn                BUS   On time
## 21:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-07-17 18:17:10
## Time   To                                      Plat  Expected
## 18:56  London Paddington                       11A   19:15
## 19:13  Swansea                                 9B    19:15
## 19:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 19:19  Hereford                                9     19:21
## 19:20  Gatwick Airport                         4     On time
##        via Guildford                           
## 19:22  Ealing Broadway                         14    On time
## 19:26  London Paddington                       10    On time
## 19:27  Bath Spa                                9     On time
## 19:29  Plymouth                                7     On time
## 19:37  Basingstoke                             2     On time
## 19:42  Ascot                                   5     On time
## 19:42  London Paddington                       10    On time
## 19:42  Newbury                                 8     On time
## 19:46  London Paddington                       11    20:51
## 19:48  London Paddington                       10    19:48
## 19:49  Oxford                                  9B    On time
## 19:52  Ealing Broadway                         14    On time
## 19:53  Cheltenham Spa                          8     On time
## 19:53  Didcot Parkway                          12    On time
## 19:56  London Paddington                       10A   20:02
## 19:57  Weston-super-Mare                       -     Cancelled
## 20:01  Redhill                                 6     On time
## 20:03  London Paddington                       11    20:10
## 20:10  Newbury                                 1     On time
## 20:12  Ascot                                   4     On time
## 20:12  London Paddington                       10    On time
## 20:13  Swansea                                 8B    20:25
## 20:15  Ealing Broadway                         15    On time
## 20:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 20:19  Great Malvern                           9B    On time
## 20:19  London Paddington                       11    On time
## 20:22  Ealing Broadway                         14    On time
## 20:27  Bath Spa                                -     Cancelled
## 20:27  London Paddington                       10A   On time
## 20:29  Plymouth                                7     On time
## 20:33  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:35  London Paddington                       -     Cancelled
## 20:37  Basingstoke                             2     On time
## 20:42  Ascot                                   6     On time
## 20:48  London Paddington                       10    On time
## 20:49  Oxford                                  9     On time
## 20:52  Bournemouth                             7     On time
## 20:52  Ealing Broadway                         14    On time
## 20:53  Didcot Parkway                          12    On time
## 20:56  London Paddington                       10A   On time
## 20:57  Exeter St Davids                        9B    On time
##        via Bristol                             
## 21:10  Newbury                                 1     On time
## 21:12  Ascot                                   4     On time
## 21:12  London Paddington                       -     Cancelled
## 21:13  Swansea                                 9     On time
## 21:15  Birmingham New Street                   13B   On time
##        via Coventry                            
## 21:15  Ealing Broadway                         15    On time
## 21:16  London Paddington                       11    21:27
## 20:00  Heathrow Central Bus Stn                BUS   On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
```
