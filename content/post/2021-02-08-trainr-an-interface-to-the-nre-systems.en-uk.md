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

## Example (Last rendered on 2023-02-09 14:03)

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
## Reading (RDG) Station Board on 2023-02-09 14:03:33
## Time   From                                    Plat  Expected
## 14:02  Penzance                                11    On time
## 14:03  Didcot Parkway                          15A   13:59
## 14:09  Bristol Temple Meads                    10A   14:14
## 14:09  London Paddington                       14    14:17
## 14:11  London Paddington                       9     On time
## 14:13  London Waterloo                         4     On time
## 14:16  Cardiff Central                         11    On time
## 14:16  London Paddington                       9B    On time
## 14:18  London Paddington                       12B   14:21
## 14:19  Basingstoke                             2     On time
## 14:22  Newbury                                 11A   On time
## 14:24  Oxford                                  10A   On time
## 14:25  London Paddington                       9     On time
## 14:27  London Paddington                       7     On time
## 14:29  Cheltenham Spa                          11A   On time
## 14:32  Didcot Parkway                          15    On time
## 14:33  London Paddington                       7     On time
## 14:34  Redhill                                 5     On time
## 14:39  Abbey Wood                              14    On time
## 14:39  Manchester Piccadilly                   8B    14:45
## 14:40  Bristol Temple Meads                    10    On time
## 14:40  Newbury                                 1     On time
## 14:41  London Paddington                       9     On time
## 14:43  London Waterloo                         6     On time
## 14:43  Newbury                                 11    On time
## 14:45  Swansea                                 10    On time
## 14:46  London Paddington                       9     On time
## 14:47  London Paddington                       12    On time
## 14:49  Basingstoke                             2     On time
## 14:51  Gatwick Airport                         4     On time
## 14:51  London Paddington                       9     On time
## 14:55  London Paddington                       8     On time
## 14:55  Worcester Shrub Hill                    10A   On time
## 14:58  Penzance                                11    On time
## 14:59  Didcot Parkway                          15    On time
## 15:00  London Paddington                       7     On time
## 15:05  Bournemouth                             8B    On time
## 15:09  Bristol Temple Meads                    10    On time
## 15:11  Abbey Wood                              13    On time
## 15:11  London Paddington                       9     On time
## 15:12  London Waterloo                         4     On time
## 15:15  Cardiff Central                         11    On time
## 15:16  London Paddington                       9     On time
## 15:17  London Paddington                       12    On time
## 15:25  London Paddington                       9     On time
## 15:25  Oxford                                  10    On time
## 15:26  Basingstoke                             2     On time
## 15:27  London Paddington                       7     On time
## 15:30  Cheltenham Spa                          10A   On time
## 15:33  London Paddington                       7     On time
## 15:33  Redhill                                 5     On time
## 15:35  Didcot Parkway                          15    On time
## 15:36  Newbury                                 1     On time
## 15:39  Abbey Wood                              14    On time
## 15:39  Bristol Temple Meads                    11    On time
## 15:39  Manchester Piccadilly                   8     On time
## 15:41  London Paddington                       9     On time
## 15:43  London Paddington                       12    On time
## 15:43  London Waterloo                         6     On time
## 15:44  Swansea                                 10    On time
## 15:46  London Paddington                       9     On time
## 15:47  Exeter St Davids                        11    On time
## 15:51  Gatwick Airport                         4     On time
## 15:51  London Paddington                       9     On time
## 15:53  Basingstoke                             2     On time
## 15:53  Hereford                                10A   On time
## 15:56  London Paddington                       9     On time
## 14:04  Heathrow Central Bus Stn                BUS   On time
## 14:34  Heathrow Central Bus Stn                BUS   On time
## 15:04  Heathrow Central Bus Stn                BUS   On time
## 15:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-09 14:03:37
## Time   To                                      Plat  Expected
## 14:04  London Paddington                       11    On time
## 14:07  Basingstoke                             2     On time
## 14:08  Ealing Broadway                         15A   On time
## 14:09  London Waterloo                         6     On time
## 14:11  London Paddington                       10A   14:15
## 14:12  Newbury                                 1     On time
## 14:13  Swansea                                 9     On time
## 14:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 14:18  Great Malvern                           9B    On time
## 14:19  London Paddington                       11    On time
## 14:20  Redhill                                 5     On time
## 14:24  London Paddington                       11A   On time
## 14:25  Didcot Parkway                          12B   On time
## 14:27  Abbey Wood                              14    On time
## 14:27  Bristol Temple Meads                    9     On time
## 14:27  London Paddington                       10A   On time
## 14:29  Penzance                                7     On time
## 14:32  Basingstoke                             2     On time
## 14:35  London Paddington                       11A   On time
## 14:37  Ealing Broadway                         15    On time
## 14:37  Newbury                                 7     On time
## 14:39  London Waterloo                         4     On time
## 14:43  Cardiff Central                         9     On time
## 14:43  London Paddington                       10    On time
## 14:45  London Paddington                       11    On time
## 14:48  London Paddington                       10    On time
## 14:48  Oxford                                  9     On time
## 14:52  Bournemouth                             8B    On time
## 14:53  Cheltenham Spa                          9     On time
## 14:55  Didcot Parkway                          12    On time
## 14:57  Abbey Wood                              14    On time
## 14:57  Weston-super-Mare                       8     On time
## 14:58  London Paddington                       10A   On time
## 15:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 15:02  Paignton                                7     On time
## 15:04  London Paddington                       11    On time
## 15:05  Basingstoke                             2     On time
## 15:09  London Waterloo                         6     On time
## 15:10  Newbury                                 1     On time
## 15:12  Ealing Broadway                         15    On time
## 15:13  London Paddington                       10    On time
## 15:13  Swansea                                 9     On time
## 15:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 15:18  London Paddington                       11    On time
## 15:18  Redhill                                 5     On time
## 15:18  Worcester Foregate Street               9     On time
## 15:23  Didcot Parkway                          12    On time
## 15:27  Abbey Wood                              13    On time
## 15:27  Bristol Temple Meads                    9     On time
## 15:27  London Paddington                       10    On time
## 15:29  Penzance                                7     On time
## 15:32  Basingstoke                             2     On time
## 15:34  London Paddington                       10A   On time
## 15:37  Newbury                                 7     On time
## 15:39  London Waterloo                         4     On time
## 15:42  Ealing Broadway                         15    On time
## 15:43  Cardiff Central                         9     On time
## 15:43  London Paddington                       11    On time
## 15:45  London Paddington                       10    On time
## 15:48  Worcester Foregate Street               9     On time
## 15:50  London Paddington                       11    On time
## 15:51  Didcot Parkway                          12    On time
## 15:53  Cheltenham Spa                          9     On time
## 15:56  London Paddington                       10A   On time
## 15:58  Abbey Wood                              14    On time
## 15:58  Weston-super-Mare                       9     On time
## 16:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 14:30  Heathrow Airport T3 (Bus)               BUS   On time
## 15:00  Heathrow Airport T3 (Bus)               BUS   On time
## 15:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
```
