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

## Example (Last rendered on 2022-01-16 12:03)

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
## Reading (RDG) Station Board on 2022-01-16 12:04:01
## Time   From                                    Plat  Expected
## 11:58  Plymouth                                11    12:00
## 12:10  Didcot Parkway                          15    On time
## 12:12  London Paddington                       9     12:15
## 12:13  London Paddington                       7     12:17
## 12:13  London Paddington                       14    On time
## 12:15  London Paddington                       12    12:23
## 12:21  Swansea                                 11    12:56
## 12:27  London Paddington                       7B    On time
## 12:28  Didcot Parkway                          10    On time
## 12:31  London Paddington                       7     On time
## 12:33  Basingstoke                             2     On time
## 12:38  Newbury                                 7B    On time
## 12:41  Bristol Temple Meads                    11    13:01
## 12:43  London Paddington                       14    On time
## 12:47  Oxford                                  9     On time
## 12:47  Salisbury                               1     On time
## 12:50  London Paddington                       8     On time
## 12:58  Penzance                                11    On time
## 13:00  London Paddington                       7     On time
## 13:02  Bournemouth                             8     On time
## 13:08  Great Malvern                           10A   On time
## 13:12  London Paddington                       8     On time
## 13:13  Didcot Parkway                          15    On time
## 13:13  London Paddington                       7     On time
## 13:13  London Paddington                       14    On time
## 13:15  London Paddington                       12    On time
## 13:18  Swansea                                 11    On time
## 13:27  London Paddington                       7     On time
## 13:28  Bedwyn                                  1     On time
## 13:29  Didcot Parkway                          10    On time
## 13:31  London Paddington                       8     On time
## 13:33  Basingstoke                             2     On time
## 13:36  Bristol Temple Meads                    10    On time
## 13:43  London Paddington                       14    On time
## 13:47  Oxford                                  7     On time
## 13:47  Salisbury                               1     On time
## 13:48  Taunton                                 11    On time
## 13:50  London Paddington                       8     On time
## 13:58  Penzance                                11A   On time
## 12:10  Swindon                                 BUS   On time
## 12:14  Bracknell                               BUS   On time
## 12:21  Heathrow Central Bus Stn                BUS   On time
## 12:30  Bracknell                               BUS   On time
## 12:43  Swindon                                 BUS   On time
## 12:44  Bracknell                               BUS   On time
## 12:45  Guildford                               BUS   On time
## 13:00  Bracknell                               BUS   On time
## 13:00  Swindon                                 BUS   On time
## 13:14  Bracknell                               BUS   On time
## 13:18  Guildford                               BUS   On time
## 13:21  Heathrow Central Bus Stn                BUS   On time
## 13:30  Bracknell                               BUS   On time
## 13:30  Swindon                                 BUS   On time
## 13:44  Bracknell                               BUS   On time
## 14:00  Bracknell                               BUS   On time
## 14:00  Swindon                                 BUS   On time
## 14:02  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-16 12:04:06
## Time   To                                      Plat  Expected
## 11:59  London Paddington                       11    12:02
## 12:07  Oxford                                  13    On time
## 12:12  London Paddington                       15    On time
## 12:12  Salisbury                               1     On time
## 12:14  Hereford                                9     12:15
## 12:18  Bristol Temple Meads                    7     12:18
## 12:22  Ealing Broadway                         14    On time
## 12:26  Didcot Parkway                          12    On time
## 12:28  Penzance                                7B    On time
## 12:30  London Paddington                       11    13:06
## 12:32  London Paddington                       10    On time
## 12:33  Swansea                                 7     On time
## 12:38  Basingstoke                             2     On time
## 12:44  Newbury                                 7B    On time
## 12:50  London Paddington                       11    13:02
## 12:52  Didcot Parkway                          8     On time
## 12:52  Ealing Broadway                         14    On time
## 12:59  London Paddington                       11    On time
## 13:01  Exeter St Davids                        7     On time
## 13:07  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 13:10  London Paddington                       10A   On time
## 13:12  Yeovil Pen Mill                         1     On time
## 13:14  Ealing Broadway                         15    On time
## 13:14  Great Malvern                           8     On time
## 13:18  Bristol Temple Meads                    7     On time
## 13:20  London Paddington                       11    On time
## 13:22  Ealing Broadway                         14    On time
## 13:26  Didcot Parkway                          12    On time
## 13:29  Plymouth                                7     On time
## 13:30  London Paddington                       10    On time
## 13:33  Carmarthen                              8     On time
## 13:38  Basingstoke                             2     On time
## 13:44  Bedwyn                                  1     On time
## 13:45  London Paddington                       10    On time
## 13:50  London Paddington                       11    On time
## 13:52  Bournemouth                             7     On time
## 13:52  Didcot Parkway                          8     On time
## 13:52  Ealing Broadway                         14    On time
## 13:59  London Paddington                       11A   On time
## 12:05  Swindon                                 BUS   On time
## 12:06  Bracknell                               BUS   On time
## 12:21  Bracknell                               BUS   On time
## 12:25  Swindon                                 BUS   On time
## 12:35  Guildford                               BUS   On time
## 12:36  Bracknell                               BUS   On time
## 12:51  Bracknell                               BUS   On time
## 13:00  Heathrow Central Bus Stn                BUS   On time
## 13:05  Swindon                                 BUS   On time
## 13:06  Bracknell                               BUS   On time
## 13:08  Guildford                               BUS   On time
## 13:21  Bracknell                               BUS   On time
## 13:25  Swindon                                 BUS   On time
## 13:36  Bracknell                               BUS   On time
## 13:46  Guildford                               BUS   On time
## 13:51  Bracknell                               BUS   On time
## 14:00  Heathrow Central Bus Stn                BUS   On time
```
