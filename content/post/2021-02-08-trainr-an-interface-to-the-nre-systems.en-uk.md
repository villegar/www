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

## Example (Last rendered on 2023-02-04 12:03)

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
## Reading (RDG) Station Board on 2023-02-04 12:03:51
## Time   From                                    Plat  Expected
## 11:46  Swansea                                 11    12:05
## 11:54  Great Malvern                           10A   12:12
## 11:59  Penzance                                10    On time
## 12:04  London Paddington                       14    On time
## 12:07  Didcot Parkway                          15A   On time
## 12:10  Bristol Temple Meads                    10    12:15
## 12:10  London Paddington                       12B   On time
## 12:11  London Waterloo                         5     12:15
## 12:17  London Paddington                       9     On time
## 12:20  Basingstoke                             2     On time
## 12:25  London Paddington                       9     On time
## 12:25  Oxford                                  10A   On time
## 12:27  London Paddington                       7     On time
## 12:31  Didcot Parkway                          15A   On time
## 12:31  Newbury                                 11A   On time
## 12:33  London Paddington                       7B    On time
## 12:33  Redhill                                 4     On time
## 12:34  Cheltenham Spa                          10A   On time
## 12:34  London Paddington                       14    On time
## 12:39  Manchester Piccadilly                   7     On time
## 12:40  Bristol Temple Meads                    10    On time
## 12:41  London Waterloo                         6     On time
## 12:42  Newbury                                 1     On time
## 12:43  London Paddington                       12B   On time
## 12:46  Swansea                                 10    12:48
## 12:47  London Paddington                       9B    On time
## 12:50  Basingstoke                             2     On time
## 12:51  Gatwick Airport                         5     On time
## 12:51  London Paddington                       8B    On time
## 12:54  Great Malvern                           10A   On time
## 12:58  London Paddington                       7     On time
## 12:59  Penzance                                11    On time
## 13:02  Didcot Parkway                          15A   On time
## 13:04  London Paddington                       14    On time
## 13:06  Bournemouth                             13B   On time
## 13:10  Bristol Temple Meads                    10    On time
## 13:11  London Paddington                       8     On time
## 13:11  London Paddington                       12B   On time
## 13:11  London Waterloo                         4     On time
## 13:17  London Paddington                       9B    On time
## 13:22  Basingstoke                             2     On time
## 13:24  Cardiff Central                         11A   On time
## 13:25  London Paddington                       9     On time
## 13:26  Oxford                                  10A   On time
## 13:27  London Paddington                       7     On time
## 13:31  Newbury                                 11A   On time
## 13:32  London Paddington                       8B    On time
## 13:33  Cheltenham Spa                          10A   On time
## 13:33  Didcot Parkway                          15A   On time
## 13:33  Redhill                                 5     On time
## 13:37  London Paddington                       14    On time
## 13:40  Taunton                                 10    On time
## 13:41  Manchester Piccadilly                   7     On time
## 13:41  Newbury                                 1     On time
## 13:43  London Paddington                       13B   On time
## 13:45  London Waterloo                         6     On time
## 13:46  Exeter St Davids                        11A   On time
## 13:46  Swansea                                 10    On time
## 13:47  London Paddington                       9B    On time
## 13:51  Basingstoke                             2     On time
## 13:51  Gatwick Airport                         4     On time
## 13:51  London Paddington                       8B    On time
## 13:54  Great Malvern                           10A   On time
## 13:55  London Paddington                       9     On time
## 12:04  Heathrow Central Bus Stn                BUS   On time
## 12:34  Heathrow Central Bus Stn                BUS   On time
## 13:04  Heathrow Central Bus Stn                BUS   On time
## 13:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-02-04 12:03:57
## Time   To                                      Plat  Expected
## 11:48  London Paddington                       11    12:06
## 11:57  London Paddington                       10A   12:12
## 12:05  London Paddington                       10    On time
## 12:06  London Waterloo                         6     On time
## 12:08  Basingstoke                             2     On time
## 12:12  London Paddington                       10    12:16
## 12:12  Newbury                                 1     On time
## 12:13  Swansea                                 9     On time
## 12:15  Ealing Broadway                         15A   On time
## 12:15  Manchester Piccadilly                   7     On time
##        via Coventry & Wilmslow                 
## 12:19  Hereford                                9     On time
## 12:20  Redhill                                 4     On time
## 12:23  Didcot Parkway                          12B   On time
## 12:24  Ealing Broadway                         14    On time
## 12:27  Bristol Temple Meads                    9     On time
## 12:27  London Paddington                       10A   On time
## 12:30  London Waterloo                         5     On time
## 12:30  Penzance                                7     On time
## 12:32  London Paddington                       11A   On time
## 12:35  London Paddington                       10A   On time
## 12:35  Newbury                                 7B    On time
## 12:36  London Waterloo                         6     On time
## 12:38  Basingstoke                             2     On time
## 12:42  London Paddington                       10    On time
## 12:45  Ealing Broadway                         15A   On time
## 12:48  London Paddington                       10    12:48
## 12:49  Oxford                                  9B    On time
## 12:52  Bournemouth                             7     On time
## 12:53  Cheltenham Spa                          8B    On time
## 12:53  Didcot Parkway                          12B   On time
## 12:54  Ealing Broadway                         14    On time
## 12:57  London Paddington                       10A   On time
## 13:01  Exeter St Davids                        7     On time
## 13:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 13:05  Basingstoke                             2     On time
## 13:05  London Paddington                       11    On time
## 13:06  London Waterloo                         6     On time
## 13:10  Newbury                                 1     On time
## 13:12  London Paddington                       10    On time
## 13:13  Swansea                                 8     On time
## 13:15  Birmingham New Street                   13B   On time
##        via Coventry                            
## 13:15  Ealing Broadway                         15A   On time
## 13:19  Worcester Foregate Street               9B    On time
## 13:20  Gatwick Airport                         5     On time
##        via Guildford                           
## 13:23  Didcot Parkway                          12B   On time
## 13:24  Ealing Broadway                         14    On time
## 13:25  London Paddington                       11A   On time
## 13:27  Bristol Temple Meads                    9     On time
## 13:28  London Paddington                       10A   On time
## 13:30  London Waterloo                         4     On time
## 13:30  Penzance                                7     On time
## 13:32  London Paddington                       11A   On time
## 13:34  Newbury                                 8B    On time
## 13:34  Redhill                                 13A   On time
## 13:35  London Paddington                       10A   On time
## 13:38  Basingstoke                             2     On time
## 13:38  London Waterloo                         6     On time
## 13:43  London Paddington                       10    On time
## 13:45  Ealing Broadway                         15A   On time
## 13:47  London Paddington                       11A   On time
## 13:49  Oxford                                  9B    On time
## 13:50  London Paddington                       10    On time
## 13:53  Cheltenham Spa                          8B    On time
## 13:54  Ealing Broadway                         14    On time
## 13:55  Didcot Parkway                          13B   On time
## 13:56  London Paddington                       10A   On time
## 13:57  Weston-super-Mare                       9     On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
## 13:30  Heathrow Airport T3 (Bus)               BUS   On time
## 14:00  Heathrow Airport T3 (Bus)               BUS   On time
```
