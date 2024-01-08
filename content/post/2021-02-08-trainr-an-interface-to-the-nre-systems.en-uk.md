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

## Example (Last rendered on 2024-01-08 15:35)

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
## Reading (RDG) Station Board on 2024-01-08 15:35:44.849117
## Time   From                                    Plat  Expected
## 15:06  Bournemouth                             8B    15:53
## 15:31  Cheltenham Spa                          11A   On time
## 15:32  London Paddington                       -     Cancelled
## 15:35  Didcot Parkway                          15A   15:31
## 15:36  Newbury Racecourse                      1     15:38
## 15:39  Bristol Temple Meads                    11    On time
## 15:39  London Paddington                       9     On time
## 15:41  Manchester Piccadilly                   7B    On time
## 15:42  Abbey Wood                              14    On time
## 15:43  London Waterloo                         -     Cancelled
## 15:44  Swansea                                 10    15:46
## 15:46  London Paddington                       9B    On time
## 15:46  London Paddington                       12B   On time
## 15:47  Exeter St Davids                        11A   15:49
## 15:51  London Paddington                       9     On time
## 15:55  Basingstoke                             2     On time
## 15:55  London Paddington                       8B    On time
## 15:56  Plymouth                                11    On time
## 15:57  Gatwick Airport                         5     On time
## 15:59  Hereford                                10A   On time
## 16:02  Didcot Parkway                          15A   On time
## 16:09  Bournemouth                             8B    On time
## 16:09  Bristol Temple Meads                    10    On time
## 16:11  London Paddington                       9     On time
## 16:11  London Waterloo                         4     16:27
## 16:12  Abbey Wood                              14    On time
## 16:16  Cardiff Central                         11    On time
## 16:17  Basingstoke                             2     On time
## 16:17  London Paddington                       12B   On time
## 16:22  Newbury                                 -     Cancelled
## 16:23  London Paddington                       9     On time
## 16:23  Oxford                                  10A   On time
## 16:25  Abbey Wood                              13    On time
## 16:26  London Paddington                       7     On time
## 16:28  Gatwick Airport                         5     16:32
## 16:31  Cheltenham Spa                          11A   On time
## 16:31  Didcot Parkway                          15A   On time
## 16:32  Newbury Racecourse                      1     On time
## 16:34  London Paddington                       -     Cancelled
## 16:39  Bristol Temple Meads                    10    On time
## 16:40  Manchester Piccadilly                   7B    On time
## 16:41  London Paddington                       9     On time
## 16:42  Abbey Wood                              14    On time
## 16:42  London Waterloo                         6     17:07
## 16:42  Paignton                                11    On time
## 16:45  Swansea                                 10    On time
## 16:46  London Paddington                       9     On time
## 16:46  London Paddington                       12B   On time
## 16:53  London Paddington                       8     On time
## 16:55  Basingstoke                             2     On time
## 16:55  London Paddington                       9B    On time
## 16:57  Abbey Wood                              13    On time
## 16:57  Worcester Foregate Street               10    On time
## 16:58  London Paddington                       7     On time
## 16:58  Newbury                                 -     Cancelled
## 17:02  Penzance                                11    On time
## 17:04  Didcot Parkway                          15A   On time
## 17:04  Gatwick Airport                         4     On time
## 17:06  Bournemouth                             8B    On time
## 17:09  Weston-super-Mare                       11    On time
## 17:11  Abbey Wood                              14    On time
## 17:11  London Paddington                       9     On time
## 17:14  Newcastle                               15    On time
## 17:16  London Waterloo                         6     On time
## 17:17  Cardiff Central                         11    On time
## 17:22  Oxford                                  10    On time
## 17:23  London Paddington                       8     On time
## 17:23  London Paddington                       12B   On time
## 17:26  Basingstoke                             2     On time
## 17:26  London Paddington                       7     On time
## 17:29  Gatwick Airport                         5     On time
## 17:30  Cheltenham Spa                          11A   On time
## 17:34  Abbey Wood                              13    On time
## 17:34  Newbury Racecourse                      3     On time
## 15:45  Heathrow Airport T3 (Bus)               BUS   On time
## 16:15  Heathrow Airport T3 (Bus)               BUS   On time
## 16:45  Heathrow Airport T3 (Bus)               BUS   On time
## 17:18  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-08 15:35:48.441913
## Time   To                                      Plat  Expected
## 15:14  Manchester Piccadilly                   8B    15:54
##        via Coventry & Stoke-on-Trent           
## 15:37  Newbury                                 -     Cancelled
## 15:39  London Waterloo                         -     Cancelled
## 15:41  Cardiff Central                         9     On time
## 15:42  London Paddington                       15A   On time
## 15:43  London Paddington                       11    On time
## 15:43  York                                    12B   On time
##        via Doncaster                           
## 15:45  London Paddington                       10    15:47
## 15:48  Worcester Foregate Street               9B    On time
## 15:50  London Paddington                       11A   On time
## 15:51  Didcot Parkway                          12B   On time
## 15:52  Bournemouth                             7B    On time
## 15:53  Weston-super-Mare                       9     On time
## 15:54  Gatwick Airport                         5     On time
##        via Guildford                           
## 15:58  Cheltenham Spa                          8B    On time
## 15:59  Abbey Wood                              14    On time
## 16:02  London Paddington                       10A   On time
## 16:04  London Paddington                       11    On time
## 16:07  Basingstoke                             2     On time
## 16:09  London Waterloo                         -     Cancelled
## 16:10  London Paddington                       15A   On time
## 16:11  London Paddington                       10    On time
## 16:12  Newbury Racecourse                      1     On time
## 16:13  Carmarthen                              9     On time
## 16:14  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 16:16  Abbey Wood                              13    On time
## 16:18  Great Malvern                           9B    On time
## 16:18  London Paddington                       11    On time
## 16:20  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:24  London Paddington                       -     Cancelled
## 16:25  Bristol Temple Meads                    9     On time
## 16:25  Didcot Parkway                          12B   On time
## 16:26  London Paddington                       10A   On time
## 16:29  Penzance                                7     On time
## 16:31  Abbey Wood                              14    On time
## 16:33  Basingstoke                             2     On time
## 16:34  London Paddington                       11A   On time
## 16:36  Newbury                                 -     Cancelled
## 16:39  London Waterloo                         4     On time
## 16:41  London Paddington                       10    On time
## 16:42  London Paddington                       15A   On time
## 16:43  Swansea                                 9     On time
## 16:44  London Paddington                       11    On time
## 16:47  Abbey Wood                              13    On time
## 16:47  London Paddington                       10    On time
## 16:48  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:49  Oxford                                  9     On time
## 16:51  Didcot Parkway                          12B   On time
## 16:52  Bournemouth                             7B    On time
## 16:55  Taunton                                 8     On time
## 16:58  Cheltenham Spa                          9B    On time
## 17:00  London Paddington                       -     Cancelled
## 17:01  Abbey Wood                              14    On time
## 17:01  Plymouth                                7     On time
## 17:02  London Paddington                       10    On time
## 17:05  London Paddington                       11    On time
## 17:09  London Waterloo                         6     On time
## 17:10  Newbury Racecourse                      1     On time
## 17:11  London Paddington                       15A   On time
## 17:11  London Paddington                       11    On time
## 17:13  Swansea                                 9     On time
## 17:15  Abbey Wood                              13    On time
## 17:15  Basingstoke                             2     On time
## 17:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 17:18  London Paddington                       11    On time
## 17:20  Gatwick Airport                         4     On time
##        via Guildford                           
## 17:25  London Paddington                       10    On time
## 17:27  Bristol Temple Meads                    8     On time
## 17:27  Didcot Parkway                          12B   On time
## 17:29  Penzance                                7     On time
## 17:32  Abbey Wood                              14    On time
## 17:33  London Paddington                       11A   On time
## 16:00  Heathrow Airport T3 (Bus)               BUS   On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
```
