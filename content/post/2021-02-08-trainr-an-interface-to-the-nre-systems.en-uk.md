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

## Example (Last rendered on 2024-01-14 17:04)

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
## Reading (RDG) Station Board on 2024-01-14 17:04:14.95233
## Time   From                                    Plat  Expected
## 16:50  Swansea                                 11    On time
## 16:58  Penzance                                12    17:00
## 16:59  Hereford                                10A   On time
## 17:00  London Paddington                       9B    On time
## 17:00  Sheffield                               13    17:03
## 17:02  Ascot                                   4     On time
## 17:03  Bournemouth                             8     16:54
## 17:05  Abbey Wood                              14    On time
## 17:10  Redhill                                 5     On time
## 17:15  London Paddington                       12    On time
## 17:20  Bedwyn                                  1     17:24
## 17:22  Oxford                                  11A   On time
## 17:24  Bristol Temple Meads                    10    On time
## 17:28  London Paddington                       7     On time
## 17:31  London Paddington                       -     Cancelled
## 17:32  Ascot                                   4     On time
## 17:35  Abbey Wood                              14    On time
## 17:35  Didcot Parkway                          15    On time
## 17:37  Paignton                                -     Cancelled
## 17:38  Gatwick Airport                         6     On time
## 17:40  Manchester Piccadilly                   3     On time
## 17:46  London Paddington                       -     Cancelled
## 17:51  Swansea                                 11    On time
## 17:58  Plymouth                                12    On time
## 17:59  Hereford                                10A   On time
## 18:00  London Paddington                       9B    On time
## 18:02  Ascot                                   4     On time
## 18:05  Abbey Wood                              14    On time
## 18:10  Redhill                                 5     On time
## 18:15  London Paddington                       13A   On time
## 18:21  Newbury                                 1     On time
## 18:22  Oxford                                  10A   On time
## 18:24  Plymouth                                11    On time
## 18:28  London Paddington                       7     On time
## 18:31  London Paddington                       8     On time
## 18:34  Ascot                                   4     On time
## 18:35  Abbey Wood                              14    18:39
## 18:35  Didcot Parkway                          15    On time
## 18:38  Gatwick Airport                         6     On time
## 18:40  Manchester Piccadilly                   8     On time
## 18:46  London Paddington                       9     On time
## 18:58  London Paddington                       7     On time
## 19:02  Ascot                                   4     On time
## 17:15  Swindon                                 BUS   On time
## 17:16  Bramley (Hampshire)                     BUS   On time
## 17:18  Heathrow Airport T3 (Bus)               BUS   On time
## 17:45  Swindon                                 BUS   On time
## 17:48  Heathrow Airport T3 (Bus)               BUS   On time
## 18:00  Winchester                              BUS   On time
## 18:15  Swindon                                 BUS   On time
## 18:16  Bramley (Hampshire)                     BUS   On time
## 18:18  Heathrow Airport T3 (Bus)               BUS   On time
## 18:45  Swindon                                 BUS   On time
## 18:48  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-14 17:04:17.037409
## Time   To                                      Plat  Expected
## 17:05  London Paddington                       11    On time
## 17:08  London Paddington                       12    On time
## 17:14  Great Malvern                           9B    On time
## 17:14  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 17:15  London Paddington                       10A   On time
## 17:17  Swansea                                 7     On time
## 17:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:24  Ascot                                   4     On time
## 17:24  London Paddington                       11A   On time
## 17:25  Didcot Parkway                          12    On time
## 17:29  Abbey Wood                              14    On time
## 17:29  Penzance                                7     On time
## 17:34  Plymouth                                -     Cancelled
## 17:36  London Paddington                       10    On time
## 17:37  London Paddington                       15    On time
## 17:42  London Paddington                       -     Cancelled
## 17:42  Newcastle                               13B   On time
##        via Coventry & Doncaster                
## 17:45  Bedwyn                                  1     On time
## 17:49  Oxford                                  -     Cancelled
## 17:53  Ascot                                   4     On time
## 17:59  Abbey Wood                              14    On time
## 18:01  Redhill                                 6     On time
## 18:05  London Paddington                       11    On time
## 18:08  London Paddington                       12    18:11
## 18:14  Great Malvern                           9B    On time
## 18:14  Manchester Piccadilly                   3     On time
##        via Coventry & Wilmslow                 
## 18:15  London Paddington                       10A   On time
## 18:17  Swansea                                 8     On time
## 18:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:24  Ascot                                   4     On time
## 18:24  London Paddington                       10A   On time
## 18:25  Didcot Parkway                          13A   On time
## 18:29  Abbey Wood                              14    On time
## 18:29  Penzance                                7     On time
## 18:34  Bristol Temple Meads                    8     On time
## 18:36  London Paddington                       11    On time
## 18:37  London Paddington                       15    On time
## 18:43  Newbury                                 1     On time
## 18:49  Bournemouth                             8     On time
## 18:49  Oxford                                  9     On time
## 18:53  Ascot                                   4     On time
## 18:59  Abbey Wood                              14    On time
## 19:01  Plymouth                                7     On time
## 19:01  Redhill                                 6     On time
## 17:05  Swindon                                 BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:37  Bramley (Hampshire)                     BUS   On time
## 17:40  Swindon                                 BUS   On time
## 17:52  Winchester                              BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:05  Swindon                                 BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:37  Bramley (Hampshire)                     BUS   On time
## 18:40  Swindon                                 BUS   On time
## 18:52  Winchester                              BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
```
