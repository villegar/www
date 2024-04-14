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

## Example (Last rendered on 2024-04-14 11:41)

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
## Reading (RDG) Station Board on 2024-04-14 11:41:20.870733
## Time   From                                    Plat  Expected
## 12:40  Manchester Piccadilly                   7B    12:55
## 12:44  Swansea                                 10    12:47
## 12:45  London Paddington                       9     On time
## 12:47  Salisbury                               2     On time
## 12:53  London Paddington                       9     On time
## 12:53  Penzance                                11    On time
## 12:56  London Paddington                       7     On time
## 12:57  Great Malvern                           10    13:00
## 13:02  London Waterloo                         4     On time
## 13:04  London Paddington                       7     On time
## 13:05  Southampton Airport Parkway             8B    On time
## 13:06  Abbey Wood                              14    13:09
## 13:07  London Paddington                       9     On time
## 13:09  Weston-super-Mare                       10    On time
## 13:17  Bedwyn                                  1     On time
## 13:22  Paignton                                11    On time
## 13:23  Bristol Parkway                         10A   On time
## 13:26  London Paddington                       7     On time
## 13:27  Guildford                               5     On time
## 13:32  Basingstoke                             2     On time
## 13:32  London Waterloo                         4     On time
## 13:35  Bristol Temple Meads                    11    On time
## 13:35  Didcot Parkway                          13    On time
## 13:36  Abbey Wood                              14    On time
## 13:39  Manchester Piccadilly                   7B    On time
## 13:44  Swansea                                 10    On time
## 13:47  London Paddington                       9     On time
## 13:47  Salisbury                               2     On time
## 13:55  London Paddington                       8B    On time
## 13:57  Great Malvern                           10    On time
## 13:58  Penzance                                11    14:08
## 13:59  London Paddington                       9     On time
## 14:02  London Waterloo                         4     On time
## 14:04  London Paddington                       9     On time
## 14:06  Abbey Wood                              14    On time
## 14:06  Southampton Airport Parkway             12B   On time
## 14:07  London Paddington                       8     On time
## 14:09  Bristol Temple Meads                    10    On time
## 14:19  Newbury                                 1     On time
## 14:21  Swindon                                 11A   On time
## 14:26  London Paddington                       7     On time
## 14:27  Guildford                               5     On time
## 14:32  Basingstoke                             2     On time
## 14:32  London Waterloo                         4     On time
## 14:35  Didcot Parkway                          12    On time
## 14:36  Abbey Wood                              14    On time
## 12:45  Heathrow Airport T3 (Bus)               BUS   On time
## 13:15  Heathrow Airport T3 (Bus)               BUS   On time
## 13:45  Heathrow Airport T3 (Bus)               BUS   On time
## 14:15  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-04-14 11:41:24.557028
## Time   To                                      Plat  Expected
## 12:37  Basingstoke                             2     12:39
## 12:43  Newbury                                 1     On time
## 12:46  London Paddington                       10    12:48
## 12:46  Swindon                                 9     On time
## 12:52  Southampton Airport Parkway             7B    12:56
## 12:54  London Waterloo                         4     On time
## 12:55  Weston-super-Mare                       9     On time
## 13:01  Paignton                                7     On time
## 13:02  Abbey Wood                              14    On time
## 13:05  London Paddington                       10    On time
## 13:05  London Paddington                       11    On time
## 13:09  Swansea                                 7     On time
## 13:12  Yeovil Pen Mill                         2     On time
## 13:13  Hereford                                9     On time
## 13:13  London Paddington                       10    On time
## 13:14  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 13:24  London Waterloo                         4     On time
## 13:25  London Paddington                       11    On time
## 13:25  London Paddington                       10A   On time
## 13:26  Didcot Parkway                          12A   On time
## 13:28  Plymouth                                7     On time
## 13:32  Abbey Wood                              14    On time
## 13:35  Guildford                               5     On time
## 13:36  London Paddington                       11    On time
## 13:37  Basingstoke                             2     On time
## 13:43  Bedwyn                                  1     On time
## 13:46  London Paddington                       10    On time
## 13:49  Swindon                                 9     On time
## 13:52  Southampton Airport Parkway             7B    On time
## 13:54  London Waterloo                         4     On time
## 13:57  Oxford                                  8B    On time
## 14:01  Bristol Temple Meads                    9     On time
## 14:02  Abbey Wood                              14    On time
## 14:05  London Paddington                       10    On time
## 14:07  London Paddington                       11    14:09
## 14:10  Swansea                                 9     On time
## 14:12  Salisbury                               2     On time
## 14:13  London Paddington                       10    On time
## 14:15  Great Malvern                           8     On time
## 14:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 14:22  London Paddington                       11A   On time
## 14:24  London Waterloo                         4     On time
## 14:26  Didcot Parkway                          13A   On time
## 14:28  Penzance                                7     On time
## 14:32  Abbey Wood                              14    On time
## 14:35  Guildford                               5     On time
## 14:37  Basingstoke                             2     On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
```
