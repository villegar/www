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

## Example (Last rendered on 2022-01-09 12:03)

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
## Reading (RDG) Station Board on 2022-01-09 12:03:36
## Time   From                                    Plat  Expected
## 11:39  Plymouth                                11    12:15
## 11:58  Plymouth                                11    12:20
## 12:10  Didcot Parkway                          15    12:12
## 12:12  London Paddington                       9B    On time
## 12:13  London Paddington                       14    On time
## 12:13  London Paddington                       7     12:18
## 12:15  London Paddington                       12    12:18
## 12:21  Swansea                                 11    12:30
## 12:31  London Paddington                       7     On time
## 12:33  Basingstoke                             2     On time
## 12:38  Newbury                                 7B    On time
## 12:39  Manchester Piccadilly                   12    On time
## 12:41  Bristol Temple Meads                    11    On time
## 12:43  London Paddington                       14    12:54
## 12:47  Salisbury                               1     On time
## 12:56  Great Malvern                           10A   On time
## 12:58  Penzance                                11    On time
## 13:00  London Paddington                       -     Cancelled
## 13:06  Bournemouth                             8     On time
## 13:10  Didcot Parkway                          15    On time
## 13:12  London Paddington                       9     On time
## 13:13  London Paddington                       7B    On time
## 13:13  London Paddington                       14    On time
## 13:15  London Paddington                       13    On time
## 13:18  Swansea                                 11    13:24
## 13:27  London Paddington                       7     On time
## 13:28  Bedwyn                                  1     On time
## 13:31  London Paddington                       8     On time
## 13:33  Basingstoke                             2     On time
## 13:36  Bristol Temple Meads                    10    On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:43  London Paddington                       14    On time
## 13:47  Salisbury                               1     On time
## 13:48  Exeter St Davids                        11A   13:50
## 13:48  London Paddington                       9     On time
## 13:56  Great Malvern                           10    On time
## 13:58  Penzance                                11    On time
## 12:02  Guildford                               BUS   On time
## 12:03  Bracknell                               BUS   On time
## 12:10  Swindon                                 BUS   On time
## 12:19  Bracknell                               BUS   On time
## 12:21  Heathrow Central Bus Stn                BUS   On time
## 12:33  Bracknell                               BUS   On time
## 12:43  Swindon                                 BUS   On time
## 12:45  Guildford                               BUS   On time
## 12:49  Bracknell                               BUS   On time
## 13:00  Swindon                                 BUS   On time
## 13:03  Bracknell                               BUS   On time
## 13:18  Guildford                               BUS   On time
## 13:19  Bracknell                               BUS   On time
## 13:21  Heathrow Central Bus Stn                BUS   On time
## 13:30  Swindon                                 BUS   On time
## 13:33  Bracknell                               BUS   On time
## 13:49  Bracknell                               BUS   On time
## 14:00  Swindon                                 BUS   On time
## 14:02  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-09 12:03:40
## Time   To                                      Plat  Expected
## 11:50  London Paddington                       11    12:16
## 11:52  Ealing Broadway                         14    Delayed
## 11:59  London Paddington                       11    12:21
## 12:12  London Paddington                       15    12:13
## 12:12  Salisbury                               1     On time
## 12:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 12:18  Bristol Temple Meads                    7     12:18
## 12:18  Hereford                                9B    On time
## 12:26  Didcot Parkway                          12    On time
## 12:27  Ealing Broadway                         14    On time
## 12:28  Penzance                                8     12:35
## 12:30  London Paddington                       11    12:30
## 12:33  Swansea                                 7     On time
## 12:38  Basingstoke                             2     On time
## 12:44  Newbury                                 7B    On time
## 12:50  London Paddington                       11    On time
## 12:57  Ealing Broadway                         14    On time
## 12:59  London Paddington                       11    On time
## 13:01  Exeter St Davids                        -     Cancelled
## 13:01  London Paddington                       10A   On time
## 13:12  London Paddington                       15    On time
## 13:12  Yeovil Pen Mill                         1     On time
## 13:14  Great Malvern                           9     On time
## 13:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 13:18  Bristol Temple Meads                    7B    On time
## 13:20  London Paddington                       11    13:25
## 13:26  Didcot Parkway                          13    On time
## 13:27  Ealing Broadway                         14    On time
## 13:29  Plymouth                                7     On time
## 13:33  Carmarthen                              8     On time
## 13:38  Basingstoke                             2     On time
## 13:44  Bedwyn                                  1     On time
## 13:45  London Paddington                       10    On time
## 13:50  London Paddington                       11A   13:50
## 13:50  Oxford                                  9     On time
## 13:52  Bournemouth                             7     On time
## 13:57  Ealing Broadway                         14    On time
## 13:59  London Paddington                       11    On time
## 14:01  London Paddington                       10    On time
## 12:05  Swindon                                 BUS   On time
## 12:16  Bracknell                               BUS   On time
## 12:25  Swindon                                 BUS   On time
## 12:31  Bracknell                               BUS   On time
## 12:35  Guildford                               BUS   On time
## 12:46  Bracknell                               BUS   On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
## 13:01  Bracknell                               BUS   On time
## 13:05  Swindon                                 BUS   On time
## 13:08  Guildford                               BUS   On time
## 13:16  Bracknell                               BUS   On time
## 13:25  Swindon                                 BUS   On time
## 13:31  Bracknell                               BUS   On time
## 13:46  Bracknell                               BUS   On time
## 13:46  Guildford                               BUS   On time
## 14:00  Heathrow Central Bus Stn                BUS   On time
## 14:01  Bracknell                               BUS   On time
```
