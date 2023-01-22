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

## Example (Last rendered on 2023-01-22 20:04)

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
## Reading (RDG) Station Board on 2023-01-22 20:04:01
## Time   From                                    Plat  Expected
## 19:56  Hereford                                10    20:04
## 20:07  London Paddington                       8     On time
## 20:10  Exeter St Davids                        10    On time
## 20:12  London Paddington                       9B    20:14
## 20:13  Didcot Parkway                          15    20:16
## 20:14  London Paddington                       8B    On time
## 20:20  Newbury                                 1     On time
## 20:27  London Paddington                       7     On time
## 20:28  Abbey Wood                              14    On time
## 20:32  Basingstoke                             2     On time
## 20:39  Manchester Piccadilly                   8     On time
## 20:41  Plymouth                                11    On time
## 20:47  London Paddington                       9B    On time
## 20:51  Swansea                                 10    On time
## 20:54  London Paddington                       9     On time
## 20:58  Abbey Wood                              14    On time
## 20:58  Great Malvern                           10A   On time
## 20:58  Penzance                                11    On time
## 21:06  Bournemouth                             8     On time
## 21:07  London Paddington                       9     On time
## 21:11  Taunton                                 10    On time
## 21:12  London Paddington                       12B   On time
## 21:13  Didcot Parkway                          13    On time
## 21:13  London Paddington                       -     Cancelled
## 21:19  Bedwyn                                  1     On time
## 21:26  London Paddington                       7     On time
## 21:28  Abbey Wood                              14    On time
## 21:32  Basingstoke                             2     On time
## 21:39  Manchester Piccadilly                   8     On time
## 21:48  Swansea                                 10    On time
## 21:53  Great Malvern                           11A   On time
## 21:54  London Paddington                       9     On time
## 21:58  Abbey Wood                              14    On time
## 20:04  Guildford                               BUS   On time
## 20:06  Ascot                                   BUS   On time
## 20:21  Ascot                                   BUS   On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:36  Ascot                                   BUS   On time
## 20:38  Guildford                               BUS   On time
## 20:51  Ascot                                   BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
## 21:06  Ascot                                   BUS   On time
## 21:18  Guildford                               BUS   On time
## 21:21  Ascot                                   BUS   On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
## 21:36  Ascot                                   BUS   On time
## 21:51  Ascot                                   BUS   On time
## 22:00  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-01-22 20:04:04
## Time   To                                      Plat  Expected
## 20:02  London Paddington                       10    20:05
## 20:09  Swansea                                 8     On time
## 20:14  Ealing Broadway                         15    20:17
## 20:14  Great Malvern                           9B    20:15
## 20:15  London Paddington                       10    On time
## 20:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 20:24  Abbey Wood                              14    On time
## 20:25  Didcot Parkway                          8B    On time
## 20:28  Plymouth                                7     On time
## 20:37  Basingstoke                             2     On time
## 20:43  Newbury                                 1     On time
## 20:45  London Paddington                       11    On time
## 20:49  Oxford                                  9B    On time
## 20:52  Bournemouth                             8     On time
## 20:54  Abbey Wood                              14    On time
## 20:55  London Paddington                       10    On time
## 20:56  Weston-super-Mare                       9     On time
## 21:00  London Paddington                       11    On time
## 21:02  London Paddington                       10A   On time
## 21:09  Swansea                                 9     On time
## 21:12  Birmingham New Street                   8     On time
##        via Coventry                            
## 21:14  Ealing Broadway                         13    On time
## 21:15  Didcot Parkway                          12B   On time
## 21:15  London Paddington                       10    On time
## 21:15  Worcester Shrub Hill                    -     Cancelled
## 21:24  Ealing Broadway                         14    On time
## 21:28  Exeter St Davids                        7     On time
## 21:37  Basingstoke                             2     On time
## 21:43  Bedwyn                                  1     On time
## 21:49  London Paddington                       10    On time
## 21:52  Southampton Central                     8     On time
## 21:53  Ealing Broadway                         14    On time
## 21:55  London Paddington                       11A   On time
## 21:56  Bristol Temple Meads                    9     On time
## 20:12  Guildford                               BUS   On time
## 20:16  Ascot                                   BUS   On time
## 20:31  Ascot                                   BUS   On time
## 20:35  Guildford                               BUS   On time
## 20:46  Ascot                                   BUS   On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
## 21:01  Ascot                                   BUS   On time
## 21:16  Ascot                                   BUS   On time
## 21:30  Guildford                               BUS   On time
## 21:31  Ascot                                   BUS   On time
## 21:46  Ascot                                   BUS   On time
## 21:58  Guildford                               BUS   On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
## 22:01  Ascot                                   BUS   On time
```
