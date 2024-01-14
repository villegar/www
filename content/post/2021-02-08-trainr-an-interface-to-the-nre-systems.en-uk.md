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

## Example (Last rendered on 2024-01-14 11:04)

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
## Reading (RDG) Station Board on 2024-01-14 11:04:23.147316
## Time   From                                    Plat  Expected
## 10:46  London Paddington                       7B    11:04
## 10:59  London Paddington                       -     Cancelled
## 11:03  Ascot                                   4     On time
## 11:03  Southampton Central                     8     10:59
## 11:05  London Paddington                       14    11:08
## 11:10  Redhill                                 5     On time
## 11:14  Great Malvern                           10A   11:18
## 11:18  London Paddington                       13    On time
## 11:20  Bedwyn                                  1     On time
## 11:24  Bristol Temple Meads                    -     Cancelled
## 11:28  London Paddington                       7     On time
## 11:30  Oxford                                  9B    11:40
## 11:31  London Paddington                       8     11:34
## 11:32  Ascot                                   4     On time
## 11:35  Abbey Wood                              14    On time
## 11:35  Didcot Parkway                          15    On time
## 11:35  Totnes                                  11    On time
## 11:38  Gatwick Airport                         6     On time
## 11:38  Swansea                                 10    11:46
## 11:46  London Paddington                       9B    On time
## 11:49  Manchester Piccadilly                   3     On time
## 11:58  Totnes                                  11    On time
## 12:02  Ascot                                   4     On time
## 12:02  Swansea                                 10    On time
## 12:05  Abbey Wood                              14    On time
## 12:09  Great Malvern                           11A   On time
## 12:10  Redhill                                 5     On time
## 12:15  London Paddington                       13    On time
## 12:20  Newbury                                 1     On time
## 12:21  Oxford                                  10A   On time
## 12:23  Bristol Temple Meads                    11    On time
## 12:28  London Paddington                       7     On time
## 12:31  London Paddington                       -     Cancelled
## 12:32  Ascot                                   4     On time
## 12:35  Abbey Wood                              14    On time
## 12:36  Didcot Parkway                          15    On time
## 12:38  Gatwick Airport                         6     On time
## 12:46  Slough                                  9     On time
## 12:48  Manchester Piccadilly                   8B    On time
## 12:58  London Paddington                       7     On time
## 13:02  Ascot                                   4     On time
## 11:15  Heathrow Airport T3 (Bus)               BUS   On time
## 11:15  Swindon                                 BUS   On time
## 11:16  Bramley (Hampshire)                     BUS   On time
## 11:45  Heathrow Airport T3 (Bus)               BUS   On time
## 11:55  Swindon                                 BUS   On time
## 11:55  Winchester                              BUS   On time
## 12:15  Heathrow Airport T3 (Bus)               BUS   On time
## 12:15  Swindon                                 BUS   On time
## 12:16  Bramley (Hampshire)                     BUS   On time
## 12:45  Heathrow Airport T3 (Bus)               BUS   On time
## 12:45  Swindon                                 BUS   On time
## 12:55  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-14 11:04:26.106763
## Time   To                                      Plat  Expected
## 10:52  Oxford                                  7B    11:05
## 11:01  Paignton                                -     Cancelled
## 11:07  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 11:14  Great Malvern                           9B    On time
## 11:15  London Paddington                       10A   11:19
## 11:17  Carmarthen                              7     11:19
## 11:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:24  Ascot                                   4     On time
## 11:25  Didcot Parkway                          13    On time
## 11:28  London Paddington                       -     Cancelled
## 11:29  Abbey Wood                              14    On time
## 11:29  Plymouth                                7     On time
## 11:32  London Paddington                       9B    11:41
## 11:34  Bristol Temple Meads                    8     11:34
## 11:37  London Paddington                       15    On time
## 11:37  London Paddington                       11    On time
## 11:42  London Paddington                       10    11:47
## 11:43  Bedwyn                                  1     On time
## 11:52  Oxford                                  9B    On time
## 11:53  Ascot                                   4     On time
## 11:59  Abbey Wood                              14    On time
## 12:01  Redhill                                 6     On time
## 12:05  London Paddington                       11    On time
## 12:07  Manchester Piccadilly                   3     On time
##        via Coventry & Wilmslow                 
## 12:08  London Paddington                       10    On time
## 12:14  Hereford                                9B    On time
## 12:15  London Paddington                       11A   On time
## 12:17  Swansea                                 7     On time
## 12:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 12:24  Ascot                                   4     On time
## 12:24  London Paddington                       10A   On time
## 12:25  Didcot Parkway                          13    On time
## 12:29  Abbey Wood                              14    On time
## 12:29  Penzance                                7     On time
## 12:34  Weston-super-Mare                       -     Cancelled
## 12:35  London Paddington                       11    On time
## 12:37  London Paddington                       15    On time
## 12:43  Newbury                                 1     On time
## 12:49  Bournemouth                             8B    On time
## 12:52  Oxford                                  9     On time
## 12:53  Ascot                                   4     On time
## 12:59  Abbey Wood                              14    On time
## 13:01  Paignton                                7     On time
## 13:01  Redhill                                 6     On time
## 11:05  Swindon                                 BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:37  Bramley (Hampshire)                     BUS   On time
## 11:40  Swindon                                 BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
## 12:00  Winchester                              BUS   On time
## 12:05  Swindon                                 BUS   On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:37  Bramley (Hampshire)                     BUS   On time
## 12:40  Swindon                                 BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
## 13:00  Winchester                              BUS   On time
```
