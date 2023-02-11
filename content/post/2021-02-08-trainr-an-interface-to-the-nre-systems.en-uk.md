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

## Example (Last rendered on 2023-02-11 16:03)

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
## Reading (RDG) Station Board on 2023-02-11 16:03:57
## Time   From                                    Plat  Expected
## 15:59  London Paddington                       7     On time
## 16:00  Didcot Parkway                          15    On time
## 16:00  Plymouth                                11    15:57
## 16:03  Abbey Wood                              14    On time
## 16:10  Didcot Parkway                          10    On time
## 16:11  London Paddington                       12    On time
## 16:13  London Waterloo                         5     16:19
## 16:17  London Paddington                       -     Cancelled
## 16:20  Basingstoke                             2     On time
## 16:23  Bristol Temple Meads                    11    On time
## 16:25  London Paddington                       9     On time
## 16:27  London Paddington                       7     On time
## 16:31  Didcot Parkway                          15    On time
## 16:32  London Paddington                       8     On time
## 16:32  Oxford                                  10A   On time
## 16:33  Abbey Wood                              14    On time
## 16:33  Redhill                                 4     On time
## 16:41  Manchester Piccadilly                   7B    On time
## 16:41  Newbury                                 1     On time
## 16:43  London Paddington                       12    On time
## 16:43  London Waterloo                         -     Cancelled
## 16:47  London Paddington                       9B    On time
## 16:50  Basingstoke                             2     On time
## 16:51  Gatwick Airport                         5     On time
## 16:53  London Paddington                       8     On time
## 16:54  Great Malvern                           -     Cancelled
## 16:56  Swansea                                 11    On time
## 16:59  London Paddington                       7     On time
## 17:01  Didcot Parkway                          15    On time
## 17:01  Penzance                                10    On time
## 17:03  Abbey Wood                              14    On time
## 17:06  Bournemouth                             12    On time
## 17:10  Didcot Parkway                          10    On time
## 17:10  London Paddington                       13    On time
## 17:13  London Waterloo                         4     On time
## 17:17  London Paddington                       -     Cancelled
## 17:20  Basingstoke                             2     On time
## 17:25  London Paddington                       9     On time
## 17:26  Bristol Temple Meads                    -     Cancelled
## 17:27  London Paddington                       7     On time
## 17:31  Didcot Parkway                          15    On time
## 17:32  London Paddington                       7     On time
## 17:32  Oxford                                  10A   On time
## 17:33  Abbey Wood                              14    On time
## 17:33  Redhill                                 5     On time
## 17:41  Manchester Piccadilly                   7     On time
## 17:41  Newbury                                 1     On time
## 17:43  London Paddington                       12    On time
## 17:43  London Waterloo                         6     On time
## 17:44  Paignton                                11    On time
## 17:47  London Paddington                       8B    On time
## 17:50  Basingstoke                             2     On time
## 17:51  Gatwick Airport                         4     On time
## 17:54  Hereford                                -     Cancelled
## 17:55  Swansea                                 11    On time
## 17:59  London Paddington                       8     On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:08  Swindon                                 BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 16:53  Chippenham                              BUS   On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
## 17:08  Swindon                                 BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
## 17:53  Chippenham                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-11 16:04:02
## Time   To                                      Plat  Expected
## 16:01  Swansea                                 7     16:03
## 16:05  London Paddington                       11    On time
## 16:07  Basingstoke                             2     On time
## 16:09  London Waterloo                         6     On time
## 16:11  London Paddington                       10    On time
## 16:12  Newbury                                 1     On time
## 16:15  Ealing Broadway                         15    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:19  Great Malvern                           -     Cancelled
## 16:20  Redhill                                 4     On time
## 16:23  Didcot Parkway                          12    On time
## 16:24  Abbey Wood                              14    On time
## 16:27  Didcot Parkway                          9     On time
## 16:29  Plymouth                                7     On time
## 16:32  London Paddington                       11    On time
## 16:34  Taunton                                 8     On time
## 16:37  Basingstoke                             2     On time
## 16:37  London Paddington                       10A   On time
## 16:39  London Waterloo                         5     On time
## 16:45  Ealing Broadway                         15    On time
## 16:49  Oxford                                  9B    On time
## 16:52  Bournemouth                             7B    On time
## 16:53  Didcot Parkway                          12    On time
## 16:54  Abbey Wood                              14    On time
## 16:55  Paignton                                8     On time
## 16:56  London Paddington                       -     Cancelled
## 16:59  London Paddington                       11    On time
## 17:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 17:01  Swansea                                 7     On time
## 17:05  London Paddington                       10    On time
## 17:07  Basingstoke                             2     On time
## 17:09  London Waterloo                         6     On time
## 17:11  London Paddington                       10    On time
## 17:12  Newbury                                 1     On time
## 17:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 17:19  Hereford                                -     Cancelled
## 17:20  Ealing Broadway                         15    On time
## 17:20  Redhill                                 5     On time
## 17:23  Didcot Parkway                          13    On time
## 17:24  Abbey Wood                              14    On time
## 17:27  Didcot Parkway                          9     On time
## 17:29  Penzance                                7     On time
## 17:32  London Paddington                       -     Cancelled
## 17:34  Weston-super-Mare                       7     On time
## 17:37  London Paddington                       10A   On time
## 17:38  Basingstoke                             2     On time
## 17:39  London Waterloo                         4     On time
## 17:45  Ealing Broadway                         15    On time
## 17:46  London Paddington                       11    On time
## 17:50  Oxford                                  8B    On time
## 17:54  Abbey Wood                              14    On time
## 17:55  Didcot Parkway                          12    On time
## 17:56  London Paddington                       -     Cancelled
## 17:59  London Paddington                       11    On time
## 18:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:01  Swansea                                 8     On time
## 16:05  Swindon                                 BUS   On time
## 16:15  Chippenham                              BUS   On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
## 17:05  Swindon                                 BUS   On time
## 17:15  Chippenham                              BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
```
