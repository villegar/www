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

## Example (Last rendered on 2022-02-20 14:03)

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
## Reading (RDG) Station Board on 2022-02-20 14:03:53
## Time   From                                    Plat  Expected
## 13:10  Bristol Temple Meads                    11    14:01
## 13:47  Salisbury                               1     14:02
## 13:53  London Paddington                       9     14:11
## 13:55  Great Malvern                           -     Cancelled
## 13:58  Exeter St Davids                        -     Cancelled
## 14:01  London Paddington                       -     Cancelled
## 14:08  Newbury Racecourse                      11    14:21
## 14:09  Bristol Temple Meads                    10    14:39
## 14:10  Didcot Parkway                          13    14:13
## 14:10  Guildford                               6     On time
## 14:12  London Paddington                       -     Cancelled
## 14:16  London Paddington                       14    On time
## 14:17  London Waterloo                         -     Cancelled
## 14:20  Newbury                                 12    14:22
## 14:26  London Paddington                       7     15:00
## 14:33  Basingstoke                             2     On time
## 14:39  London Paddington                       -     Cancelled
## 14:41  Manchester Piccadilly                   13    On time
## 14:45  London Paddington                       9B    On time
## 14:45  Swansea                                 -     Cancelled
## 14:46  London Paddington                       14    On time
## 14:49  London Waterloo                         -     Cancelled
## 14:49  Salisbury                               1     15:16
## 14:53  London Paddington                       9     On time
## 14:56  Hereford                                -     Cancelled
## 14:57  Exeter St Davids                        11    15:16
## 15:00  London Paddington                       -     Cancelled
## 15:07  London Paddington                       -     Cancelled
## 15:07  Southampton Central                     8     On time
## 15:09  Weston-super-Mare                       -     Cancelled
## 15:10  Guildford                               6     On time
## 15:11  Bristol Temple Meads                    -     Delayed
## 15:12  London Paddington                       -     Cancelled
## 15:13  Didcot Parkway                          15    On time
## 15:14  London Paddington                       14    On time
## 15:17  London Waterloo                         4     On time
## 15:18  Bedwyn                                  1     15:20
## 15:23  London Paddington                       -     Cancelled
## 15:26  London Paddington                       -     Cancelled
## 15:33  Basingstoke                             2     On time
## 15:39  Manchester Piccadilly                   7     On time
## 15:40  Bristol Temple Meads                    10    On time
## 15:41  Exeter St Davids                        -     Cancelled
## 15:43  London Paddington                       9     On time
## 15:43  London Paddington                       14    On time
## 15:46  Swansea                                 -     Cancelled
## 15:47  Salisbury                               1     On time
## 15:49  London Waterloo                         -     Cancelled
## 15:53  London Paddington                       9     On time
## 15:57  Hereford                                -     Cancelled
## 15:58  Exeter St Davids                        11    On time
## 14:21  Heathrow Central Bus Stn                BUS   On time
## 15:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-20 14:03:56
## Time   To                                      Plat  Expected
## 13:15  London Paddington                       11    14:03
## 13:52  London Paddington                       14    14:03
## 13:55  Bristol Temple Meads                    9     14:12
## 14:00  London Paddington                       -     Cancelled
## 14:02  London Paddington                       -     Cancelled
## 14:09  Carmarthen                              -     Cancelled
## 14:12  London Paddington                       10    14:40
## 14:12  Salisbury                               1     On time
## 14:14  Hereford                                -     Cancelled
## 14:15  Manchester Piccadilly                   12    On time
##        via Coventry & Wilmslow                 
## 14:22  Ealing Broadway                         14    On time
## 14:25  Didcot Parkway                          13    On time
## 14:25  London Waterloo                         -     Cancelled
## 14:28  Exeter St Davids                        7     15:01
## 14:38  Basingstoke                             2     On time
## 14:40  Cardiff Central                         -     Cancelled
## 14:44  Newbury                                 12    On time
## 14:45  Guildford                               6     On time
## 14:48  Oxford                                  9B    On time
## 14:49  London Paddington                       -     Cancelled
## 14:52  Ealing Broadway                         14    On time
## 14:54  Bristol Temple Meads                    9     On time
## 14:56  London Waterloo                         -     Cancelled
## 14:59  London Paddington                       11    15:17
## 15:01  London Paddington                       -     Cancelled
## 15:03  Exeter St Davids                        -     Cancelled
## 15:09  Swansea                                 -     Cancelled
## 15:11  London Paddington                       -     Cancelled
## 15:11  London Paddington                       -     Delayed
## 15:12  Gillingham (Dorset)                     1     15:19
## 15:14  Great Malvern                           -     Cancelled
## 15:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 15:22  Ealing Broadway                         14    On time
## 15:25  Bristol Temple Meads                    -     Cancelled
## 15:25  Didcot Parkway                          12    On time
## 15:25  London Waterloo                         4     On time
## 15:29  Exeter St Davids                        -     Cancelled
## 15:38  Basingstoke                             2     On time
## 15:43  London Paddington                       -     Cancelled
## 15:44  Bedwyn                                  1     On time
## 15:45  Guildford                               6     On time
## 15:46  London Paddington                       10    On time
## 15:48  Oxford                                  9     On time
## 15:50  London Paddington                       -     Cancelled
## 15:52  Ealing Broadway                         14    On time
## 15:52  Southampton Central                     7     On time
## 15:55  Bristol Temple Meads                    9     On time
## 15:56  London Waterloo                         4     On time
## 15:58  London Paddington                       11    On time
## 16:02  London Paddington                       -     Cancelled
## 15:00  Heathrow Central Bus Stn                BUS   On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
```
