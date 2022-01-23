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

## Example (Last rendered on 2022-01-23 14:03)

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
## Reading (RDG) Station Board on 2022-01-23 14:03:33
## Time   From                                    Plat  Expected
## 13:57  Great Malvern                           13A   14:00
## 13:58  Penzance                                11A   14:03
## 14:05  London Waterloo                         4     14:02
## 14:10  Didcot Parkway                          13A   On time
## 14:10  Redhill                                 5     On time
## 14:12  London Paddington                       9B    On time
## 14:13  London Paddington                       7     14:17
## 14:13  London Paddington                       14    On time
## 14:16  London Paddington                       13B   On time
## 14:18  Swansea                                 11    14:22
## 14:27  London Paddington                       7B    On time
## 14:31  London Paddington                       7     On time
## 14:32  London Waterloo                         4     14:37
## 14:33  Basingstoke                             2     On time
## 14:38  Gatwick Airport                         5     On time
## 14:38  Newbury                                 7B    On time
## 14:41  Banbury                                 13    On time
## 14:41  Bristol Temple Meads                    11    On time
## 14:43  London Paddington                       14    On time
## 14:48  London Paddington                       9     On time
## 14:49  Salisbury                               1     On time
## 14:56  Hereford                                12A   On time
## 14:57  Penzance                                11    15:01
## 15:00  London Paddington                       7     On time
## 15:02  London Waterloo                         4     15:05
## 15:07  Bournemouth                             8B    On time
## 15:08  Redhill                                 6     On time
## 15:12  London Paddington                       9B    On time
## 15:13  Didcot Parkway                          15A   On time
## 15:13  London Paddington                       7     On time
## 15:13  London Paddington                       14    On time
## 15:15  London Paddington                       12B   On time
## 15:22  Bedwyn                                  1     On time
## 15:23  Swansea                                 11    15:35
## 15:25  Oxford                                  15A   On time
## 15:27  London Paddington                       7B    On time
## 15:29  Bristol Temple Meads                    10    On time
## 15:31  London Paddington                       8     On time
## 15:32  London Waterloo                         4     On time
## 15:33  Basingstoke                             2     On time
## 15:38  Gatwick Airport                         5     On time
## 15:39  Banbury                                 7     On time
## 15:42  Exeter St Davids                        11    On time
## 15:43  London Paddington                       14    On time
## 15:47  Salisbury                               1     On time
## 15:48  London Paddington                       9B    On time
## 15:56  Hereford                                12A   On time
## 15:57  Exeter St Davids                        11A   On time
## 16:02  London Waterloo                         4     On time
## 14:21  Heathrow Central Bus Stn                BUS   On time
## 14:30  Swindon                                 BUS   On time
## 15:00  Swindon                                 BUS   On time
## 15:21  Heathrow Central Bus Stn                BUS   On time
## 15:30  Swindon                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-23 14:03:37
## Time   To                                      Plat  Expected
## 13:59  London Paddington                       11A   14:04
## 14:01  London Paddington                       13A   On time
## 14:12  London Paddington                       13A   On time
## 14:12  Salisbury                               1     On time
## 14:14  Hereford                                9B    On time
## 14:15  Banbury                                 12    On time
## 14:18  Bristol Temple Meads                    7     On time
## 14:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 14:20  London Paddington                       11    14:23
## 14:24  London Waterloo                         4     On time
## 14:27  Ealing Broadway                         14    On time
## 14:28  Penzance                                7B    On time
## 14:30  Didcot Parkway                          13B   On time
## 14:33  Swansea                                 7     On time
## 14:38  Basingstoke                             2     On time
## 14:41  Redhill                                 15    On time
## 14:44  Newbury                                 7B    On time
## 14:45  London Paddington                       11    On time
## 14:50  Oxford                                  9     On time
## 14:54  London Waterloo                         4     On time
## 14:57  Ealing Broadway                         14    On time
## 14:59  London Paddington                       11    15:02
## 15:01  London Paddington                       12A   On time
## 15:03  Exeter St Davids                        7     On time
## 15:12  Gillingham (Dorset)                     1     On time
## 15:14  Great Malvern                           9B    On time
## 15:14  London Paddington                       15A   On time
## 15:15  Banbury                                 8B    On time
## 15:18  Bristol Temple Meads                    7     On time
## 15:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 15:24  London Waterloo                         4     On time
## 15:27  Ealing Broadway                         14    On time
## 15:29  Plymouth                                7B    On time
## 15:30  Didcot Parkway                          12B   On time
## 15:30  London Paddington                       11    15:36
## 15:32  London Paddington                       15A   On time
## 15:33  Swansea                                 8     On time
## 15:38  Basingstoke                             2     On time
## 15:41  Redhill                                 6     On time
## 15:44  Bedwyn                                  1     On time
## 15:45  London Paddington                       10    On time
## 15:50  London Paddington                       11    On time
## 15:50  Oxford                                  9B    On time
## 15:52  Bournemouth                             7     On time
## 15:54  London Waterloo                         4     On time
## 15:57  Ealing Broadway                         14    On time
## 15:59  London Paddington                       11A   On time
## 16:01  London Paddington                       12A   On time
## 14:10  Swindon                                 BUS   On time
## 14:25  Swindon                                 BUS   On time
## 15:00  Heathrow Central Bus Stn                BUS   On time
## 15:10  Swindon                                 BUS   On time
## 15:25  Swindon                                 BUS   On time
## 16:00  Heathrow Central Bus Stn                BUS   On time
```
