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

## Example (Last rendered on 2024-01-17 15:04)

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
## Reading (RDG) Station Board on 2024-01-17 15:04:37.581829
## Time   From                                    Plat  Expected
## 14:59  Penzance                                11A   15:22
## 15:00  Didcot Parkway                          -     On time
## 15:06  Bournemouth                             8B    On time
## 15:07  Newcastle                               15    On time
## 15:09  Weston-super-Mare                       -     On time
## 15:10  Abbey Wood                              -     On time
## 15:11  London Paddington                       -     On time
## 15:12  London Waterloo                         -     15:16
## 15:15  Cardiff Central                         -     15:18
## 15:17  London Paddington                       -     On time
## 15:19  London Paddington                       -     On time
## 15:23  London Paddington                       -     On time
## 15:25  Basingstoke                             2     On time
## 15:25  Oxford                                  -     On time
## 15:28  Gatwick Airport                         -     On time
## 15:31  Cheltenham Spa                          -     On time
## 15:32  London Paddington                       -     On time
## 15:35  Didcot Parkway                          -     On time
## 15:36  Newbury                                 -     On time
## 15:39  Bristol Temple Meads                    -     On time
## 15:39  London Paddington                       9     On time
## 15:41  Manchester Piccadilly                   7B    On time
## 15:42  Abbey Wood                              14    On time
## 15:43  London Waterloo                         -     On time
## 15:44  Swansea                                 -     15:47
## 15:46  London Paddington                       -     On time
## 15:46  London Paddington                       -     On time
## 15:47  Exeter St Davids                        -     15:52
## 15:51  London Paddington                       -     On time
## 15:55  Basingstoke                             2     On time
## 15:55  London Paddington                       -     On time
## 15:56  Plymouth                                -     On time
## 15:57  Gatwick Airport                         -     On time
## 15:59  Hereford                                -     On time
## 16:02  Didcot Parkway                          -     On time
## 16:09  Bournemouth                             8     On time
## 16:09  Bristol Temple Meads                    -     On time
## 16:11  London Paddington                       9     On time
## 16:11  London Waterloo                         -     On time
## 16:12  Abbey Wood                              14    On time
## 16:16  Cardiff Central                         -     On time
## 16:17  Basingstoke                             2     On time
## 16:17  London Paddington                       -     On time
## 16:22  Newbury                                 -     On time
## 16:23  London Paddington                       -     On time
## 16:23  Oxford                                  10    On time
## 16:25  Abbey Wood                              13    On time
## 16:26  London Paddington                       -     On time
## 16:28  Gatwick Airport                         5     On time
## 16:31  Cheltenham Spa                          -     On time
## 16:31  Didcot Parkway                          -     On time
## 16:32  Newbury                                 -     On time
## 16:34  London Paddington                       -     On time
## 16:39  Bristol Temple Meads                    -     On time
## 16:40  Manchester Piccadilly                   7     On time
## 16:41  London Paddington                       -     On time
## 16:42  Abbey Wood                              14    On time
## 16:42  Exeter St Davids                        -     On time
## 16:42  London Waterloo                         6     On time
## 16:45  Swansea                                 -     On time
## 16:46  London Paddington                       -     On time
## 16:46  London Paddington                       -     On time
## 16:53  London Paddington                       -     On time
## 16:55  Basingstoke                             2     On time
## 16:55  London Paddington                       -     On time
## 16:57  Abbey Wood                              13    On time
## 16:57  Worcester Foregate Street               -     On time
## 16:58  Newbury                                 -     On time
## 15:15  Heathrow Airport T3 (Bus)               -     On time
## 15:45  Heathrow Airport T3 (Bus)               -     On time
## 16:15  Heathrow Airport T3 (Bus)               -     On time
## 16:45  Heathrow Airport T3 (Bus)               -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-17 15:04:41.873833
## Time   To                                      Plat  Expected
## 15:04  London Paddington                       11A   15:23
## 15:05  Basingstoke                             2     On time
## 15:09  London Waterloo                         6     On time
## 15:10  Newbury                                 -     On time
## 15:11  London Paddington                       -     On time
## 15:11  London Paddington                       -     On time
## 15:13  Swansea                                 -     On time
## 15:14  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 15:17  Gatwick Airport                         5     On time
##        via Guildford                           
## 15:18  London Paddington                       -     15:19
## 15:18  Worcester Foregate Street               -     On time
## 15:22  Didcot Parkway                          -     On time
## 15:25  Bristol Temple Meads                    -     On time
## 15:27  London Paddington                       -     On time
## 15:29  Abbey Wood                              14    On time
## 15:29  Penzance                                -     On time
## 15:32  Basingstoke                             2     On time
## 15:34  London Paddington                       -     On time
## 15:37  Newbury                                 -     On time
## 15:39  London Waterloo                         4     On time
## 15:41  Cardiff Central                         9     On time
## 15:42  London Paddington                       -     On time
## 15:43  London Paddington                       -     On time
## 15:43  York                                    12B   On time
##        via Doncaster                           
## 15:45  London Paddington                       -     15:48
## 15:48  Worcester Foregate Street               -     On time
## 15:50  London Paddington                       -     15:53
## 15:51  Didcot Parkway                          -     On time
## 15:52  Bournemouth                             7B    On time
## 15:53  Weston-super-Mare                       -     On time
## 15:54  Gatwick Airport                         5     On time
##        via Guildford                           
## 15:58  Cheltenham Spa                          -     On time
## 15:59  Abbey Wood                              14    On time
## 16:02  London Paddington                       -     On time
## 16:04  London Paddington                       -     On time
## 16:07  Basingstoke                             2     On time
## 16:09  London Waterloo                         6     On time
## 16:10  London Paddington                       -     On time
## 16:11  London Paddington                       -     On time
## 16:12  Newbury                                 -     On time
## 16:13  Carmarthen                              9     On time
## 16:14  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 16:16  Abbey Wood                              13    On time
## 16:18  Great Malvern                           -     On time
## 16:18  London Paddington                       -     On time
## 16:20  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:24  London Paddington                       -     On time
## 16:25  Bristol Temple Meads                    -     On time
## 16:25  Didcot Parkway                          -     On time
## 16:26  London Paddington                       10    On time
## 16:29  Penzance                                -     On time
## 16:31  Abbey Wood                              14    On time
## 16:33  Basingstoke                             2     On time
## 16:34  London Paddington                       -     On time
## 16:36  Newbury                                 -     On time
## 16:39  London Waterloo                         4     On time
## 16:41  London Paddington                       -     On time
## 16:42  London Paddington                       -     On time
## 16:43  Swansea                                 -     On time
## 16:44  London Paddington                       -     17:14
## 16:47  Abbey Wood                              13    On time
## 16:47  London Paddington                       -     On time
## 16:48  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:49  Oxford                                  -     On time
## 16:51  Didcot Parkway                          -     On time
## 16:52  Bournemouth                             7     On time
## 16:55  Taunton                                 -     On time
## 16:58  Cheltenham Spa                          -     On time
## 17:00  London Paddington                       -     On time
## 17:01  Abbey Wood                              14    On time
## 17:01  Plymouth                                -     On time
## 17:02  London Paddington                       -     On time
## 15:30  Heathrow Airport T3 (Bus)               -     On time
## 16:00  Heathrow Airport T3 (Bus)               -     On time
## 16:30  Heathrow Airport T3 (Bus)               -     On time
## 17:00  Heathrow Airport T3 (Bus)               -     On time
```
