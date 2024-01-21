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

## Example (Last rendered on 2024-01-21 17:04)

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
## Reading (RDG) Station Board on 2024-01-21 17:04:26.404314
## Time   From                                    Plat  Expected
## 16:58  Bournemouth                             8B    On time
## 16:58  Penzance                                11    17:06
## 16:59  Hereford                                10    17:22
## 17:00  London Paddington                       7     On time
## 17:00  Sheffield                               -     Cancelled
## 17:09  Bristol Temple Meads                    10    17:14
## 17:11  Guildford                               5     On time
## 17:12  London Paddington                       14    17:16
## 17:12  London Paddington                       9     17:18
## 17:14  Swindon                                 11    17:16
## 17:20  Bedwyn                                  3     17:23
## 17:22  Oxford                                  10    17:24
## 17:24  London Paddington                       9     On time
## 17:27  London Waterloo                         4     On time
## 17:35  Bristol Temple Meads                    10    On time
## 17:35  Didcot Parkway                          15    On time
## 17:36  Paignton                                11    17:44
## 17:38  Guildford                               5     On time
## 17:39  Manchester Piccadilly                   12    On time
## 17:42  London Paddington                       14    17:47
## 17:44  Carmarthen                              10    On time
## 17:48  London Paddington                       9B    On time
## 17:51  London Paddington                       13B   On time
## 17:54  London Waterloo                         4     On time
## 17:57  London Paddington                       8     On time
## 17:58  Plymouth                                11    18:12
## 17:59  Hereford                                10    18:01
## 18:07  London Paddington                       7     On time
## 18:09  Cardiff Central                         10    On time
## 18:11  Guildford                               5     On time
## 18:12  London Paddington                       14    On time
## 18:12  London Paddington                       9B    On time
## 18:14  Bristol Temple Meads                    11    On time
## 18:21  Newbury                                 1     On time
## 18:22  Oxford                                  11A   On time
## 18:24  London Paddington                       9B    On time
## 18:27  London Waterloo                         4     On time
## 18:29  Cheltenham Spa                          10A   On time
## 18:35  Bristol Temple Meads                    11    On time
## 18:35  Didcot Parkway                          12    On time
## 18:38  Guildford                               5     On time
## 18:40  Manchester Piccadilly                   8     On time
## 18:42  London Paddington                       14    On time
## 18:44  Swansea                                 10    On time
## 18:47  London Paddington                       13B   On time
## 18:51  London Paddington                       8     On time
## 18:54  London Waterloo                         4     On time
## 18:56  London Paddington                       9     On time
## 18:59  Great Malvern                           10    On time
## 18:59  London Paddington                       7     On time
## 17:16  Bramley (Hampshire)                     BUS   On time
## 17:18  Heathrow Airport T3 (Bus)               BUS   On time
## 17:48  Heathrow Airport T3 (Bus)               BUS   On time
## 18:00  Winchester                              BUS   On time
## 18:16  Bramley (Hampshire)                     BUS   On time
## 18:18  Heathrow Airport T3 (Bus)               BUS   On time
## 18:48  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-21 17:04:28.218325
## Time   To                                      Plat  Expected
## 17:02  Plymouth                                7     On time
## 17:03  London Paddington                       10    17:23
## 17:06  London Paddington                       11    17:07
## 17:10  Swansea                                 7     17:14
## 17:12  London Paddington                       10    17:15
## 17:14  Great Malvern                           9     17:19
## 17:14  Manchester Piccadilly                   8B    On time
##        via Coventry & Wilmslow                 
## 17:15  London Paddington                       11    17:17
## 17:21  Guildford                               5     On time
## 17:24  London Waterloo                         4     On time
## 17:26  Bristol Temple Meads                    9     On time
## 17:26  Didcot Parkway                          12A   On time
## 17:28  Penzance                                7     On time
## 17:29  Ealing Broadway                         14    On time
## 17:29  London Paddington                       10    On time
## 17:36  London Paddington                       10    On time
## 17:42  London Paddington                       11    17:45
## 17:42  Newcastle                               -     Cancelled
##        via Coventry & Doncaster                
## 17:45  Bedwyn                                  3     On time
## 17:48  Swindon                                 9B    On time
## 17:50  London Waterloo                         4     On time
## 17:52  Oxford                                  13B   On time
## 17:55  London Paddington                       10    On time
## 17:56  Guildford                               5     On time
## 17:59  Cheltenham Spa                          8     On time
## 17:59  Ealing Broadway                         14    On time
## 18:03  London Paddington                       10    On time
## 18:06  London Paddington                       11    18:13
## 18:10  Swansea                                 7     On time
## 18:14  Great Malvern                           9B    On time
## 18:14  Manchester Piccadilly                   12B   On time
##        via Coventry & Wilmslow                 
## 18:15  London Paddington                       10    On time
## 18:18  London Paddington                       11    On time
## 18:21  Guildford                               5     On time
## 18:24  London Waterloo                         4     On time
## 18:26  Bristol Temple Meads                    9B    On time
## 18:26  Didcot Parkway                          15A   On time
## 18:28  Penzance                                7     On time
## 18:29  Ealing Broadway                         14    On time
## 18:29  London Paddington                       11A   On time
## 18:36  London Paddington                       10A   On time
## 18:42  London Paddington                       11    On time
## 18:43  Newbury                                 1     On time
## 18:46  Bournemouth                             8     On time
## 18:48  Swindon                                 13B   On time
## 18:50  London Waterloo                         4     On time
## 18:52  Oxford                                  8     On time
## 18:55  London Paddington                       10    On time
## 18:56  Guildford                               5     On time
## 18:59  Ealing Broadway                         14    On time
## 19:00  Bristol Temple Meads                    9     On time
## 19:01  Plymouth                                7     On time
## 19:03  London Paddington                       10    On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:37  Bramley (Hampshire)                     BUS   On time
## 17:52  Winchester                              BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:37  Bramley (Hampshire)                     BUS   On time
## 18:52  Winchester                              BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
```
