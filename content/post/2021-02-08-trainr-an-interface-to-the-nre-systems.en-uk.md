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

## Example (Last rendered on 2023-03-24 16:03)

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
## Reading (RDG) Station Board on 2023-03-24 16:03:54
## Time   From                                    Plat  Expected
## 15:47  Exeter St Davids                        11    15:58
## 15:57  Plymouth                                10    16:03
## 16:07  Didcot Parkway                          15    16:00
## 16:09  Bristol Temple Meads                    10    16:11
## 16:11  Abbey Wood                              14    On time
## 16:11  London Paddington                       9     16:13
## 16:11  London Waterloo                         4     On time
## 16:16  Cardiff Central                         11A   16:31
## 16:17  Basingstoke                             2     On time
## 16:21  London Paddington                       12B   On time
## 16:22  Newbury                                 11    On time
## 16:24  Oxford                                  10A   On time
## 16:25  Abbey Wood                              13    On time
## 16:25  London Paddington                       9     On time
## 16:29  Cheltenham Spa                          11A   On time
## 16:31  Didcot Parkway                          15    On time
## 16:32  Newbury                                 1     On time
## 16:33  London Paddington                       7B    On time
## 16:33  Redhill                                 5     On time
## 16:38  Abbey Wood                              14    On time
## 16:39  Bristol Temple Meads                    10    On time
## 16:39  Manchester Piccadilly                   8     On time
## 16:41  London Paddington                       9     On time
## 16:42  London Paddington                       12    On time
## 16:42  London Waterloo                         6     On time
## 16:43  Paignton                                11    16:45
## 16:45  Cardiff Central                         10    17:01
## 16:46  London Paddington                       9B    On time
## 16:50  Basingstoke                             2     On time
## 16:53  Worcester Foregate Street               10    On time
## 16:55  Abbey Wood                              13    On time
## 16:56  London Paddington                       9     On time
## 16:57  Newbury                                 11    On time
## 16:59  London Paddington                       7     On time
## 17:01  Penzance                                10    On time
## 17:03  Didcot Parkway                          15A   On time
## 17:03  Gatwick Airport                         5     On time
## 17:06  Bournemouth                             8     On time
## 17:09  Bristol Temple Meads                    11    On time
## 17:11  Abbey Wood                              14    On time
## 17:11  London Paddington                       9     On time
## 17:16  London Waterloo                         6     On time
## 17:17  Cardiff Central                         11    On time
## 17:22  London Paddington                       12    On time
## 17:24  Oxford                                  10A   On time
## 17:25  London Paddington                       8     On time
## 17:26  Abbey Wood                              13    On time
## 17:26  Basingstoke                             2     On time
## 17:29  Cheltenham Spa                          10A   On time
## 17:34  Newbury                                 1     On time
## 17:35  Didcot Parkway                          15    On time
## 17:35  London Paddington                       7     On time
## 17:35  Redhill                                 5     On time
## 17:38  Bristol Temple Meads                    10    On time
## 17:40  Abbey Wood                              14    On time
## 17:40  Manchester Piccadilly                   8     On time
## 17:41  London Paddington                       9     On time
## 17:42  London Waterloo                         4     On time
## 17:45  Exeter St Davids                        11    On time
## 17:47  Swansea                                 10    17:49
## 17:49  Basingstoke                             2     On time
## 17:54  London Paddington                       12B   On time
## 17:55  London Paddington                       8     On time
## 17:56  Hereford                                10    On time
## 17:57  Plymouth                                11    On time
## 17:58  Abbey Wood                              13    On time
## 17:58  London Paddington                       9     On time
## 18:02  Gatwick Airport                         5     On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-24 16:03:59
## Time   To                                      Plat  Expected
## 15:50  London Paddington                       11    16:02
## 16:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 16:04  London Paddington                       10    On time
## 16:07  Basingstoke                             2     On time
## 16:09  London Waterloo                         6     On time
## 16:12  Ealing Broadway                         15    On time
## 16:12  London Paddington                       10    On time
## 16:12  Newbury                                 1     On time
## 16:13  Swansea                                 9     16:14
## 16:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 16:18  Abbey Wood                              13    On time
## 16:18  London Paddington                       11A   16:32
## 16:19  Great Malvern                           9B    On time
## 16:20  Redhill                                 5     On time
## 16:24  London Paddington                       11    On time
## 16:25  Didcot Parkway                          12B   On time
## 16:26  London Paddington                       10A   On time
## 16:27  Bristol Temple Meads                    9     On time
## 16:28  Abbey Wood                              14    On time
## 16:29  Penzance                                7     On time
## 16:32  London Paddington                       11A   On time
## 16:33  Basingstoke                             2     On time
## 16:37  Newbury                                 7B    On time
## 16:38  Ealing Broadway                         15    On time
## 16:39  London Waterloo                         4     On time
## 16:42  London Paddington                       10    On time
## 16:43  Swansea                                 9     On time
## 16:45  London Paddington                       11    16:45
## 16:47  London Paddington                       10    17:02
## 16:48  Abbey Wood                              13    On time
## 16:48  Oxford                                  9B    On time
## 16:50  Didcot Parkway                          12    On time
## 16:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:52  Bournemouth                             8     On time
## 16:57  London Paddington                       10    On time
## 16:58  Abbey Wood                              14    On time
## 16:58  Taunton                                 9     On time
## 16:59  London Paddington                       11    On time
## 17:02  Plymouth                                7     On time
## 17:05  London Paddington                       10    On time
## 17:09  London Waterloo                         6     On time
## 17:10  Newbury                                 1     On time
## 17:11  Ealing Broadway                         15A   On time
## 17:11  London Paddington                       11    On time
## 17:13  Swansea                                 9     On time
## 17:15  Basingstoke                             2     On time
## 17:15  Birmingham New Street                   8     On time
##        via Coventry                            
## 17:18  Abbey Wood                              13    On time
## 17:18  London Paddington                       11    On time
## 17:20  Redhill                                 5     On time
## 17:25  Didcot Parkway                          12    On time
## 17:27  Bristol Temple Meads                    8     On time
## 17:27  London Paddington                       10A   On time
## 17:28  Abbey Wood                              14    On time
## 17:29  Penzance                                7     On time
## 17:32  London Paddington                       10A   On time
## 17:38  Basingstoke                             2     On time
## 17:39  London Waterloo                         6     On time
## 17:41  London Paddington                       10    On time
## 17:41  Newbury                                 7     On time
## 17:42  Ealing Broadway                         15    On time
## 17:43  Swansea                                 9     On time
## 17:45  London Paddington                       11    On time
## 17:48  Abbey Wood                              13    On time
## 17:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:50  London Paddington                       10    On time
## 17:52  Bournemouth                             8     On time
## 17:57  Basingstoke                             2     On time
## 17:57  Taunton                                 8     On time
## 17:58  Abbey Wood                              14    On time
## 17:58  Didcot Parkway                          12B   On time
## 17:58  London Paddington                       11    On time
## 18:00  Hereford                                9     On time
## 18:00  London Paddington                       10    On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
```
