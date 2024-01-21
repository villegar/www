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

## Example (Last rendered on 2024-01-21 19:07)

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
## Reading (RDG) Station Board on 2024-01-21 19:07:13.433564
## Time   From                                    Plat  Expected
## 18:58  Penzance                                11    19:07
## 18:59  Great Malvern                           10    19:14
## 19:02  Bournemouth                             8     19:17
## 19:07  London Paddington                       9     19:12
## 19:08  Bristol Temple Meads                    10A   19:19
## 19:11  Guildford                               5     On time
## 19:12  London Paddington                       14    19:16
## 19:12  London Paddington                       7     19:14
## 19:14  Swindon                                 11A   19:26
## 19:19  Bedwyn                                  1     On time
## 19:22  Oxford                                  10A   On time
## 19:24  London Paddington                       9     On time
## 19:27  London Waterloo                         6     On time
## 19:35  Didcot Parkway                          12    On time
## 19:38  Guildford                               5     On time
## 19:39  Manchester Piccadilly                   15    19:48
## 19:40  Paignton                                11A   20:02
## 19:42  London Paddington                       14    19:45
## 19:44  Carmarthen                              10A   On time
## 19:47  London Paddington                       13B   On time
## 19:49  London Paddington                       8B    On time
## 19:54  London Paddington                       9     On time
## 19:54  London Waterloo                         4     20:06
## 19:58  Penzance                                11    20:02
## 19:59  Hereford                                10    On time
## 20:07  London Paddington                       9     On time
## 20:09  Bristol Temple Meads                    10    On time
## 20:11  Guildford                               13    On time
## 20:12  London Paddington                       8B    On time
## 20:13  London Paddington                       14    On time
## 20:14  Swindon                                 11    On time
## 20:18  Newbury                                 1     On time
## 20:22  Oxford                                  10    On time
## 20:27  London Paddington                       7     On time
## 20:27  London Waterloo                         6     On time
## 20:35  Didcot Parkway                          12    On time
## 20:38  Guildford                               5     On time
## 20:39  Manchester Piccadilly                   8     On time
## 20:41  Plymouth                                11    On time
## 20:42  London Paddington                       14    On time
## 20:47  London Paddington                       13    On time
## 20:49  Swansea                                 10    On time
## 20:51  London Paddington                       7B    On time
## 20:54  London Paddington                       9     On time
## 20:54  London Waterloo                         4     On time
## 20:58  Penzance                                11    21:23
## 20:59  Great Malvern                           10    On time
## 19:16  Bramley (Hampshire)                     BUS   On time
## 19:18  Heathrow Airport T3 (Bus)               BUS   On time
## 19:48  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Winchester                              BUS   On time
## 20:10  Heathrow Airport T3 (Bus)               BUS   On time
## 20:16  Bramley (Hampshire)                     BUS   On time
## 20:40  Heathrow Airport T3 (Bus)               BUS   On time
## 21:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-21 19:07:18.564829
## Time   To                                      Plat  Expected
## 19:03  London Paddington                       10    19:15
## 19:06  London Paddington                       11    19:08
## 19:10  Swansea                                 9     19:13
## 19:12  London Paddington                       10A   19:20
## 19:12  Manchester Piccadilly                   8     19:18
##        via Coventry & Wilmslow                 
## 19:15  London Paddington                       11A   19:27
## 19:16  Hereford                                7     On time
## 19:21  Guildford                               5     On time
## 19:24  London Waterloo                         4     On time
## 19:26  Bristol Temple Meads                    9     On time
## 19:26  Didcot Parkway                          12A   On time
## 19:28  Plymouth                                8     Delayed
## 19:29  Ealing Broadway                         14    On time
## 19:29  London Paddington                       10A   On time
## 19:42  London Paddington                       11A   20:03
## 19:43  Bedwyn                                  1     On time
## 19:48  Swindon                                 13B   On time
## 19:50  London Waterloo                         6     On time
## 19:52  Oxford                                  8B    On time
## 19:55  London Paddington                       10A   On time
## 19:59  Ealing Broadway                         14    On time
## 20:00  Bristol Temple Meads                    9     On time
## 20:03  London Paddington                       10    On time
## 20:06  London Paddington                       11    On time
## 20:10  Swansea                                 9     On time
## 20:12  Guildford                               5     On time
## 20:12  London Paddington                       10    On time
## 20:14  Great Malvern                           8B    On time
## 20:14  Manchester Piccadilly                   15    On time
##        via Coventry & Wilmslow                 
## 20:15  London Paddington                       11    On time
## 20:24  London Waterloo                         4     On time
## 20:26  Didcot Parkway                          12A   On time
## 20:28  Plymouth                                7     On time
## 20:29  Ealing Broadway                         14    On time
## 20:29  London Paddington                       10    On time
## 20:42  London Paddington                       11    On time
## 20:43  Newbury                                 1     On time
## 20:46  Southampton Central                     -     Cancelled
## 20:48  Swindon                                 13    On time
## 20:50  London Waterloo                         6     On time
## 20:53  Oxford                                  7B    On time
## 20:55  London Paddington                       10    On time
## 20:59  Ealing Broadway                         14    On time
## 21:00  Bristol Temple Meads                    9     On time
## 21:03  London Paddington                       10    On time
## 21:06  London Paddington                       11    21:24
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:37  Bramley (Hampshire)                     BUS   On time
## 19:52  Winchester                              BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 20:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:37  Bramley (Hampshire)                     BUS   On time
## 20:52  Winchester                              BUS   On time
## 21:05  Heathrow Airport T3 (Bus)               BUS   On time
```
