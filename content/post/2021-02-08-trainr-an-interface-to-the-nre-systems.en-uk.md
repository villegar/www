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

## Example (Last rendered on 2022-12-10 20:04)

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
## Reading (RDG) Station Board on 2022-12-10 20:04:03
## Time   From                                    Plat  Expected
## 19:40  Weston-super-Mare                       10    20:16
## 19:46  Swansea                                 10    20:05
## 19:54  Great Malvern                           10A   20:14
## 19:55  London Paddington                       8     20:08
## 20:01  Didcot Parkway                          15    On time
## 20:02  Plymouth                                11    20:53
## 20:10  Bristol Temple Meads                    11    20:20
## 20:11  London Paddington                       8     On time
## 20:13  London Paddington                       12    On time
## 20:14  London Waterloo                         -     Cancelled
## 20:17  London Paddington                       9     20:19
## 20:18  Newbury                                 11    On time
## 20:23  Basingstoke                             2     On time
## 20:25  London Paddington                       9     20:36
## 20:25  Oxford                                  10A   On time
## 20:27  London Paddington                       7     On time
## 20:31  Didcot Parkway                          15    On time
## 20:33  Abbey Wood                              14    On time
## 20:33  Cheltenham Spa                          11A   20:55
## 20:35  Redhill                                 5     On time
## 20:39  Manchester Piccadilly                   7     20:41
## 20:42  London Paddington                       8     On time
## 20:43  London Paddington                       12    On time
## 20:43  Newbury                                 13    On time
## 20:44  London Waterloo                         4     21:00
## 20:46  Swansea                                 10    On time
## 20:47  London Paddington                       9     On time
## 20:50  Basingstoke                             2     On time
## 20:54  Great Malvern                           10A   On time
## 20:55  London Paddington                       9     On time
## 20:58  Gatwick Airport                         15    On time
## 21:03  Abbey Wood                              14    On time
## 21:04  Didcot Parkway                          15    On time
## 21:05  Bournemouth                             13B   On time
## 21:10  Bristol Temple Meads                    10    On time
## 21:11  London Paddington                       9     On time
## 21:13  London Paddington                       12    On time
## 21:14  London Waterloo                         6     Delayed
## 21:15  Penzance                                11    On time
## 21:17  London Paddington                       9     On time
## 21:22  Basingstoke                             2     On time
## 21:25  Bedwyn                                  12B   On time
## 21:25  Oxford                                  10    On time
## 21:31  Didcot Parkway                          13    On time
## 21:33  Abbey Wood                              14    On time
## 21:33  Cheltenham Spa                          10    On time
## 21:36  London Paddington                       12    On time
## 21:39  Manchester Piccadilly                   7B    On time
## 21:40  Newbury                                 1     On time
## 21:44  London Waterloo                         5     21:56
## 21:45  London Paddington                       13    On time
## 21:49  Swansea                                 10    On time
## 21:50  Basingstoke                             2     On time
## 21:51  London Paddington                       8     On time
## 21:51  Redhill                                 -     Cancelled
## 21:54  Worcester Foregate Street               11    On time
## 21:56  London Paddington                       9     On time
## 21:58  Gatwick Airport                         15    On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-10 20:04:10
## Time   To                                      Plat  Expected
## 19:42  London Paddington                       10    20:17
## 19:48  London Paddington                       10    20:06
## 19:56  London Paddington                       10A   20:17
## 19:57  Taunton                                 8     20:09
## 20:01  Redhill                                 -     Cancelled
## 20:03  London Paddington                       11    20:54
## 20:05  Basingstoke                             2     On time
## 20:09  London Waterloo                         -     Cancelled
## 20:10  Newbury                                 3     On time
## 20:12  London Paddington                       11    20:21
## 20:13  Swansea                                 8     On time
## 20:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 20:19  Great Malvern                           9     20:19
## 20:20  Ealing Broadway                         15    On time
## 20:20  London Paddington                       11    On time
## 20:23  Didcot Parkway                          12    On time
## 20:24  Abbey Wood                              14    On time
## 20:27  Bristol Temple Meads                    9     20:37
## 20:27  London Paddington                       10A   On time
## 20:29  Plymouth                                7     On time
## 20:32  Bedwyn                                  13B   On time
## 20:32  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:35  London Paddington                       11A   20:56
## 20:37  Basingstoke                             2     On time
## 20:39  London Waterloo                         -     Cancelled
## 20:44  Swindon                                 8     On time
## 20:45  Ealing Broadway                         15    On time
## 20:48  London Paddington                       10    On time
## 20:49  Oxford                                  9     On time
## 20:52  Bournemouth                             7     On time
## 20:53  Didcot Parkway                          12    On time
## 20:54  Abbey Wood                              14    On time
## 20:56  London Paddington                       10A   On time
## 20:57  Exeter St Davids                        9     On time
##        via Bristol                             
## 21:05  Basingstoke                             2     On time
## 21:09  London Waterloo                         4     On time
## 21:10  Newbury                                 7     On time
## 21:13  London Paddington                       10    On time
## 21:13  Swansea                                 9     On time
## 21:15  Birmingham New Street                   13B   On time
##        via Coventry                            
## 21:15  Ealing Broadway                         15    On time
## 21:16  London Paddington                       11    On time
## 21:19  Oxford                                  9     On time
## 21:21  Didcot Parkway                          12    On time
## 21:24  Abbey Wood                              14    On time
## 21:26  London Paddington                       10    On time
## 21:33  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:35  Basingstoke                             2     On time
## 21:35  London Paddington                       10    On time
## 21:39  London Waterloo                         6     On time
## 21:41  Ealing Broadway                         13    On time
## 21:51  London Paddington                       10    On time
## 21:52  Abbey Wood                              14    On time
## 21:52  Bournemouth                             7B    On time
## 21:53  Oxford                                  8     On time
## 21:56  London Paddington                       11    On time
## 21:57  Bristol Temple Meads                    9     On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
```
