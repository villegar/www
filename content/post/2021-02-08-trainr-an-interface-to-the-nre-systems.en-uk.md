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

## Example (Last rendered on 2024-01-14 21:04)

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
## Reading (RDG) Station Board on 2024-01-14 21:04:06.720736
## Time   From                                    Plat  Expected
## 20:50  Plymouth                                11    20:55
## 20:58  Penzance                                12    21:07
## 20:59  Great Malvern                           10A   20:56
## 21:00  London Paddington                       9     21:17
## 21:02  Ascot                                   4     21:04
## 21:04  Bournemouth                             8B    20:50
## 21:05  Abbey Wood                              14    On time
## 21:10  Redhill                                 15B   On time
## 21:13  London Paddington                       7     21:18
## 21:15  London Paddington                       13    On time
## 21:19  Bedwyn                                  1     21:23
## 21:23  Taunton                                 11    21:34
## 21:28  London Paddington                       7B    On time
## 21:32  Ascot                                   6     On time
## 21:35  Abbey Wood                              13    On time
## 21:35  Didcot Parkway                          15    On time
## 21:39  Manchester Piccadilly                   8B    On time
## 21:42  Gatwick Airport                         14    On time
## 21:43  London Paddington                       7     On time
## 21:50  Swansea                                 10    On time
## 21:58  London Paddington                       8B    On time
## 22:00  Great Malvern                           9B    On time
## 22:02  Ascot                                   6     On time
## 22:04  Plymouth                                11    On time
## 22:05  Abbey Wood                              14    On time
## 22:11  Redhill                                 4     On time
## 22:13  London Paddington                       7     On time
## 22:15  London Paddington                       13    On time
## 22:24  Newbury                                 1     On time
## 22:27  Didcot Parkway                          7     On time
## 22:28  London Paddington                       9     On time
## 22:29  Henley-on-Thames                        13A   On time
## 22:35  Bristol Temple Meads                    11    On time
## 22:36  Abbey Wood                              14    On time
## 22:39  Manchester Piccadilly                   8     On time
## 22:39  Swansea                                 10A   On time
## 22:41  London Paddington                       7     On time
## 22:44  Gatwick Airport                         15B   On time
## 22:50  Great Malvern                           10A   On time
## 22:52  Penzance                                11    On time
## 23:02  Ascot                                   6     On time
## 21:10  Heathrow Airport T3 (Bus)               BUS   On time
## 21:15  Swindon                                 BUS   On time
## 21:16  Bramley (Hampshire)                     BUS   On time
## 21:40  Heathrow Airport T3 (Bus)               BUS   On time
## 21:45  Swindon                                 BUS   On time
## 22:10  Heathrow Airport T3 (Bus)               BUS   On time
## 22:15  Swindon                                 BUS   On time
## 22:16  Basingstoke                             BUS   On time
## 22:40  Heathrow Airport T3 (Bus)               BUS   On time
## 22:45  Swindon                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-14 21:04:08.352727
## Time   To                                      Plat  Expected
## 21:05  London Paddington                       11    On time
## 21:08  London Paddington                       12    On time
## 21:12  Birmingham New Street                   8B    On time
##        via Coventry                            
## 21:13  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:14  Worcester Shrub Hill                    9     21:26
## 21:15  London Paddington                       10A   On time
## 21:20  Bristol Parkway                         7     On time
## 21:20  Didcot Parkway                          13    On time
## 21:29  Abbey Wood                              14    On time
## 21:29  Exeter St Davids                        7B    On time
## 21:36  London Paddington                       11    On time
## 21:37  London Paddington                       15    On time
## 21:45  Bristol Temple Meads                    7     On time
## 21:48  Bedwyn                                  1     On time
## 21:49  Southampton Central                     8B    On time
## 21:53  Ascot                                   6     On time
## 21:59  Ealing Broadway                         13    On time
## 22:00  Oxford                                  8B    On time
## 22:05  London Paddington                       10    On time
## 22:08  London Paddington                       9B    On time
## 22:11  London Paddington                       11    On time
## 22:14  Swansea                                 7     On time
## 22:18  Guildford                               4     On time
## 22:20  Didcot Parkway                          13    On time
## 22:28  London Paddington                       7     On time
## 22:30  Worcester Shrub Hill                    9     On time
## 22:31  Ealing Broadway                         14    On time
## 22:42  Bristol Temple Meads                    7     On time
## 22:42  London Paddington                       11    On time
## 22:45  London Paddington                       10A   On time
## 22:48  Newbury                                 1     On time
## 22:53  Ascot                                   6     On time
## 22:54  London Paddington                       11    On time
## 22:55  London Paddington                       10A   On time
## 22:58  Ealing Broadway                         14    On time
## 21:05  Heathrow Airport T3 (Bus)               BUS   On time
## 21:05  Swindon                                 BUS   On time
## 21:37  Bramley (Hampshire)                     BUS   On time
## 21:45  Swindon                                 BUS   On time
## 21:52  Winchester                              BUS   On time
## 22:05  Heathrow Airport T3 (Bus)               BUS   On time
## 22:05  Swindon                                 BUS   On time
## 22:50  Swindon                                 BUS   On time
```
