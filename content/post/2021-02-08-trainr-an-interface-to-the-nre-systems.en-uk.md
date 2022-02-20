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

## Example (Last rendered on 2022-02-20 16:04)

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
## Reading (RDG) Station Board on 2022-02-20 16:04:06
## Time   From                                    Plat  Expected
## 14:57  Exeter St Davids                        11    16:21
## 15:11  Bristol Temple Meads                    11    16:02
## 15:17  London Waterloo                         4     16:16
## 15:39  Manchester Piccadilly                   7     15:57
## 15:53  London Paddington                       9     16:10
## 15:57  Hereford                                -     Cancelled
## 15:58  Exeter St Davids                        -     16:43
## 16:07  London Paddington                       -     Cancelled
## 16:09  Bristol Temple Meads                    10    16:36
## 16:10  Guildford                               6     On time
## 16:13  Didcot Parkway                          15    16:16
## 16:13  London Paddington                       -     Cancelled
## 16:13  London Paddington                       14    On time
## 16:13  Newbury                                 7     16:16
## 16:17  London Waterloo                         -     Cancelled
## 16:23  London Paddington                       -     Cancelled
## 16:25  Oxford                                  -     Cancelled
## 16:26  London Paddington                       7     On time
## 16:32  Cheltenham Spa                          -     Cancelled
## 16:33  Basingstoke                             2     On time
## 16:39  Manchester Piccadilly                   13    17:04
## 16:43  London Paddington                       14    On time
## 16:46  London Paddington                       -     Cancelled
## 16:47  Salisbury                               1     On time
## 16:47  Swansea                                 -     Cancelled
## 16:49  London Waterloo                         -     Cancelled
## 16:53  London Paddington                       9     On time
## 16:57  Great Malvern                           -     Cancelled
## 16:58  Exeter St Davids                        11    17:14
## 17:00  London Paddington                       -     Cancelled
## 17:07  London Paddington                       -     Cancelled
## 17:07  Southampton Central                     8     On time
## 17:10  Bristol Temple Meads                    10    On time
## 17:10  Guildford                               6     On time
## 17:13  Didcot Parkway                          15    On time
## 17:13  London Paddington                       14    On time
## 17:13  London Paddington                       -     Cancelled
## 17:17  Staines                                 4     On time
## 17:20  Bedwyn                                  1     On time
## 17:23  London Paddington                       9     On time
## 17:25  Oxford                                  -     On time
## 17:25  Oxford                                  10    On time
## 17:26  London Paddington                       -     Cancelled
## 17:26  Newbury Racecourse                      8     On time
## 17:33  Basingstoke                             2     On time
## 17:37  Exeter St Davids                        -     Cancelled
## 17:39  Manchester Piccadilly                   8B    On time
## 17:40  Bristol Temple Meads                    -     Cancelled
## 17:43  London Paddington                       14    On time
## 17:45  Carmarthen                              -     Cancelled
## 17:45  London Paddington                       -     Cancelled
## 17:49  London Waterloo                         -     Cancelled
## 17:53  London Paddington                       9     On time
## 17:53  Newbury                                 12    On time
## 17:56  London Paddington                       -     Cancelled
## 17:57  Exeter St Davids                        -     Cancelled
## 17:57  Hereford                                -     Cancelled
## 16:21  Heathrow Central Bus Stn                BUS   On time
## 17:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-02-20 16:04:10
## Time   To                                      Plat  Expected
## 14:59  London Paddington                       11    16:22
## 15:11  London Paddington                       11    16:04
## 15:52  Southampton Central                     7     16:02
## 15:55  Bristol Temple Meads                    9     16:11
## 16:02  London Paddington                       -     Cancelled
## 16:09  Swansea                                 -     Cancelled
## 16:11  London Paddington                       10    16:37
## 16:12  Salisbury                               -     Cancelled
## 16:15  Hereford                                -     Cancelled
## 16:15  Manchester Piccadilly                   -     Cancelled
##        via Coventry & Wilmslow                 
## 16:22  London Paddington                       14    On time
## 16:24  Bristol Temple Meads                    -     Cancelled
## 16:25  Didcot Parkway                          12    On time
## 16:25  London Paddington                       -     Cancelled
## 16:25  London Waterloo                         -     Cancelled
## 16:28  Exeter St Davids                        7     On time
## 16:34  London Paddington                       -     Cancelled
## 16:38  Basingstoke                             2     On time
## 16:44  Newbury                                 15    On time
## 16:45  Guildford                               6     On time
## 16:47  Oxford                                  -     Cancelled
## 16:50  London Paddington                       -     Cancelled
## 16:52  Ealing Broadway                         14    On time
## 16:55  Bristol Temple Meads                    9     On time
## 16:56  London Waterloo                         -     Cancelled
## 16:59  London Paddington                       11    17:15
## 17:01  London Paddington                       -     Cancelled
## 17:03  Exeter St Davids                        -     Cancelled
## 17:09  Swansea                                 -     Cancelled
## 17:12  London Paddington                       10    On time
## 17:12  Salisbury                               1     On time
## 17:14  Great Malvern                           -     Cancelled
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Wilmslow                 
## 17:22  Ealing Broadway                         14    On time
## 17:25  Bristol Temple Meads                    9     On time
## 17:25  Didcot Parkway                          12    On time
## 17:25  London Paddington                       10    On time
## 17:25  London Paddington                       -     On time
## 17:25  London Waterloo                         -     Cancelled
## 17:28  Exeter St Davids                        -     Cancelled
## 17:38  Basingstoke                             2     On time
## 17:40  London Paddington                       -     Cancelled
## 17:44  Bedwyn                                  1     On time
## 17:45  Guildford                               6     On time
## 17:45  London Paddington                       -     Cancelled
## 17:48  Oxford                                  -     Cancelled
## 17:50  London Paddington                       -     Cancelled
## 17:52  Ealing Broadway                         14    On time
## 17:52  Southampton Central                     8B    On time
## 17:55  Bristol Temple Meads                    9     On time
## 17:56  London Waterloo                         -     Cancelled
## 17:58  Cheltenham Spa                          -     Cancelled
## 17:59  London Paddington                       -     Cancelled
## 18:01  London Paddington                       -     Cancelled
## 17:00  Heathrow Central Bus Stn                BUS   On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
```
