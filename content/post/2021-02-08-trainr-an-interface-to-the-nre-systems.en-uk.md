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

## Example (Last rendered on 2022-03-27 16:04)

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
## Reading (RDG) Station Board on 2022-03-27 16:04:11
## Time   From                                    Plat  Expected
## 16:57  Great Malvern                           11A   On time
## 16:58  Penzance                                10    17:02
## 16:59  London Paddington                       7B    On time
## 17:01  London Paddington                       9     On time
## 17:05  Ascot                                   4     On time
## 17:07  Eastleigh                               8     On time
## 17:08  Guildford                               6     On time
## 17:10  Weston-super-Mare                       10    17:15
## 17:13  Didcot Parkway                          15    On time
## 17:13  London Paddington                       9     On time
## 17:14  London Paddington                       14    On time
## 17:15  London Paddington                       12    On time
## 17:20  Bedwyn                                  1     On time
## 17:23  London Paddington                       -     Cancelled
## 17:26  London Paddington                       7     On time
## 17:33  Basingstoke                             2     On time
## 17:35  Ascot                                   4     On time
## 17:37  Paignton                                11    17:41
## 17:39  Manchester Piccadilly                   8     On time
## 17:40  Bristol Temple Meads                    -     Cancelled
## 17:42  London Paddington                       14    On time
## 17:45  Cardiff Central                         11    On time
## 17:45  London Paddington                       9     On time
## 17:50  Bristol Parkway                         -     On time
## 17:53  London Paddington                       -     Cancelled
## 17:56  London Paddington                       8     On time
## 17:57  Hereford                                10    On time
## 17:57  Plymouth                                11    18:00
## 18:05  Ascot                                   4     On time
## 18:06  Plymouth                                -     Cancelled
## 18:07  London Paddington                       9     On time
## 18:08  Guildford                               6     On time
## 18:12  London Paddington                       9     On time
## 18:13  Didcot Parkway                          15    On time
## 18:14  London Paddington                       14    On time
## 18:15  London Paddington                       12    On time
## 18:21  Newbury                                 1     On time
## 18:23  London Paddington                       9     On time
## 18:26  London Paddington                       7     On time
## 18:33  Basingstoke                             2     On time
## 18:33  Gloucester                              11    On time
## 18:35  Ascot                                   4     On time
## 18:39  Manchester Piccadilly                   12    On time
## 18:40  Bristol Temple Meads                    11    On time
## 18:44  Cardiff Central                         10    19:15
## 18:44  London Paddington                       14    On time
## 18:44  London Paddington                       8     On time
## 18:53  London Paddington                       -     Cancelled
## 18:56  Worcester Shrub Hill                    10    On time
## 18:58  Penzance                                11    19:03
## 18:59  London Paddington                       7     On time
## 17:45  Heathrow Central Bus Stn                BUS   On time
## 18:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-03-27 16:04:14
## Time   To                                      Plat  Expected
## 16:59  London Paddington                       10    17:04
## 17:01  London Paddington                       11A   17:04
## 17:03  Plymouth                                7B    On time
## 17:09  Port Talbot Parkway                     9     On time
## 17:12  London Paddington                       10    17:16
## 17:12  Salisbury                               1     On time
## 17:14  Ealing Broadway                         15    On time
## 17:14  Great Malvern                           9     On time
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 17:19  Ascot                                   4     On time
## 17:25  Bristol Temple Meads                    -     Cancelled
## 17:25  Didcot Parkway                          12    On time
## 17:28  Penzance                                7     On time
## 17:30  Ealing Broadway                         14    On time
## 17:38  Basingstoke                             2     On time
## 17:40  London Paddington                       11    17:42
## 17:41  Guildford                               6     On time
## 17:44  Bedwyn                                  1     On time
## 17:45  London Paddington                       -     Cancelled
## 17:48  Oxford                                  9     On time
## 17:49  Ascot                                   4     On time
## 17:50  London Paddington                       -     On time
## 17:50  London Paddington                       11    On time
## 17:52  Eastleigh                               8     On time
## 17:55  Weston-super-Mare                       -     Cancelled
## 17:58  Gloucester                              8     On time
## 17:59  London Paddington                       11    18:01
## 18:00  Ealing Broadway                         14    On time
## 18:01  London Paddington                       10    On time
## 18:09  Port Talbot Parkway                     9     On time
## 18:14  Ealing Broadway                         15    On time
## 18:14  Great Malvern                           9     On time
## 18:14  London Paddington                       -     Cancelled
## 18:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 18:19  Ascot                                   4     On time
## 18:25  Bristol Temple Meads                    9     On time
## 18:25  Didcot Parkway                          12    On time
## 18:29  Exeter St Davids                        7     On time
## 18:30  Ealing Broadway                         14    On time
## 18:33  London Paddington                       11    On time
## 18:39  Basingstoke                             2     On time
## 18:41  Guildford                               6     On time
## 18:41  London Paddington                       11    On time
## 18:44  Newbury                                 1     On time
## 18:46  London Paddington                       10    19:16
## 18:47  Oxford                                  8     On time
## 18:49  Ascot                                   4     On time
## 18:55  Weston-super-Mare                       -     Cancelled
## 18:59  London Paddington                       11    19:04
## 19:00  Ealing Broadway                         14    On time
## 19:01  Plymouth                                7     On time
## 19:02  London Paddington                       10    On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
```
