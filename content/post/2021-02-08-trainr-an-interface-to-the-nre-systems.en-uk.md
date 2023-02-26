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

## Example (Last rendered on 2023-02-26 18:03)

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
## Reading (RDG) Station Board on 2023-02-26 18:03:18
## Time   From                                    Plat  Expected
## 17:57  Hereford                                11A   18:08
## 17:57  London Paddington                       8B    On time
## 18:06  Plymouth                                10    18:10
## 18:09  London Paddington                       8     18:12
## 18:12  London Paddington                       9     18:14
## 18:13  Didcot Parkway                          14    On time
## 18:13  London Paddington                       12    On time
## 18:14  Plymouth                                11    18:23
## 18:26  Abbey Wood                              14    18:29
## 18:27  London Paddington                       9     On time
## 18:30  Cardiff Central                         13    On time
## 18:32  Basingstoke                             2     On time
## 18:33  Cheltenham Spa                          10A   On time
## 18:39  Manchester Piccadilly                   12    On time
## 18:40  Bristol Temple Meads                    11    On time
## 18:44  Swansea                                 10    On time
## 18:54  London Paddington                       9     On time
## 18:56  Abbey Wood                              14    On time
## 18:56  Great Malvern                           11A   On time
## 19:06  Southampton Central                     7     On time
## 19:09  London Paddington                       8     On time
## 19:10  Taunton                                 10    19:16
## 19:12  London Paddington                       9     On time
## 19:13  Didcot Parkway                          15    On time
## 19:13  London Paddington                       12    On time
## 19:26  Abbey Wood                              14    On time
## 19:27  London Paddington                       9     On time
## 19:28  Penzance                                11    On time
## 19:32  Basingstoke                             2     On time
## 19:39  Manchester Piccadilly                   7B    On time
## 19:49  Swansea                                 11    On time
## 19:54  London Paddington                       9     On time
## 19:56  Hereford                                10    On time
## 19:57  Abbey Wood                              14    On time
## 18:03  Bracknell                               BUS   On time
## 18:04  Guildford                               BUS   On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:08  Bedwyn                                  BUS   On time
## 18:19  Bracknell                               BUS   On time
## 18:33  Bracknell                               BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 18:40  Guildford                               BUS   On time
## 18:46  Newbury                                 BUS   On time
## 18:49  Bracknell                               BUS   On time
## 19:03  Bracknell                               BUS   On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:18  Guildford                               BUS   On time
## 19:19  Bracknell                               BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:33  Bracknell                               BUS   On time
## 19:49  Bracknell                               BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-26 18:03:23
## Time   To                                      Plat  Expected
## 18:00  Cheltenham Spa                          8B    On time
## 18:02  London Paddington                       11A   18:09
## 18:10  Swansea                                 8     18:13
## 18:13  London Paddington                       10    On time
## 18:14  Ealing Broadway                         14    On time
## 18:14  Great Malvern                           9     18:15
## 18:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 18:20  London Paddington                       11    18:24
## 18:22  Abbey Wood                              15    On time
## 18:25  Didcot Parkway                          12    On time
## 18:25  Penzance                                8     On time
## 18:29  Bristol Temple Meads                    9     On time
## 18:35  London Paddington                       10A   On time
## 18:37  Basingstoke                             2     On time
## 18:43  London Paddington                       11    On time
## 18:50  London Paddington                       10    On time
## 18:52  Abbey Wood                              15    On time
## 18:55  Weston-super-Mare                       9     On time
## 19:02  London Paddington                       11A   On time
## 19:10  Swansea                                 8     On time
## 19:13  London Paddington                       10    19:17
## 19:14  Ealing Broadway                         15    On time
## 19:14  Hereford                                9     On time
## 19:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 19:22  Abbey Wood                              15    On time
## 19:25  Didcot Parkway                          12    On time
## 19:25  Plymouth                                8     On time
## 19:29  Bristol Temple Meads                    9     On time
## 19:35  London Paddington                       11    On time
## 19:37  Basingstoke                             2     On time
## 19:40  Swindon                                 13    On time
## 19:50  London Paddington                       11    On time
## 19:52  Abbey Wood                              15    On time
## 19:52  Southampton Central                     7B    On time
## 19:55  Bristol Temple Meads                    9     On time
## 20:02  London Paddington                       10    On time
## 18:05  Bracknell                               BUS   On time
## 18:21  Bracknell                               BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:35  Bracknell                               BUS   On time
## 18:43  Newbury                                 BUS   On time
## 18:45  Guildford                               BUS   On time
## 18:51  Bracknell                               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:05  Bracknell                               BUS   On time
## 19:21  Bracknell                               BUS   On time
## 19:30  Guildford                               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:35  Bracknell                               BUS   On time
## 19:43  Bedwyn                                  BUS   On time
## 19:51  Bracknell                               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
```
