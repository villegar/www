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

## Example (Last rendered on 2023-01-14 18:07)

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
## Reading (RDG) Station Board on 2023-01-14 18:07:10
## Time   From                                    Plat  Expected
## 17:58  Plymouth                                11    18:31
## 18:01  Didcot Parkway                          15    On time
## 18:10  Bristol Temple Meads                    10    18:37
## 18:10  London Paddington                       12    On time
## 18:11  London Paddington                       -     Cancelled
## 18:17  London Paddington                       9     On time
## 18:19  London Waterloo                         5     On time
## 18:21  Bristol Parkway                         -     Cancelled
## 18:23  Basingstoke                             2     On time
## 18:25  London Paddington                       -     Cancelled
## 18:25  Oxford                                  10    On time
## 18:27  London Paddington                       7     18:29
## 18:29  Newbury                                 11    On time
## 18:31  Didcot Parkway                          15    On time
## 18:33  Abbey Wood                              14    On time
## 18:33  Gloucester                              10    18:35
## 18:33  London Paddington                       7     On time
## 18:33  Redhill                                 4     On time
## 18:40  Bath Spa                                -     Cancelled
## 18:41  London Paddington                       -     Cancelled
## 18:41  London Waterloo                         6     18:48
## 18:41  Manchester Piccadilly                   7     On time
## 18:42  Newbury                                 1     On time
## 18:43  London Paddington                       12    On time
## 18:46  Swansea                                 -     Cancelled
## 18:47  London Paddington                       9     On time
## 18:50  Basingstoke                             2     On time
## 18:51  Gatwick Airport                         5     On time
## 18:51  London Paddington                       8     On time
## 18:54  Great Malvern                           10    18:56
## 18:55  London Paddington                       9     On time
## 18:57  Salisbury                               3     On time
## 18:59  Penzance                                11    19:09
## 19:01  Didcot Parkway                          15    On time
## 19:03  Abbey Wood                              14    On time
## 19:06  Southampton Central                     13B   On time
## 19:10  Bristol Temple Meads                    -     Cancelled
## 19:11  London Paddington                       -     Cancelled
## 19:11  London Waterloo                         5     On time
## 19:12  London Paddington                       12    On time
## 19:17  London Paddington                       9     On time
## 19:22  Basingstoke                             2     On time
## 19:25  London Paddington                       -     Cancelled
## 19:26  Oxford                                  10    On time
## 19:27  London Paddington                       7     On time
## 19:27  Newbury                                 11    On time
## 19:31  Didcot Parkway                          15    On time
## 19:32  London Paddington                       7     On time
## 19:32  Redhill                                 6     On time
## 19:33  Abbey Wood                              14    On time
## 19:38  London Paddington                       -     Cancelled
## 19:40  Bath Spa                                -     Cancelled
## 19:40  Manchester Piccadilly                   13    On time
## 19:40  Newbury                                 1     On time
## 19:41  London Waterloo                         4     On time
## 19:43  London Paddington                       12    On time
## 19:46  Swansea                                 -     Cancelled
## 19:47  London Paddington                       7     On time
## 19:49  London Paddington                       8     On time
## 19:51  Basingstoke                             2     On time
## 19:51  Gatwick Airport                         5     On time
## 19:51  London Paddington                       9     On time
## 19:54  Worcester Foregate Street               10    On time
## 19:55  London Paddington                       8     On time
## 19:57  Salisbury                               3     On time
## 20:02  Plymouth                                11    On time
## 20:03  Abbey Wood                              14    On time
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
## Reading (RDG) Station Board on 2023-01-14 18:07:14
## Time   To                                      Plat  Expected
## 18:05  London Paddington                       11    18:41
## 18:10  Newbury                                 1     On time
## 18:12  London Paddington                       10    18:38
## 18:12  London Waterloo                         6     On time
## 18:13  Swansea                                 -     Cancelled
## 18:15  Ealing Broadway                         15    On time
## 18:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 18:18  Yeovil Junction                         3     On time
## 18:19  Worcester Foregate Street               9     On time
## 18:23  Didcot Parkway                          12    On time
## 18:24  Abbey Wood                              14    On time
## 18:24  London Paddington                       -     Cancelled
## 18:27  Bath Spa                                -     Cancelled
## 18:27  London Paddington                       10    On time
## 18:29  Penzance                                7     On time
## 18:32  London Paddington                       11    On time
## 18:34  Newbury                                 7     On time
## 18:35  London Paddington                       10    18:35
## 18:36  Redhill                                 4     On time
## 18:37  Basingstoke                             2     On time
## 18:42  London Paddington                       -     Cancelled
## 18:42  London Waterloo                         5     On time
## 18:43  Swansea                                 -     Cancelled
## 18:45  Ealing Broadway                         15    On time
## 18:49  Oxford                                  9     On time
## 18:50  London Paddington                       -     Cancelled
## 18:52  Southampton Central                     7     On time
## 18:53  Didcot Parkway                          12    On time
## 18:53  Gloucester                              8     On time
## 18:54  Abbey Wood                              14    On time
## 18:56  London Paddington                       10    18:56
## 18:57  Taunton                                 9     On time
## 19:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:05  Basingstoke                             2     On time
## 19:05  London Paddington                       11    19:10
## 19:10  Newbury                                 1     On time
## 19:12  London Paddington                       -     Cancelled
## 19:12  London Waterloo                         6     On time
## 19:13  Swansea                                 -     Cancelled
## 19:15  Ealing Broadway                         15    On time
## 19:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 19:15  Salisbury                               3     On time
## 19:19  Hereford                                9     On time
## 19:20  Gatwick Airport                         4     On time
##        via Guildford                           
## 19:23  Didcot Parkway                          12    On time
## 19:24  Abbey Wood                              14    On time
## 19:27  Bath Spa                                -     Cancelled
## 19:28  London Paddington                       10    On time
## 19:29  Plymouth                                7     On time
## 19:32  London Paddington                       11    On time
## 19:34  Newbury                                 7     On time
## 19:37  Basingstoke                             2     On time
## 19:41  Swansea                                 -     Cancelled
## 19:42  London Paddington                       -     Cancelled
## 19:42  London Waterloo                         5     On time
## 19:45  Ealing Broadway                         15    On time
## 19:48  London Paddington                       -     Cancelled
## 19:51  Oxford                                  8     On time
## 19:53  Gloucester                              9     On time
## 19:54  Abbey Wood                              14    On time
## 19:55  Didcot Parkway                          12    On time
## 19:56  London Paddington                       10    On time
## 19:58  Taunton                                 8     On time
## 20:01  Redhill                                 6     On time
## 20:03  London Paddington                       11    On time
## 20:05  Basingstoke                             2     On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
```
