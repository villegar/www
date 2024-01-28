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

## Example (Last rendered on 2024-01-28 11:05)

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
## Reading (RDG) Station Board on 2024-01-28 11:05:30.710588
## Time   From                                    Plat  Expected
## 11:00  London Paddington                       7     11:02
## 11:02  Swansea                                 10    On time
## 11:05  London Paddington                       14    11:08
## 11:06  Southampton Central                     8     11:03
## 11:09  Bristol Temple Meads                    11    On time
## 11:14  London Paddington                       9B    On time
## 11:19  Bedwyn                                  1     On time
## 11:28  London Paddington                       7     On time
## 11:34  Basingstoke                             2     On time
## 11:35  Abbey Wood                              14    On time
## 11:35  Didcot Parkway                          12    On time
## 11:36  Totnes                                  11    On time
## 11:39  Manchester Piccadilly                   7B    On time
## 11:40  Swansea                                 10    11:48
## 11:45  London Paddington                       13    On time
## 11:47  Salisbury                               2     On time
## 11:57  Great Malvern                           10A   On time
## 11:58  London Paddington                       9     On time
## 11:58  Totnes                                  11    On time
## 12:05  Abbey Wood                              14    On time
## 12:05  Southampton Central                     13B   On time
## 12:09  Bristol Temple Meads                    10    On time
## 12:14  London Paddington                       9     On time
## 12:15  Swindon                                 11    On time
## 12:19  Newbury                                 1     On time
## 12:25  Swansea                                 11    On time
## 12:28  London Paddington                       7     On time
## 12:33  Basingstoke                             2     On time
## 12:35  Abbey Wood                              14    On time
## 12:35  Didcot Parkway                          13    On time
## 12:40  Manchester Piccadilly                   7B    On time
## 12:42  Cheltenham Spa                          10A   On time
## 12:44  London Paddington                       9     On time
## 12:45  London Paddington                       12    On time
## 12:47  Salisbury                               2     On time
## 12:53  Penzance                                11    On time
## 12:58  London Paddington                       9     On time
## 13:00  London Paddington                       7     On time
## 11:04  Bracknell                               BUS   On time
## 11:15  Heathrow Airport T3 (Bus)               BUS   On time
## 11:17  Bracknell                               BUS   On time
## 11:32  North Camp                              BUS   On time
## 11:34  Bracknell                               BUS   On time
## 11:45  Heathrow Airport T3 (Bus)               BUS   On time
## 11:47  Bracknell                               BUS   On time
## 12:04  Bracknell                               BUS   On time
## 12:15  Heathrow Airport T3 (Bus)               BUS   On time
## 12:17  Bracknell                               BUS   On time
## 12:20  North Camp                              BUS   On time
## 12:34  Bracknell                               BUS   On time
## 12:37  North Camp                              BUS   On time
## 12:45  Heathrow Airport T3 (Bus)               BUS   On time
## 12:47  Bracknell                               BUS   On time
## 13:04  Bracknell                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-28 11:05:32.767079
## Time   To                                      Plat  Expected
## 11:01  Paignton                                7     11:04
## 11:05  London Paddington                       10    On time
## 11:12  Salisbury                               -     Cancelled
## 11:13  London Paddington                       11    On time
## 11:14  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 11:15  Great Malvern                           9B    On time
## 11:17  London Paddington                       15    On time
## 11:25  Didcot Parkway                          13    On time
## 11:29  Abbey Wood                              14    On time
## 11:29  Plymouth                                7     On time
## 11:37  London Paddington                       11    On time
## 11:38  Basingstoke                             2     On time
## 11:43  Bedwyn                                  1     On time
## 11:44  London Paddington                       10    11:49
## 11:46  Swindon                                 13    On time
## 11:52  Carmarthen                              9     Delayed
## 11:52  Southampton Central                     7B    On time
## 11:59  Abbey Wood                              14    On time
## 11:59  London Paddington                       10A   On time
## 12:02  Bristol Temple Meads                    9     On time
## 12:05  London Paddington                       11    On time
## 12:12  Salisbury                               2     On time
## 12:14  London Paddington                       10    On time
## 12:14  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 12:15  Hereford                                9     On time
## 12:17  London Paddington                       11    On time
## 12:25  Didcot Parkway                          12    On time
## 12:29  Abbey Wood                              14    On time
## 12:29  Penzance                                7     On time
## 12:36  London Paddington                       11    On time
## 12:38  Basingstoke                             2     On time
## 12:43  Newbury                                 1     On time
## 12:44  London Paddington                       10A   On time
## 12:46  Swindon                                 12    On time
## 12:52  Southampton Central                     7B    On time
## 12:52  Swansea                                 9     On time
## 12:59  Abbey Wood                              14    On time
## 12:59  London Paddington                       11    On time
## 13:01  Paignton                                7     On time
## 13:02  Bristol Temple Meads                    9     On time
## 11:20  Bracknell                               BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:32  North Camp                              BUS   On time
## 11:33  Bracknell                               BUS   On time
## 11:50  Bracknell                               BUS   On time
## 11:55  North Camp                              BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
## 12:03  Bracknell                               BUS   On time
## 12:20  Bracknell                               BUS   On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:33  Bracknell                               BUS   On time
## 12:38  North Camp                              BUS   On time
## 12:50  Bracknell                               BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
## 13:03  Bracknell                               BUS   On time
```
