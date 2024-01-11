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

## Example (Last rendered on 2024-01-11 19:04)

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
## Reading (RDG) Station Board on 2024-01-11 19:04:42.655241
## Time   From                                    Plat  Expected
## 18:41  Manchester Piccadilly                   7B    19:14
## 18:57  London Paddington                       8B    19:00
## 18:57  Penzance                                10A   19:05
## 18:58  Great Malvern                           11A   19:01
## 18:59  London Paddington                       7B    19:02
## 19:04  Abbey Wood                              13    19:06
## 19:04  Gatwick Airport                         4     19:06
## 19:05  Didcot Parkway                          15A   19:14
## 19:08  Bournemouth                             8B    19:17
## 19:09  Weston-super-Mare                       10A   19:14
## 19:11  London Paddington                       9B    On time
## 19:14  Abbey Wood                              14    On time
## 19:15  Newbury                                 1     19:18
## 19:16  Cardiff Central                         -     Cancelled
## 19:17  London Waterloo                         6     On time
## 19:21  London Paddington                       9B    On time
## 19:23  London Paddington                       13B   On time
## 19:23  Worcester Foregate Street               10    On time
## 19:25  London Paddington                       8     On time
## 19:27  Didcot Parkway                          15A   On time
## 19:28  London Paddington                       7     On time
## 19:30  Gatwick Airport                         4     On time
## 19:31  Cheltenham Spa                          11A   On time
## 19:34  Abbey Wood                              13    On time
## 19:35  Basingstoke                             2     On time
## 19:35  London Paddington                       -     Cancelled
## 19:39  Bristol Temple Meads                    10    On time
## 19:41  Abbey Wood                              14    On time
## 19:41  London Paddington                       8     On time
## 19:41  Manchester Piccadilly                   7B    On time
## 19:44  London Waterloo                         5     19:46
## 19:46  Carmarthen                              10A   On time
## 19:47  Salisbury                               3     On time
## 19:48  London Paddington                       8     On time
## 19:53  London Paddington                       9     On time
## 19:54  London Paddington                       13B   On time
## 19:54  Plymouth                                11    On time
## 19:55  Worcester Foregate Street               10A   On time
## 19:56  London Paddington                       8B    On time
## 19:57  Gatwick Airport                         4     On time
## 19:59  Didcot Parkway                          15A   On time
## 20:00  Basingstoke                             1     On time
## 20:04  Newbury                                 2     On time
## 20:09  Bournemouth                             12B   On time
## 20:09  Weston-super-Mare                       10    On time
## 20:11  Abbey Wood                              14    On time
## 20:11  London Paddington                       9B    On time
## 20:14  London Waterloo                         6     On time
## 20:16  London Paddington                       9     On time
## 20:16  London Paddington                       13B   On time
## 20:23  London Paddington                       9B    On time
## 20:26  London Paddington                       7     On time
## 20:29  Banbury                                 11    On time
## 20:30  Gatwick Airport                         5     20:33
## 20:32  Didcot Parkway                          15A   On time
## 20:32  London Paddington                       7B    On time
## 20:34  Basingstoke                             2     On time
## 20:34  Cheltenham Spa                          10    On time
## 20:39  Bristol Temple Meads                    11    On time
## 20:41  Abbey Wood                              14    On time
## 20:42  London Waterloo                         4     On time
## 20:43  Manchester Piccadilly                   8     On time
## 20:44  Swansea                                 10    On time
## 20:45  London Paddington                       12B   On time
## 20:45  Salisbury                               15    On time
## 20:46  London Paddington                       9     On time
## 20:46  Newbury                                 1     On time
## 20:53  London Paddington                       9     On time
## 20:55  London Paddington                       8B    On time
## 20:57  Gatwick Airport                         5     On time
## 20:59  Great Malvern                           11A   On time
## 21:00  Penzance                                10    On time
## 19:18  Heathrow Airport T3 (Bus)               BUS   On time
## 19:48  Heathrow Airport T3 (Bus)               BUS   On time
## 20:10  Heathrow Airport T3 (Bus)               BUS   On time
## 20:40  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-11 19:04:45.537348
## Time   To                                      Plat  Expected
## 18:52  Bournemouth                             7B    19:15
## 18:58  London Paddington                       10A   19:06
## 18:59  Cheltenham Spa                          8B    19:03
## 19:01  Exeter St Davids                        7B    19:04
## 19:03  London Paddington                       11A   On time
## 19:05  Basingstoke                             3     On time
## 19:09  London Waterloo                         5     On time
## 19:10  Newbury                                 1     On time
## 19:12  London Paddington                       15A   19:15
## 19:13  London Paddington                       10A   19:15
## 19:13  Swansea                                 9B    On time
## 19:15  Manchester Piccadilly                   8B    19:18
##        via Coventry & Stoke-on-Trent           
## 19:18  London Paddington                       -     Cancelled
## 19:23  Gatwick Airport                         4     On time
##        via Guildford                           
## 19:23  Great Malvern                           9B    On time
## 19:25  Basingstoke                             2     On time
## 19:26  London Paddington                       10    On time
## 19:27  Bristol Temple Meads                    8     On time
## 19:28  Didcot Parkway                          13B   On time
## 19:30  Abbey Wood                              14    On time
## 19:31  Exeter St Davids                        7     On time
## 19:33  London Paddington                       11A   On time
## 19:37  Newbury                                 12A   On time
## 19:39  London Waterloo                         6     On time
## 19:41  London Paddington                       10    On time
## 19:42  London Paddington                       15A   On time
## 19:42  Newbury                                 1     On time
## 19:43  Swansea                                 8     On time
## 19:49  London Paddington                       10A   On time
## 19:49  Oxford                                  8     On time
## 19:50  Bournemouth                             7B    On time
## 19:54  Gatwick Airport                         4     On time
##        via Guildford                           
## 19:55  London Paddington                       11    On time
## 19:55  Weston-super-Mare                       9     On time
## 19:57  Basingstoke                             2     On time
## 19:57  Didcot Parkway                          13B   On time
## 19:58  Worcester Shrub Hill                    8B    On time
##        via Gloucester                          
## 20:00  Abbey Wood                              14    On time
## 20:00  London Paddington                       10A   On time
## 20:09  London Waterloo                         5     On time
## 20:10  Newbury                                 2     On time
## 20:12  London Paddington                       15A   On time
## 20:12  London Paddington                       10    On time
## 20:13  Swansea                                 9B    On time
## 20:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 20:19  Hereford                                9     On time
## 20:20  Shalford                                4     On time
## 20:21  Basingstoke                             1     On time
## 20:23  Didcot Parkway                          13B   On time
## 20:25  Bristol Temple Meads                    9B    On time
## 20:28  Totnes                                  7     On time
## 20:30  Abbey Wood                              14    On time
## 20:34  London Paddington                       11    On time
## 20:35  Newbury                                 7B    On time
## 20:36  London Paddington                       10    On time
## 20:39  London Waterloo                         6     On time
## 20:42  London Paddington                       15A   On time
## 20:42  London Paddington                       11    On time
## 20:47  London Paddington                       10    On time
## 20:48  Oxford                                  9     On time
## 20:49  Bournemouth                             8     On time
## 20:51  Didcot Parkway                          12B   On time
## 20:52  Basingstoke                             2     On time
## 20:54  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:55  Weston-super-Mare                       9     On time
## 20:58  Cheltenham Spa                          8B    On time
## 21:00  Abbey Wood                              14    On time
## 21:01  London Paddington                       11A   On time
## 21:03  London Paddington                       10    On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 20:30  Heathrow Airport T3 (Bus)               BUS   On time
```
