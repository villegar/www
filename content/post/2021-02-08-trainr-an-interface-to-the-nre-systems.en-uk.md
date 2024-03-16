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

## Example (Last rendered on 2024-03-16 11:05)

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
## Reading (RDG) Station Board on 2024-03-16 11:05:53.871576
## Time   From                                    Plat  Expected
## 10:58  Great Malvern                           10    11:07
## 11:01  Didcot Parkway                          15A   11:03
## 11:01  Exeter St Davids                        11    On time
## 11:04  Swindon                                 10A   11:01
## 11:06  Bournemouth                             13B   On time
## 11:09  Birmingham New Street                   3     On time
## 11:10  Abbey Wood                              14    On time
## 11:11  London Paddington                       8     On time
## 11:11  London Waterloo                         4     11:13
## 11:12  Bristol Temple Meads                    10    On time
## 11:14  London Paddington                       12B   On time
## 11:16  London Paddington                       9     11:18
## 11:25  Oxford                                  10A   On time
## 11:26  London Paddington                       7     On time
## 11:27  Basingstoke                             2     On time
## 11:28  Didcot Parkway                          15A   On time
## 11:28  Gatwick Airport                         5     On time
## 11:30  London Paddington                       8B    On time
## 11:30  Newbury                                 11A   On time
## 11:31  Cheltenham Spa                          10A   On time
## 11:38  London Paddington                       9     On time
## 11:40  Abbey Wood                              14    On time
## 11:40  Weston-super-Mare                       10    11:46
## 11:41  Newbury                                 1     On time
## 11:42  Manchester Piccadilly                   7B    On time
## 11:43  Exeter St Davids                        11    11:46
## 11:43  London Waterloo                         6     On time
## 11:44  London Paddington                       12B   On time
## 11:46  Swansea                                 10A   11:58
## 11:47  London Paddington                       9     On time
## 11:49  Basingstoke                             2     On time
## 11:53  London Paddington                       9     On time
## 11:55  London Paddington                       8B    On time
## 11:57  Gatwick Airport                         4     On time
## 11:58  Great Malvern                           10A   On time
## 11:59  Exeter St Davids                        11    On time
## 12:03  Didcot Parkway                          15A   On time
## 12:07  Bournemouth                             13B   On time
## 12:10  Abbey Wood                              14    On time
## 12:10  Bristol Temple Meads                    10    On time
## 12:11  London Paddington                       9     On time
## 12:11  London Waterloo                         5     On time
## 12:13  London Paddington                       8     On time
## 12:14  London Paddington                       12B   On time
## 12:19  Basingstoke                             2     On time
## 12:19  Swindon                                 11A   On time
## 12:23  London Paddington                       9     On time
## 12:23  Oxford                                  10    On time
## 12:26  London Paddington                       7     On time
## 12:28  Gatwick Airport                         4     On time
## 12:31  London Paddington                       8B    On time
## 12:31  Newbury                                 11A   On time
## 12:34  Cheltenham Spa                          10A   On time
## 12:37  Didcot Parkway                          15A   On time
## 12:38  London Paddington                       9     On time
## 12:40  Abbey Wood                              14    On time
## 12:40  Bristol Temple Meads                    10A   On time
## 12:40  Manchester Piccadilly                   7B    On time
## 12:41  Newbury                                 1     On time
## 12:43  London Waterloo                         6     On time
## 12:44  London Paddington                       12B   On time
## 12:45  London Paddington                       9B    On time
## 12:46  Swansea                                 10A   On time
## 12:49  Basingstoke                             2     On time
## 12:53  London Paddington                       9     On time
## 12:55  London Paddington                       8B    On time
## 12:57  Gatwick Airport                         5     On time
## 12:58  London Paddington                       7     On time
## 13:00  Great Malvern                           10A   On time
## 11:15  Heathrow Airport T3 (Bus)               BUS   On time
## 11:45  Heathrow Airport T3 (Bus)               BUS   On time
## 12:15  Heathrow Airport T3 (Bus)               BUS   On time
## 12:45  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-03-16 11:05:56.139779
## Time   To                                      Plat  Expected
## 11:00  London Paddington                       10    11:08
## 11:04  Basingstoke                             2     On time
## 11:05  London Paddington                       11    On time
## 11:07  London Paddington                       10A   On time
## 11:09  London Waterloo                         6     On time
## 11:09  Newbury                                 1     On time
## 11:13  Carmarthen                              8     On time
## 11:13  London Paddington                       15A   On time
## 11:13  London Paddington                       10    On time
## 11:14  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 11:19  Great Malvern                           9     On time
## 11:23  Didcot Parkway                          12B   On time
## 11:24  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:25  Bristol Temple Meads                    9B    On time
## 11:28  London Paddington                       10A   On time
## 11:29  Abbey Wood                              14    On time
## 11:29  Exeter St Davids                        7     On time
## 11:32  London Paddington                       11A   On time
## 11:33  Newbury                                 8B    On time
## 11:34  London Paddington                       10A   On time
## 11:37  Basingstoke                             2     On time
## 11:39  London Waterloo                         4     On time
## 11:40  Swindon                                 9     On time
## 11:42  London Paddington                       10    11:47
## 11:43  London Paddington                       15A   On time
## 11:45  Birmingham New Street                   3     On time
## 11:45  London Paddington                       11    11:47
## 11:49  Oxford                                  9     On time
## 11:50  London Paddington                       10A   11:59
## 11:51  Didcot Parkway                          12B   On time
## 11:52  Bournemouth                             7B    On time
## 11:54  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:55  Weston-super-Mare                       9     On time
## 11:58  Cheltenham Spa                          8B    On time
## 11:59  Abbey Wood                              14    On time
## 12:00  London Paddington                       10A   On time
## 12:05  London Paddington                       11    On time
## 12:07  Basingstoke                             2     On time
## 12:09  London Waterloo                         6     On time
## 12:12  London Paddington                       10    On time
## 12:12  Newbury                                 1     On time
## 12:13  London Paddington                       15A   On time
## 12:13  Swansea                                 9     On time
## 12:14  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 12:19  Hereford                                8     On time
## 12:20  Didcot Parkway                          12B   On time
## 12:20  London Paddington                       11A   On time
## 12:24  Gatwick Airport                         4     On time
##        via Guildford                           
## 12:25  Bristol Temple Meads                    9     On time
## 12:27  London Paddington                       10    On time
## 12:29  Abbey Wood                              14    On time
## 12:30  Exeter St Davids                        7     On time
## 12:32  London Paddington                       11A   On time
## 12:33  Newbury                                 8B    On time
## 12:35  London Paddington                       10A   On time
## 12:37  Basingstoke                             2     On time
## 12:39  London Waterloo                         5     On time
## 12:40  Cardiff Central                         9     On time
## 12:42  London Paddington                       10A   On time
## 12:43  London Paddington                       15A   On time
## 12:48  Oxford                                  9B    On time
## 12:50  London Paddington                       10A   On time
## 12:52  Bournemouth                             7B    On time
## 12:53  Didcot Parkway                          12B   On time
## 12:54  Gatwick Airport                         4     On time
##        via Guildford                           
## 12:55  Weston-super-Mare                       9     On time
## 12:58  Cheltenham Spa                          8B    On time
## 12:59  Abbey Wood                              14    On time
## 13:01  Exeter St Davids                        7     On time
## 13:01  London Paddington                       10A   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
```
