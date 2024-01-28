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

## Example (Last rendered on 2024-01-28 17:08)

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
## Reading (RDG) Station Board on 2024-01-28 17:08:52.931989
## Time   From                                    Plat  Expected
## 16:57  Hereford                                10    17:21
## 17:03  London Paddington                       9     17:28
## 17:05  Abbey Wood                              14    17:09
## 17:07  Southampton Central                     -     Cancelled
## 17:09  Bristol Temple Meads                    10    17:12
## 17:14  London Paddington                       9B    On time
## 17:15  Didcot Parkway                          11    17:20
## 17:20  Bedwyn                                  3     On time
## 17:28  London Paddington                       7     On time
## 17:30  London Paddington                       9     On time
## 17:33  Basingstoke                             2     On time
## 17:35  Abbey Wood                              14    On time
## 17:35  Didcot Parkway                          12    On time
## 17:36  Paignton                                11    On time
## 17:39  Manchester Piccadilly                   8B    On time
## 17:41  Bristol Temple Meads                    10    On time
## 17:44  Carmarthen                              11    On time
## 17:45  London Paddington                       13    On time
## 17:57  Hereford                                10    On time
## 17:58  Plymouth                                11    On time
## 18:03  London Paddington                       7     18:12
## 18:05  Abbey Wood                              14    On time
## 18:06  Southampton Central                     8B    On time
## 18:12  Bristol Temple Meads                    10    On time
## 18:14  London Paddington                       9     On time
## 18:18  Cardiff Central                         11    18:20
## 18:21  Newbury                                 1     On time
## 18:28  London Paddington                       7     On time
## 18:31  Cheltenham Spa                          10    On time
## 18:33  Basingstoke                             2     On time
## 18:35  Abbey Wood                              14    On time
## 18:35  Didcot Parkway                          13    On time
## 18:40  Manchester Piccadilly                   7B    On time
## 18:41  Bristol Temple Meads                    11    On time
## 18:44  Swansea                                 10    On time
## 18:45  London Paddington                       12    On time
## 18:57  Great Malvern                           10    On time
## 18:58  London Paddington                       9     On time
## 18:59  Penzance                                11    On time
## 19:00  London Paddington                       7     On time
## 19:05  Abbey Wood                              14    On time
## 17:17  Bracknell                               BUS   On time
## 17:18  Heathrow Airport T3 (Bus)               BUS   On time
## 17:32  North Camp                              BUS   On time
## 17:34  Bracknell                               BUS   On time
## 17:47  Bracknell                               BUS   On time
## 17:48  Heathrow Airport T3 (Bus)               BUS   On time
## 18:04  Bracknell                               BUS   On time
## 18:17  Bracknell                               BUS   On time
## 18:18  Heathrow Airport T3 (Bus)               BUS   On time
## 18:20  North Camp                              BUS   On time
## 18:34  Bracknell                               BUS   On time
## 18:37  North Camp                              BUS   On time
## 18:47  Bracknell                               BUS   On time
## 18:48  Heathrow Airport T3 (Bus)               BUS   On time
## 19:04  Bracknell                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-28 17:08:57.058991
## Time   To                                      Plat  Expected
## 16:59  London Paddington                       10    17:22
## 17:10  Swansea                                 9     17:29
## 17:12  Salisbury                               2     On time
## 17:14  London Paddington                       10    On time
## 17:14  Manchester Piccadilly                   3     On time
##        via Coventry & Stoke-on-Trent           
## 17:15  Great Malvern                           9B    On time
## 17:17  London Paddington                       11    17:21
## 17:25  Didcot Parkway                          12A   On time
## 17:29  Abbey Wood                              14    On time
## 17:29  Penzance                                7     On time
## 17:32  Bristol Temple Meads                    9     On time
## 17:38  Basingstoke                             2     On time
## 17:38  London Paddington                       11    On time
## 17:42  Newcastle                               13B   On time
##        via Coventry & Doncaster                
## 17:43  London Paddington                       10    On time
## 17:45  Bedwyn                                  3     On time
## 17:46  London Paddington                       11    On time
## 17:48  Swindon                                 13    On time
## 17:52  Southampton Central                     8B    On time
## 17:59  Abbey Wood                              14    On time
## 17:59  London Paddington                       10    On time
## 18:00  Cheltenham Spa                          8     On time
## 18:05  London Paddington                       11    On time
## 18:12  Swansea                                 7     On time
## 18:14  London Paddington                       10    On time
## 18:14  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 18:15  Great Malvern                           9     On time
## 18:19  London Paddington                       11    18:21
## 18:25  Didcot Parkway                          12    On time
## 18:29  Abbey Wood                              14    On time
## 18:29  Penzance                                7     On time
## 18:35  Bristol Temple Meads                    9     On time
## 18:36  London Paddington                       10    On time
## 18:38  Basingstoke                             2     On time
## 18:43  London Paddington                       11    On time
## 18:43  Newbury                                 1     On time
## 18:46  London Paddington                       10    On time
## 18:46  Swindon                                 12    On time
## 18:52  Bournemouth                             7B    On time
## 18:59  Abbey Wood                              14    On time
## 18:59  London Paddington                       10    On time
## 19:01  Plymouth                                7     On time
## 19:02  Bristol Temple Meads                    9     On time
## 19:05  London Paddington                       11    On time
## 17:20  Bracknell                               BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:32  North Camp                              BUS   On time
## 17:33  Bracknell                               BUS   On time
## 17:50  Bracknell                               BUS   On time
## 17:55  North Camp                              BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:03  Bracknell                               BUS   On time
## 18:20  Bracknell                               BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:33  Bracknell                               BUS   On time
## 18:38  North Camp                              BUS   On time
## 18:50  Bracknell                               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:03  Bracknell                               BUS   On time
```
