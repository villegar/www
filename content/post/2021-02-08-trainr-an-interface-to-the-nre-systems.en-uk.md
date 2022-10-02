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

## Example (Last rendered on 2022-10-02 16:03)

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
## Reading (RDG) Station Board on 2022-10-02 16:03:59
## Time   From                                    Plat  Expected
## 17:00  Didcot Parkway                          11A   On time
## 17:02  Ascot                                   4     On time
## 17:03  London Paddington                       14    On time
## 17:04  London Paddington                       7     17:01
## 17:05  Bournemouth                             8     17:07
## 17:07  London Paddington                       9     On time
## 17:08  Guildford                               6     17:12
## 17:10  Bristol Temple Meads                    10    17:13
## 17:13  Didcot Parkway                          15A   On time
## 17:14  London Paddington                       7B    On time
## 17:15  Penzance                                11    On time
## 17:20  Bedwyn                                  3     17:22
## 17:22  London Paddington                       12B   On time
## 17:25  London Paddington                       9     On time
## 17:32  Ascot                                   4     On time
## 17:33  Basingstoke                             2     On time
## 17:33  London Paddington                       14    On time
## 17:38  Guildford                               5     On time
## 17:39  Didcot Parkway                          8B    On time
## 17:40  Swindon                                 11A   On time
## 17:45  Carmarthen                              10    On time
## 17:53  London Paddington                       9     On time
## 18:00  Didcot Parkway                          11A   On time
## 18:02  Ascot                                   4     On time
## 18:03  London Paddington                       14    On time
## 18:06  Bristol Temple Meads                    10    On time
## 18:08  Guildford                               -     Cancelled
## 18:13  Didcot Parkway                          15A   On time
## 18:14  London Paddington                       7B    On time
## 18:16  Plymouth                                11    On time
## 18:21  Newbury                                 1     On time
## 18:22  London Paddington                       12B   On time
## 18:28  London Paddington                       9     On time
## 18:30  Cardiff Central                         11A   On time
## 18:32  Ascot                                   4     On time
## 18:33  Basingstoke                             2     On time
## 18:33  London Paddington                       14    On time
## 18:38  Guildford                               5     On time
## 18:39  Didcot Parkway                          12    On time
## 18:39  Swindon                                 10A   On time
## 18:45  Swansea                                 10    On time
## 18:53  London Paddington                       9     On time
## 19:02  Ascot                                   4     On time
## 17:45  Heathrow Central Bus Stn                BUS   On time
## 18:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-02 16:04:02
## Time   To                                      Plat  Expected
## 17:03  London Paddington                       11A   On time
## 17:06  Penzance                                7     On time
## 17:10  Swansea                                 9     On time
## 17:12  London Paddington                       10    17:14
## 17:12  Salisbury                               1     On time
## 17:14  Ealing Broadway                         15A   On time
## 17:15  Didcot Parkway                          8     On time
## 17:20  Didcot Parkway                          7B    On time
## 17:21  Guildford                               5     On time
## 17:22  London Paddington                       11    On time
## 17:24  Ascot                                   4     On time
## 17:24  Ealing Broadway                         14    On time
## 17:26  Didcot Parkway                          12B   On time
## 17:26  Swindon                                 9     On time
## 17:38  Basingstoke                             2     On time
## 17:41  Guildford                               6     On time
## 17:41  London Paddington                       11A   On time
## 17:43  Bedwyn                                  3     On time
## 17:47  London Paddington                       10    On time
## 17:52  Bournemouth                             8B    On time
## 17:54  Ascot                                   4     On time
## 17:54  Ealing Broadway                         14    On time
## 17:55  Bristol Temple Meads                    9     On time
## 18:03  London Paddington                       11A   On time
## 18:09  Swansea                                 9     On time
## 18:12  London Paddington                       10    On time
## 18:14  Ealing Broadway                         15A   On time
## 18:15  Didcot Parkway                          13    On time
## 18:20  Didcot Parkway                          7B    On time
## 18:21  Guildford                               5     On time
## 18:22  London Paddington                       11    On time
## 18:24  Ascot                                   4     On time
## 18:24  Ealing Broadway                         14    On time
## 18:25  Penzance                                8     On time
## 18:26  Didcot Parkway                          12B   On time
## 18:28  Swindon                                 9     On time
## 18:31  London Paddington                       11A   On time
## 18:38  Basingstoke                             2     On time
## 18:41  Guildford                               6     On time
## 18:41  London Paddington                       10A   On time
## 18:43  Newbury                                 1     On time
## 18:47  London Paddington                       10    On time
## 18:54  Ascot                                   4     On time
## 18:54  Ealing Broadway                         14    On time
## 18:55  Bristol Temple Meads                    9     On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
```
