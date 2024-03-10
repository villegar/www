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

## Example (Last rendered on 2024-03-10 17:06)

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
## Reading (RDG) Station Board on 2024-03-10 17:06:30.796219
## Time   From                                    Plat  Expected
## 16:57  Hereford                                10    17:10
## 16:59  Plymouth                                -     Cancelled
## 17:03  London Paddington                       9     On time
## 17:05  Abbey Wood                              14    On time
## 17:07  Eastleigh                               8B    17:04
## 17:08  Guildford                               5     17:05
## 17:09  Bristol Temple Meads                    10    17:13
## 17:15  Swindon                                 11    17:18
## 17:20  Bedwyn                                  3     On time
## 17:27  London Waterloo                         4     On time
## 17:28  London Paddington                       7     On time
## 17:33  Basingstoke                             2     17:36
## 17:35  Abbey Wood                              14    On time
## 17:35  Didcot Parkway                          12    On time
## 17:36  Paignton                                11A   17:42
## 17:38  Guildford                               5     On time
## 17:39  Manchester Piccadilly                   8B    17:44
## 17:44  Carmarthen                              11    Delayed
## 17:45  London Paddington                       13    17:47
## 17:48  Yeovil Pen Mill                         2     On time
## 17:57  Hereford                                10A   18:00
## 17:57  London Waterloo                         4     On time
## 17:58  Plymouth                                11    18:04
## 18:00  London Paddington                       9     On time
## 18:03  London Paddington                       7     On time
## 18:05  Abbey Wood                              14    On time
## 18:06  Eastleigh                               8     On time
## 18:08  Guildford                               5     On time
## 18:09  Plymouth                                10    On time
## 18:14  London Paddington                       9     On time
## 18:16  Swindon                                 11    On time
## 18:21  Newbury                                 1     On time
## 18:27  London Waterloo                         4     On time
## 18:28  London Paddington                       7     On time
## 18:29  Cheltenham Spa                          10    On time
## 18:30  London Paddington                       9     On time
## 18:33  Basingstoke                             2     On time
## 18:35  Abbey Wood                              14    On time
## 18:35  Didcot Parkway                          13    On time
## 18:38  Guildford                               5     On time
## 18:40  Manchester Piccadilly                   7     On time
## 18:44  Swansea                                 10    On time
## 18:45  London Paddington                       12    On time
## 18:47  Gillingham (Dorset)                     2     On time
## 18:57  London Waterloo                         4     On time
## 18:57  Worcester Shrub Hill                    10    On time
## 18:58  London Paddington                       9     On time
## 18:59  Plymouth                                -     Cancelled
## 19:00  London Paddington                       -     Cancelled
## 19:05  Abbey Wood                              14    On time
## 17:18  Heathrow Airport T3 (Bus)               BUS   On time
## 17:48  Heathrow Airport T3 (Bus)               BUS   On time
## 18:18  Heathrow Airport T3 (Bus)               BUS   On time
## 18:48  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-03-10 17:06:33.954447
## Time   To                                      Plat  Expected
## 16:59  London Paddington                       10    17:11
## 17:05  London Paddington                       -     Cancelled
## 17:10  Swansea                                 9     On time
## 17:12  Salisbury                               2     On time
## 17:14  London Paddington                       10    On time
## 17:14  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 17:15  Great Malvern                           9B    17:17
## 17:17  London Paddington                       11    17:19
## 17:21  Guildford                               5     On time
## 17:24  London Waterloo                         4     On time
## 17:25  Didcot Parkway                          12A   On time
## 17:29  Abbey Wood                              14    On time
## 17:29  Plymouth                                7     On time
## 17:38  Basingstoke                             2     On time
## 17:38  London Paddington                       11A   17:43
## 17:42  Birmingham New Street                   13    On time
##        via Coventry                            
## 17:45  Bedwyn                                  3     On time
## 17:46  London Paddington                       11    Delayed
## 17:48  Swindon                                 13    On time
## 17:51  Guildford                               5     On time
## 17:52  Eastleigh                               8B    On time
## 17:54  London Waterloo                         4     On time
## 17:59  Abbey Wood                              14    On time
## 17:59  London Paddington                       10A   18:01
## 18:00  Cheltenham Spa                          8     On time
## 18:05  Bristol Temple Meads                    9     On time
## 18:05  London Paddington                       11    On time
## 18:12  Salisbury                               2     On time
## 18:12  Swansea                                 7     On time
## 18:14  London Paddington                       10    On time
## 18:14  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 18:15  Great Malvern                           9     On time
## 18:17  London Paddington                       11    On time
## 18:21  Guildford                               5     On time
## 18:24  London Waterloo                         4     On time
## 18:25  Didcot Parkway                          12A   On time
## 18:29  Abbey Wood                              14    On time
## 18:29  Plymouth                                7     On time
## 18:35  Plymouth                                9     On time
##        via Bristol                             
## 18:36  London Paddington                       10    On time
## 18:38  Basingstoke                             2     On time
## 18:43  Newbury                                 1     On time
## 18:46  London Paddington                       10    On time
## 18:46  Swindon                                 12    On time
## 18:51  Guildford                               5     On time
## 18:52  Eastleigh                               7     On time
## 18:54  London Waterloo                         4     On time
## 18:59  Abbey Wood                              14    On time
## 18:59  London Paddington                       10    On time
## 19:01  Plymouth                                -     Cancelled
## 19:02  Bristol Temple Meads                    9     On time
## 19:05  London Paddington                       -     Cancelled
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
```
