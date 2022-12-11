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

## Example (Last rendered on 2022-12-11 12:04)

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
## Reading (RDG) Station Board on 2022-12-11 12:04:23
## Time   From                                    Plat  Expected
## 11:34  Plymouth                                11    12:26
## 11:58  Plymouth                                11    12:30
## 12:02  Ascot                                   4     On time
## 12:05  London Paddington                       8     On time
## 12:08  Guildford                               6     On time
## 12:09  Bristol Temple Meads                    10    12:16
## 12:10  Didcot Parkway                          15A   On time
## 12:10  London Paddington                       9     12:20
## 12:14  Salisbury                               2     12:28
## 12:19  Newbury                                 1     12:21
## 12:21  London Paddington                       12B   12:23
## 12:25  Oxford                                  10A   On time
## 12:26  London Paddington                       7     On time
## 12:31  Cheltenham Spa                          10A   On time
## 12:32  Ascot                                   4     On time
## 12:32  Basingstoke                             2     On time
## 12:33  Abbey Wood                              14    On time
## 12:38  Guildford                               5     On time
## 12:39  Manchester Piccadilly                   12    On time
## 12:44  Swansea                                 10    On time
## 12:45  London Paddington                       8B    On time
## 12:48  London Paddington                       9     On time
## 12:53  Penzance                                11    13:00
## 12:56  Great Malvern                           10A   On time
## 12:58  London Paddington                       7     On time
## 13:02  Ascot                                   4     On time
## 13:03  Abbey Wood                              14    On time
## 13:05  London Paddington                       9     On time
## 13:06  Southampton Central                     8     On time
## 13:08  Guildford                               6     On time
## 13:09  Weston-super-Mare                       10    On time
## 13:10  Didcot Parkway                          15A   On time
## 13:12  London Paddington                       9B    On time
## 13:14  Salisbury                               2     On time
## 13:19  Bedwyn                                  1     On time
## 13:21  London Paddington                       13B   On time
## 13:25  Oxford                                  10A   On time
## 13:27  London Paddington                       7     On time
## 13:27  Paignton                                11    On time
## 13:32  Ascot                                   4     On time
## 13:32  Basingstoke                             2     On time
## 13:33  Abbey Wood                              14    On time
## 13:38  Guildford                               5     On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:40  Bristol Temple Meads                    11    On time
## 13:43  London Paddington                       8B    On time
## 13:44  Swansea                                 10    On time
## 13:48  London Paddington                       9     On time
## 13:55  Great Malvern                           10A   On time
## 13:58  Penzance                                11    On time
## 14:03  Abbey Wood                              14    On time
## 12:04  Heathrow Central Bus Stn                BUS   On time
## 12:34  Heathrow Central Bus Stn                BUS   On time
## 13:04  Heathrow Central Bus Stn                BUS   On time
## 13:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-11 12:04:28
## Time   To                                      Plat  Expected
## 11:42  London Paddington                       11    12:27
## 12:02  London Paddington                       11    12:31
## 12:09  Swansea                                 8     On time
## 12:13  London Paddington                       10    12:17
## 12:14  Ealing Broadway                         15A   On time
## 12:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 12:18  Hereford                                9     12:21
## 12:21  Guildford                               5     On time
## 12:24  Abbey Wood                              14    On time
## 12:24  Ascot                                   4     On time
## 12:24  Salisbury                               2     12:31
## 12:26  Didcot Parkway                          12B   On time
## 12:26  London Paddington                       10A   On time
## 12:28  Penzance                                7     On time
## 12:32  London Paddington                       10A   On time
## 12:37  Basingstoke                             2     On time
## 12:41  Guildford                               6     On time
## 12:43  Newbury                                 1     On time
## 12:46  London Paddington                       10    On time
## 12:48  Oxford                                  8B    On time
## 12:54  Abbey Wood                              14    On time
## 12:54  Ascot                                   4     On time
## 12:55  London Paddington                       11    13:01
## 12:55  Weston-super-Mare                       9     On time
## 13:01  Paignton                                7     On time
## 13:02  London Paddington                       10A   On time
## 13:09  Swansea                                 9     On time
## 13:12  London Paddington                       10    On time
## 13:14  Ealing Broadway                         15A   On time
## 13:14  Great Malvern                           9B    On time
## 13:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 13:21  Guildford                               5     On time
## 13:24  Abbey Wood                              14    On time
## 13:24  Ascot                                   4     On time
## 13:24  Salisbury                               2     On time
## 13:26  Didcot Parkway                          13B   On time
## 13:26  London Paddington                       10A   On time
## 13:28  Plymouth                                7     On time
## 13:32  London Paddington                       11    On time
## 13:37  Basingstoke                             2     On time
## 13:41  Guildford                               6     On time
## 13:42  London Paddington                       11    On time
## 13:43  Bedwyn                                  1     On time
## 13:46  London Paddington                       10    On time
## 13:48  Oxford                                  8B    On time
## 13:52  Southampton Central                     7     On time
## 13:54  Abbey Wood                              14    On time
## 13:54  Ascot                                   4     On time
## 13:55  Bristol Temple Meads                    9     On time
## 13:55  London Paddington                       10A   On time
## 14:02  London Paddington                       11    On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
```
