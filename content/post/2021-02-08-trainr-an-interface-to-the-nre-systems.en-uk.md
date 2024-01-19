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

## Example (Last rendered on 2024-01-19 21:04)

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
## Reading (RDG) Station Board on 2024-01-19 21:04:42.375423
## Time   From                                    Plat  Expected
## 20:44  Swansea                                 10    21:04
## 20:57  Gatwick Airport                         5     21:10
## 20:59  Great Malvern                           11A   21:01
## 21:00  Penzance                                10    21:19
## 21:03  Didcot Parkway                          14A   21:26
## 21:04  Basingstoke                             2     On time
## 21:07  Bournemouth                             7B    21:04
## 21:09  Bristol Temple Meads                    10    21:13
## 21:11  Abbey Wood                              14    On time
## 21:11  London Paddington                       9     On time
## 21:13  London Waterloo                         6     On time
## 21:14  London Paddington                       13B   On time
## 21:16  London Paddington                       9B    On time
## 21:21  Bedwyn                                  11A   21:23
## 21:24  Oxford                                  10A   On time
## 21:25  London Paddington                       9     On time
## 21:27  Basingstoke                             2     On time
## 21:27  London Paddington                       7     On time
## 21:29  Didcot Parkway                          15A   On time
## 21:33  Cheltenham Spa                          10    On time
## 21:34  Gatwick Airport                         14B   On time
## 21:38  Newbury                                 1     On time
## 21:39  Manchester Piccadilly                   7     On time
## 21:41  Abbey Wood                              14    On time
## 21:42  London Waterloo                         4     On time
## 21:44  Carmarthen                              11    21:46
## 21:45  London Paddington                       13B   On time
## 21:45  London Paddington                       9B    On time
## 21:50  Gatwick Airport                         6     On time
## 21:53  Great Malvern                           10A   On time
## 21:54  London Paddington                       9B    On time
## 21:56  Basingstoke                             3     On time
## 22:00  Paignton                                11    22:03
## 22:05  Didcot Parkway                          15A   On time
## 22:09  Abbey Wood                              14    On time
## 22:09  Taunton                                 10    On time
## 22:11  London Paddington                       9     On time
## 22:14  London Paddington                       12B   On time
## 22:16  London Paddington                       9B    On time
## 22:20  Newbury                                 11A   On time
## 22:25  Oxford                                  12A   On time
## 22:27  London Paddington                       9     On time
## 22:32  Cheltenham Spa                          10    On time
## 22:33  Shalford                                13B   On time
## 22:35  Newbury                                 1     On time
## 22:38  Manchester Piccadilly                   7     On time
## 22:39  Basingstoke                             2     On time
## 22:40  Abbey Wood                              14    On time
## 22:41  London Paddington                       9     On time
## 22:42  London Waterloo                         6     On time
## 22:43  Swansea                                 10A   On time
## 22:45  London Paddington                       12B   On time
## 22:46  Worcester Foregate Street               13A   On time
## 22:51  London Paddington                       9     On time
## 22:53  London Paddington                       7B    On time
## 22:59  Didcot Parkway                          13    On time
## 23:03  Basingstoke                             2     On time
## 21:10  Heathrow Airport T3 (Bus)               BUS   On time
## 21:40  Heathrow Airport T3 (Bus)               BUS   On time
## 22:10  Heathrow Airport T3 (Bus)               BUS   On time
## 22:40  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-19 21:04:45.99743
## Time   To                                      Plat  Expected
## 20:47  London Paddington                       10    21:05
## 21:01  London Paddington                       11A   21:03
## 21:03  London Paddington                       10    21:20
## 21:04  London Paddington                       14A   21:27
## 21:05  Newbury                                 1     On time
## 21:09  London Waterloo                         4     On time
## 21:11  London Paddington                       10    21:14
## 21:13  Swansea                                 9     On time
## 21:14  Birmingham New Street                   7B    On time
##        via Coventry                            
## 21:18  Great Malvern                           9B    On time
## 21:22  Basingstoke                             2     On time
## 21:23  Didcot Parkway                          13B   On time
## 21:23  London Paddington                       11A   21:23
## 21:26  London Paddington                       10A   On time
## 21:27  Bristol Temple Meads                    9     On time
## 21:29  Plymouth                                7     On time
## 21:30  Abbey Wood                              14    On time
## 21:34  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:38  London Paddington                       15A   On time
## 21:39  London Waterloo                         6     On time
## 21:43  London Paddington                       10    On time
## 21:46  Didcot Parkway                          13B   On time
## 21:46  London Paddington                       11    21:46
## 21:48  Oxford                                  9B    On time
## 21:52  Bournemouth                             7     On time
## 21:56  Cheltenham Spa                          9B    On time
## 21:56  London Paddington                       10A   On time
## 21:59  Abbey Wood                              14    On time
## 22:05  Basingstoke                             3     On time
## 22:05  London Paddington                       11    On time
## 22:09  London Waterloo                         4     On time
## 22:10  Newbury                                 1     On time
## 22:12  London Paddington                       15A   On time
## 22:12  London Paddington                       10    On time
## 22:13  Swansea                                 9     On time
## 22:18  Didcot Parkway                          12B   On time
## 22:18  Worcester Shrub Hill                    9B    On time
## 22:20  London Paddington                       11A   On time
## 22:26  Basingstoke                             2     On time
## 22:26  London Paddington                       12A   On time
## 22:28  Abbey Wood                              14    On time
## 22:28  Bristol Temple Meads                    9     On time
## 22:34  Shalford                                6     On time
## 22:35  London Paddington                       10    On time
## 22:40  London Paddington                       15A   On time
## 22:43  Oxford                                  9     On time
## 22:46  London Paddington                       10A   On time
## 22:47  Didcot Parkway                          12B   On time
## 22:49  Southampton Central                     7     On time
## 22:51  London Paddington                       13A   On time
## 22:52  Basingstoke                             2     On time
## 22:55  Bristol Temple Meads                    9     On time
## 22:58  Abbey Wood                              14    On time
## 22:59  Bedwyn                                  7B    On time
## 21:05  Heathrow Airport T3 (Bus)               BUS   On time
## 22:05  Heathrow Airport T3 (Bus)               BUS   On time
```
