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

## Example (Last rendered on 2022-03-27 14:03)

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
## Reading (RDG) Station Board on 2022-03-27 14:03:51
## Time   From                                    Plat  Expected
## 14:56  Hereford                                10A   15:38
## 14:57  Penzance                                11    15:12
## 14:59  London Paddington                       7     On time
## 15:01  London Paddington                       9     On time
## 15:05  Ascot                                   4     On time
## 15:07  Eastleigh                               8     On time
## 15:08  Guildford                               6     On time
## 15:09  Weston-super-Mare                       11    15:13
## 15:12  London Paddington                       9B    On time
## 15:13  Didcot Parkway                          15    On time
## 15:14  London Paddington                       12    On time
## 15:14  London Paddington                       14    On time
## 15:18  Bedwyn                                  1     15:21
## 15:26  London Paddington                       7     15:30
## 15:33  Basingstoke                             2     On time
## 15:35  Ascot                                   4     On time
## 15:39  Manchester Piccadilly                   7     On time
## 15:40  Bristol Temple Meads                    -     Cancelled
## 15:41  Exeter St Davids                        -     Cancelled
## 15:44  London Paddington                       14    On time
## 15:46  Cardiff Central                         11    On time
## 15:47  Salisbury                               1     On time
## 15:53  London Paddington                       -     Cancelled
## 15:57  Hereford                                10    On time
## 15:58  Exeter St Davids                        -     Cancelled
## 16:01  London Paddington                       9     On time
## 16:05  Ascot                                   4     On time
## 16:08  Guildford                               6     On time
## 16:09  Bristol Temple Meads                    10    On time
## 16:13  Didcot Parkway                          15    On time
## 16:13  London Paddington                       -     Cancelled
## 16:14  London Paddington                       14    On time
## 16:15  London Paddington                       12    On time
## 16:15  Newbury                                 1     On time
## 16:23  London Paddington                       9     On time
## 16:26  London Paddington                       7     On time
## 16:32  Gloucester                              10    On time
## 16:32  London Paddington                       9     On time
## 16:33  Basingstoke                             2     On time
## 16:35  Ascot                                   4     On time
## 16:39  Manchester Piccadilly                   13    On time
## 16:42  London Paddington                       14    On time
## 16:47  Cardiff Central                         10    On time
## 16:47  Salisbury                               1     On time
## 16:53  London Paddington                       -     Cancelled
## 16:57  Great Malvern                           10    On time
## 16:58  Penzance                                11    On time
## 15:45  Heathrow Central Bus Stn                BUS   On time
## 16:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-03-27 14:03:54
## Time   To                                      Plat  Expected
## 15:00  London Paddington                       11    15:13
## 15:03  Exeter St Davids                        7     On time
## 15:03  London Paddington                       10A   15:39
## 15:09  Cardiff Central                         9     On time
## 15:12  Gillingham (Dorset)                     1     On time
## 15:14  Ealing Broadway                         15    On time
## 15:14  Great Malvern                           9B    On time
## 15:15  London Paddington                       11    15:16
## 15:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 15:19  Ascot                                   4     On time
## 15:23  Didcot Parkway                          12    On time
## 15:25  Bristol Temple Meads                    9     On time
## 15:29  Plymouth                                7     15:31
## 15:30  Ealing Broadway                         14    On time
## 15:38  Basingstoke                             2     On time
## 15:41  Guildford                               6     On time
## 15:43  London Paddington                       -     Cancelled
## 15:44  Bedwyn                                  1     On time
## 15:46  London Paddington                       -     Cancelled
## 15:49  Ascot                                   4     On time
## 15:50  London Paddington                       11    On time
## 15:52  Eastleigh                               7     On time
## 15:55  Taunton                                 -     Cancelled
## 15:58  London Paddington                       -     Cancelled
## 16:00  Ealing Broadway                         14    On time
## 16:03  London Paddington                       10    On time
## 16:09  Cardiff Central                         9     On time
## 16:12  Salisbury                               1     On time
## 16:14  Ealing Broadway                         15    On time
## 16:14  London Paddington                       10    On time
## 16:15  Hereford                                -     Cancelled
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:19  Ascot                                   4     On time
## 16:24  Bristol Temple Meads                    9     On time
## 16:25  Didcot Parkway                          12    On time
## 16:28  Plymouth                                7     On time
## 16:30  Ealing Broadway                         14    On time
## 16:34  Oxford                                  9     On time
## 16:38  Basingstoke                             2     On time
## 16:41  Guildford                               6     On time
## 16:41  London Paddington                       10    On time
## 16:44  Newbury                                 1     On time
## 16:49  Ascot                                   4     On time
## 16:50  London Paddington                       10    On time
## 16:55  Plymouth                                -     Cancelled
##        via Bristol                             
## 16:56  Ealing Broadway                         14    On time
## 16:59  London Paddington                       11    On time
## 17:01  London Paddington                       10    On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
## 17:00  Heathrow Central Bus Stn                BUS   On time
```
