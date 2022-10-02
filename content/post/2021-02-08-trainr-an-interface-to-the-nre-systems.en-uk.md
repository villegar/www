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

## Example (Last rendered on 2022-10-02 14:07)

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
## Reading (RDG) Station Board on 2022-10-02 14:07:25
## Time   From                                    Plat  Expected
## 15:05  Bournemouth                             8     On time
## 15:07  London Paddington                       9     On time
## 15:08  Guildford                               -     Cancelled
## 15:09  Bristol Temple Meads                    11    15:13
## 15:13  Didcot Parkway                          15A   On time
## 15:14  London Paddington                       7B    On time
## 15:17  Penzance                                10    15:22
## 15:18  Bedwyn                                  3     15:20
## 15:22  London Paddington                       12B   On time
## 15:25  London Paddington                       9     On time
## 15:32  Ascot                                   4     On time
## 15:33  Basingstoke                             2     On time
## 15:33  London Paddington                       14    On time
## 15:38  Guildford                               -     Cancelled
## 15:39  Didcot Parkway                          7     On time
## 15:40  Swindon                                 11A   On time
## 15:46  Swansea                                 11A   On time
## 15:47  Salisbury                               1     On time
## 15:53  London Paddington                       9     On time
## 16:00  Didcot Parkway                          11A   On time
## 16:02  Ascot                                   4     On time
## 16:03  London Paddington                       14    On time
## 16:08  Guildford                               -     Cancelled
## 16:10  Bristol Temple Meads                    10    On time
## 16:12  Newbury                                 3     On time
## 16:13  Didcot Parkway                          15A   On time
## 16:14  London Paddington                       7B    On time
## 16:15  Exeter St Davids                        11    On time
## 16:22  London Paddington                       12B   On time
## 16:25  London Paddington                       9     On time
## 16:32  Ascot                                   4     On time
## 16:33  Basingstoke                             2     On time
## 16:33  London Paddington                       14    On time
## 16:38  Guildford                               -     Cancelled
## 16:39  Didcot Parkway                          13    On time
## 16:40  Swindon                                 11A   On time
## 16:44  Swansea                                 10    On time
## 16:47  Salisbury                               1     On time
## 16:53  London Paddington                       9     On time
## 17:00  Didcot Parkway                          11    On time
## 17:02  Ascot                                   4     On time
## 17:03  London Paddington                       14    On time
## 17:04  London Paddington                       7     On time
## 15:45  Heathrow Central Bus Stn                BUS   On time
## 16:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-10-02 14:07:29
## Time   To                                      Plat  Expected
## 15:06  Plymouth                                7     On time
## 15:10  Bristol Parkway                         9     On time
## 15:12  London Paddington                       11    15:14
## 15:12  Salisbury                               1     On time
## 15:14  Ealing Broadway                         15A   On time
## 15:15  Didcot Parkway                          8     On time
## 15:20  Didcot Parkway                          7B    On time
## 15:21  Guildford                               -     Cancelled
## 15:22  London Paddington                       10    15:22
## 15:24  Ascot                                   4     On time
## 15:24  Ealing Broadway                         14    On time
## 15:26  Didcot Parkway                          12B   On time
## 15:26  Swindon                                 9     On time
## 15:38  Basingstoke                             2     On time
## 15:41  Guildford                               -     Cancelled
## 15:41  London Paddington                       11A   On time
## 15:43  Bedwyn                                  3     On time
## 15:47  London Paddington                       11A   On time
## 15:52  Bournemouth                             7     On time
## 15:54  Ascot                                   4     On time
## 15:54  Ealing Broadway                         14    On time
## 15:55  Bristol Temple Meads                    9     On time
## 16:03  London Paddington                       11A   On time
## 16:06  Penzance                                7     On time
## 16:10  Swansea                                 9     On time
## 16:12  London Paddington                       10    On time
## 16:12  Salisbury                               1     On time
## 16:14  Ealing Broadway                         15A   On time
## 16:15  Didcot Parkway                          13    On time
## 16:20  Didcot Parkway                          7B    On time
## 16:21  Guildford                               -     Delayed
## 16:22  London Paddington                       11    On time
## 16:24  Ascot                                   4     On time
## 16:24  Ealing Broadway                         14    On time
## 16:26  Didcot Parkway                          12B   On time
## 16:26  Swindon                                 9     On time
## 16:38  Basingstoke                             2     On time
## 16:41  Guildford                               -     Delayed
## 16:41  London Paddington                       11A   On time
## 16:43  Newbury                                 3     On time
## 16:47  London Paddington                       10    On time
## 16:54  Ascot                                   4     On time
## 16:54  Ealing Broadway                         14    On time
## 16:55  Bristol Temple Meads                    9     On time
## 17:03  London Paddington                       11    On time
## 17:06  Penzance                                7     On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
```
