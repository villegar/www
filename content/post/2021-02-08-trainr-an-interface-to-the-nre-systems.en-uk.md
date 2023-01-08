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

## Example (Last rendered on 2023-01-08 08:03)

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
## Reading (RDG) Station Board on 2023-01-08 08:03:16
## Time   From                                    Plat  Expected
## 08:06  London Paddington                       14    On time
## 08:20  London Paddington                       7B    On time
## 08:23  London Paddington                       13    On time
## 08:26  London Paddington                       7     On time
## 08:32  Ascot                                   6     On time
## 08:32  Basingstoke                             2     On time
## 08:38  London Paddington                       7     On time
## 08:40  London Paddington                       14    On time
## 08:44  Basingstoke                             1     On time
## 08:58  Ascot                                   4     On time
## 09:03  London Paddington                       14    On time
## 09:05  Bristol Temple Meads                    11    On time
## 09:09  London Paddington                       9     On time
## 09:14  London Paddington                       7     On time
## 09:15  London Paddington                       12    On time
## 09:22  Newbury                                 3     On time
## 09:25  London Paddington                       7     On time
## 09:32  Basingstoke                             2     On time
## 09:33  London Paddington                       14    On time
## 09:38  London Paddington                       7     On time
## 09:41  Redhill                                 13    On time
## 09:47  Salisbury                               1     On time
## 09:58  Virginia Water                          -     On time
## 10:00  London Paddington                       8     On time
## 08:27  Heathrow Central Bus Stn                BUS   On time
## 08:58  Chippenham                              BUS   On time
## 09:04  Heathrow Central Bus Stn                BUS   On time
## 09:18  Oxford                                  BUS   On time
## 09:34  Heathrow Central Bus Stn                BUS   On time
## 09:41  Didcot Parkway                          BUS   On time
## 09:58  Chippenham                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-01-08 08:03:18
## Time   To                                      Plat  Expected
## 08:06  Newbury                                 12B   On time
## 08:11  London Paddington                       13A   On time
## 08:21  Gatwick Airport                         15    On time
##        via Guildford                           
## 08:21  Penzance                                7B    On time
## 08:24  London Paddington                       14    On time
## 08:28  Swansea                                 7     On time
## 08:34  Bedwyn                                  12    On time
## 08:37  Basingstoke                             2     On time
## 08:40  Redhill                                 15    On time
## 08:48  Exeter St Davids                        7     On time
##        via Bristol                             
## 08:51  London Waterloo                         6     On time
## 08:54  Abbey Wood                              14    On time
## 09:10  Ealing Broadway                         13    On time
## 09:10  London Paddington                       11    On time
## 09:12  Salisbury                               1     On time
## 09:18  Penzance                                7     On time
## 09:21  Gatwick Airport                         13    On time
##        via Guildford                           
## 09:24  Abbey Wood                              14    On time
## 09:24  Virginia Water                          4     On time
## 09:28  Carmarthen                              7     On time
## 09:31  London Paddington                       9     On time
## 09:37  Basingstoke                             2     On time
## 09:41  Redhill                                 6     On time
## 09:42  Bristol Temple Meads                    7     On time
## 09:45  Bedwyn                                  12    On time
## 09:51  London Waterloo                         4     On time
## 09:52  Bournemouth                             8     On time
## 09:54  Abbey Wood                              14    On time
## 09:55  Didcot Parkway                          12    On time
## 10:02  Oxford                                  8     On time
## 08:07  Swindon                                 BUS   On time
## 08:20  Chippenham                              BUS   On time
## 08:30  Heathrow Airport T3 (Bus)               BUS   On time
## 08:36  Didcot Parkway                          BUS   On time
## 08:45  Oxford                                  BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
## 09:05  Swindon                                 BUS   On time
## 09:18  Chippenham                              BUS   On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
```
