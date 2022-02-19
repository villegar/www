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

## Example (Last rendered on 2022-02-19 14:04)

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
## Reading (RDG) Station Board on 2022-02-19 14:04:24
## Time   From                                    Plat  Expected
## 13:25  Bedwyn                                  -     13:58
## 13:27  London Paddington                       7     14:05
## 13:41  Newbury                                 -     Delayed
## 13:46  Swansea                                 10    14:09
## 13:59  Exeter St Davids                        -     Cancelled
## 14:07  London Waterloo                         -     Cancelled
## 14:10  Bristol Temple Meads                    10    14:35
## 14:11  London Paddington                       9     On time
## 14:13  London Paddington                       14    On time
## 14:17  London Paddington                       9     Delayed
## 14:20  Basingstoke                             2     On time
## 14:23  Bedwyn                                  11    On time
## 14:25  London Paddington                       9     On time
## 14:25  Oxford                                  -     Cancelled
## 14:27  London Paddington                       7     On time
## 14:31  Didcot Parkway                          15    On time
## 14:33  Cheltenham Spa                          -     Cancelled
## 14:33  Redhill                                 -     Cancelled
## 14:40  Bristol Temple Meads                    -     Cancelled
## 14:40  Macclesfield                            13B   14:49
## 14:41  London Waterloo                         -     Cancelled
## 14:42  Newbury                                 1     On time
## 14:43  London Paddington                       14    On time
## 14:46  Swansea                                 10    14:49
## 14:47  London Paddington                       -     Cancelled
## 14:51  Basingstoke                             2     On time
## 14:51  Gatwick Airport                         -     Cancelled
## 14:51  London Paddington                       8     On time
## 14:53  Oxford                                  10    On time
## 14:59  London Paddington                       7     On time
## 15:00  Exeter St Davids                        -     Cancelled
## 15:01  Didcot Parkway                          15    On time
## 15:07  London Waterloo                         -     Cancelled
## 15:10  Bristol Temple Meads                    10    Delayed
## 15:11  London Paddington                       8     On time
## 15:13  London Paddington                       14    On time
## 15:14  London Paddington                       12    On time
## 15:17  London Paddington                       9     On time
## 15:20  Basingstoke                             2     On time
## 15:23  Bedwyn                                  11    On time
## 15:25  London Paddington                       9     On time
## 15:25  Oxford                                  -     Cancelled
## 15:27  London Paddington                       7     On time
## 15:31  Didcot Parkway                          15    On time
## 15:33  Gloucester                              11    On time
## 15:33  Redhill                                 -     Cancelled
## 15:38  London Paddington                       9     On time
## 15:40  Bristol Temple Meads                    10    On time
## 15:40  Newbury                                 1     On time
## 15:41  London Waterloo                         -     Cancelled
## 15:42  Exeter St Davids                        -     Cancelled
## 15:43  London Paddington                       14    On time
## 15:44  London Paddington                       12    On time
## 15:47  London Paddington                       -     Cancelled
## 15:47  Swansea                                 10    On time
## 15:51  Basingstoke                             2     On time
## 15:51  Gatwick Airport                         -     Cancelled
## 15:53  Hereford                                10    15:57
## 15:55  London Paddington                       9     On time
## 14:21  Heathrow Central Bus Stn                BUS   On time
## 15:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-19 14:04:29
## Time   To                                      Plat  Expected
## 13:30  Exeter St Davids                        7     14:06
## 13:48  London Paddington                       10    14:10
## 14:00  London Paddington                       -     Delayed
## 14:05  London Paddington                       -     Cancelled
## 14:07  Basingstoke                             2     On time
## 14:12  London Paddington                       10    14:36
## 14:12  London Waterloo                         -     Cancelled
## 14:12  Newbury                                 -     Cancelled
## 14:13  Swansea                                 9     On time
## 14:19  Great Malvern                           9     Delayed
## 14:20  Redhill                                 -     Cancelled
## 14:22  Ealing Broadway                         14    On time
## 14:24  Didcot Parkway                          13    On time
## 14:27  Bristol Temple Meads                    9     On time
## 14:27  London Paddington                       -     Cancelled
## 14:29  Exeter St Davids                        7     On time
## 14:34  Bedwyn                                  7B    On time
## 14:35  London Paddington                       -     Cancelled
## 14:37  Basingstoke                             2     On time
## 14:42  London Paddington                       -     Cancelled
## 14:42  London Waterloo                         -     Cancelled
## 14:48  London Paddington                       10    14:50
## 14:49  Oxford                                  -     Cancelled
## 14:52  Ealing Broadway                         14    On time
## 14:53  Cheltenham Spa                          8     On time
## 14:53  Didcot Parkway                          12    On time
## 14:56  London Paddington                       10    On time
## 15:01  Exeter St Davids                        7     On time
## 15:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 15:05  London Paddington                       -     Cancelled
## 15:07  Basingstoke                             2     On time
## 15:12  London Paddington                       10    Delayed
## 15:12  London Waterloo                         -     Cancelled
## 15:12  Newbury                                 -     Cancelled
## 15:13  Swansea                                 8     On time
## 15:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 15:19  Great Malvern                           9     On time
## 15:20  Redhill                                 -     Cancelled
## 15:22  Ealing Broadway                         14    On time
## 15:24  Didcot Parkway                          12    On time
## 15:27  Bristol Temple Meads                    9     On time
## 15:27  London Paddington                       -     Cancelled
## 15:29  Exeter St Davids                        7     On time
## 15:34  Bedwyn                                  7B    On time
## 15:35  London Paddington                       11    On time
## 15:37  Basingstoke                             2     On time
## 15:40  Bristol Parkway                         9     On time
## 15:42  London Waterloo                         -     Cancelled
## 15:43  London Paddington                       10    On time
## 15:45  Ealing Broadway                         15    On time
## 15:46  London Paddington                       -     Cancelled
## 15:48  London Paddington                       10    On time
## 15:49  Oxford                                  -     Cancelled
## 15:52  Ealing Broadway                         14    On time
## 15:53  Didcot Parkway                          12    On time
## 15:57  Bristol Temple Meads                    9     On time
## 15:58  London Paddington                       10    15:58
## 16:01  Gatwick Airport                         -     Cancelled
##        via Guildford                           
## 15:00  Heathrow Central Bus Stn                BUS   On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
```
