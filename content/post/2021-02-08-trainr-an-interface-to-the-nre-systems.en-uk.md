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

## Example (Last rendered on 2023-04-18 20:04)

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
## Reading (RDG) Station Board on 2023-04-18 20:04:34
## Time   From                                    Plat  Expected
## 21:00  Penzance                                10    21:03
## 21:03  Didcot Parkway                          15A   On time
## 21:04  Basingstoke                             2     21:07
## 21:07  Bournemouth                             8B    On time
## 21:09  Bristol Temple Meads                    10    On time
## 21:10  London Paddington                       14    21:12
## 21:11  London Paddington                       7     On time
## 21:13  Abbey Wood                              13    On time
## 21:13  London Waterloo                         6     On time
## 21:20  London Paddington                       14B   On time
## 21:21  Bedwyn                                  11A   On time
## 21:25  London Paddington                       8     On time
## 21:27  London Paddington                       7B    On time
## 21:28  Basingstoke                             2     On time
## 21:28  Didcot Parkway                          15A   On time
## 21:29  Redhill                                 5     On time
## 21:34  Didcot Parkway                          14A   On time
## 21:37  Cheltenham Spa                          13A   On time
## 21:38  Newbury                                 1     On time
## 21:41  Abbey Wood                              14    21:45
## 21:41  Didcot Parkway                          7B    On time
## 21:42  London Waterloo                         4     On time
## 21:46  London Paddington                       12B   On time
## 21:46  Swansea                                 15    On time
## 21:51  London Paddington                       8     On time
## 21:56  Gatwick Airport                         6     On time
## 21:57  Basingstoke                             3     On time
## 22:00  Paignton                                11A   On time
## 22:07  Didcot Parkway                          15A   On time
## 22:07  London Paddington                       13    On time
## 22:10  Exeter St Davids                        15A   On time
## 22:11  Abbey Wood                              14    On time
## 22:11  London Paddington                       8     On time
## 22:14  Newbury                                 1     On time
## 22:18  London Paddington                       12B   On time
## 22:20  Newbury                                 11A   On time
## 22:26  London Paddington                       8     On time
## 22:33  Cheltenham Spa                          15    On time
## 22:34  Shalford                                14A   On time
## 22:39  Didcot Parkway                          7B    On time
## 22:40  Abbey Wood                              14    On time
## 22:40  Basingstoke                             2     On time
## 22:42  London Waterloo                         6     On time
## 22:45  London Paddington                       12B   On time
## 22:50  Salisbury                               11    On time
## 22:51  Didcot Parkway                          13    On time
## 22:53  Swansea                                 15    On time
## 22:55  London Paddington                       8     On time
## 22:58  London Paddington                       12B   On time
## 23:03  Basingstoke                             2     On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-18 20:04:39
## Time   To                                      Plat  Expected
## 21:03  London Paddington                       10    21:04
## 21:05  Newbury                                 1     On time
## 21:07  Ealing Broadway                         15A   On time
## 21:09  London Waterloo                         4     On time
## 21:11  London Paddington                       10    On time
## 21:14  Didcot Parkway                          8B    On time
## 21:17  Swansea                                 7     On time
## 21:22  Basingstoke                             2     On time
## 21:23  London Paddington                       11A   On time
## 21:27  Abbey Wood                              13    On time
## 21:29  Bristol Temple Meads                    8     On time
## 21:29  Plymouth                                7B    On time
## 21:32  Didcot Parkway                          14B   On time
## 21:34  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:37  London Paddington                       14A   On time
## 21:39  London Waterloo                         6     On time
## 21:40  Ealing Broadway                         15A   On time
## 21:46  London Paddington                       13A   On time
## 21:48  London Paddington                       15    On time
## 21:52  Bournemouth                             7B    On time
## 21:53  Cheltenham Spa                          8     On time
## 21:56  Didcot Parkway                          12B   On time
## 21:57  Abbey Wood                              14    On time
## 22:05  Basingstoke                             3     On time
## 22:05  London Paddington                       11A   On time
## 22:08  Ealing Broadway                         15A   On time
## 22:09  London Waterloo                         4     On time
## 22:10  Newbury                                 1     On time
## 22:13  London Paddington                       15A   On time
## 22:13  Swansea                                 8     On time
## 22:20  London Paddington                       11A   On time
## 22:23  Didcot Parkway                          12B   On time
## 22:27  Abbey Wood                              14    On time
## 22:29  Basingstoke                             2     On time
## 22:30  Plymouth                                8     On time
##        via Bristol                             
## 22:39  London Paddington                       15    On time
## 22:47  Didcot Parkway                          12B   On time
## 22:49  Southampton Central                     7B    On time
## 22:52  Basingstoke                             2     On time
## 22:55  London Paddington                       15    On time
## 22:57  Abbey Wood                              14    On time
## 22:57  Bristol Temple Meads                    8     On time
## 23:01  Bedwyn                                  12B   On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
```
