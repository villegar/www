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

## Example (Last rendered on 2023-01-15 10:05)

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
## Reading (RDG) Station Board on 2023-01-15 10:05:55
## Time   From                                    Plat  Expected
## 09:37  Bristol Parkway                         11    10:19
## 09:56  London Paddington                       9     10:05
## 09:57  Worcester Foregate Street               10A   10:16
## 09:58  Didcot Parkway                          15A   On time
## 09:59  Southampton Central                     14    On time
## 10:03  London Waterloo                         4     10:05
## 10:10  Weston-super-Mare                       10    10:31
## 10:11  Redhill                                 6     10:18
## 10:12  London Paddington                       9     On time
## 10:16  London Paddington                       13B   On time
## 10:18  Bedwyn                                  15    On time
## 10:25  Cardiff Central                         11    10:39
## 10:26  London Paddington                       7     On time
## 10:33  London Paddington                       14    On time
## 10:33  London Waterloo                         4     On time
## 10:35  Exeter St Davids                        11A   On time
## 10:39  Birmingham New Street                   15B   On time
## 10:39  Gatwick Airport                         5     On time
## 10:42  London Paddington                       9     On time
## 10:45  London Paddington                       8B    On time
## 10:53  Bristol Parkway                         10    11:08
## 10:53  London Paddington                       9     On time
## 10:53  Southampton Central                     13    10:56
## 10:56  Great Malvern                           11    On time
## 10:59  London Paddington                       7     On time
## 11:03  London Paddington                       14    On time
## 11:03  London Waterloo                         4     On time
## 11:07  London Paddington                       9     On time
## 11:09  Bristol Temple Meads                    10    On time
## 11:10  Didcot Parkway                          15A   On time
## 11:11  Redhill                                 6     On time
## 11:12  London Paddington                       9     On time
## 11:15  Cardiff Central                         10    On time
## 11:15  London Paddington                       12B   On time
## 11:19  Bedwyn                                  1     On time
## 11:25  Oxford                                  10A   On time
## 11:26  London Paddington                       7     On time
## 11:32  London Waterloo                         4     On time
## 11:33  Abbey Wood                              14    On time
## 11:34  Plymouth                                11    On time
## 11:38  Gatwick Airport                         5     On time
## 11:39  Stockport                               7     On time
## 11:44  Cardiff Central                         11    12:00
## 11:45  London Paddington                       9     On time
## 11:53  London Paddington                       9     On time
## 11:56  Great Malvern                           10A   On time
## 11:58  Plymouth                                11    On time
## 12:02  London Waterloo                         4     On time
## 12:03  Abbey Wood                              14    On time
## 10:04  Heathrow Central Bus Stn                BUS   On time
## 10:34  Heathrow Central Bus Stn                BUS   On time
## 10:50  Bramley (Hampshire)                     BUS   On time
## 11:00  Winchester                              BUS   On time
## 11:04  Heathrow Central Bus Stn                BUS   On time
## 11:34  Heathrow Central Bus Stn                BUS   On time
## 12:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-01-15 10:06:00
## Time   To                                      Plat  Expected
## 09:40  London Paddington                       11    10:20
## 09:58  Cardiff Central                         9     10:06
## 09:59  London Paddington                       10A   10:18
## 10:12  London Paddington                       10    10:32
## 10:13  Hereford                                9     On time
## 10:14  Ealing Broadway                         15A   On time
## 10:15  Stockport                               14    On time
##        via Coventry & Stoke-on-Trent           
## 10:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:24  Abbey Wood                              12    On time
## 10:24  London Waterloo                         4     On time
## 10:27  London Paddington                       11    10:40
## 10:28  Penzance                                7     On time
## 10:36  London Paddington                       11A   On time
## 10:41  Redhill                                 6     On time
## 10:43  Newbury                                 3     On time
## 10:43  Swindon                                 9     On time
## 10:48  Oxford                                  8B    On time
## 10:54  Abbey Wood                              14    On time
## 10:54  London Paddington                       10    11:09
## 10:54  London Waterloo                         4     On time
## 10:55  Weston-super-Mare                       9     On time
## 10:57  London Paddington                       11    On time
## 11:01  Paignton                                7     On time
## 11:09  Port Talbot Parkway                     9     On time
## 11:11  London Paddington                       10    On time
## 11:14  Ealing Broadway                         15A   On time
## 11:14  Great Malvern                           9     On time
## 11:15  Stockport                               13    On time
##        via Coventry & Stoke-on-Trent           
## 11:16  London Paddington                       10    On time
## 11:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:24  Abbey Wood                              14    On time
## 11:24  London Waterloo                         4     On time
## 11:26  Didcot Parkway                          12B   On time
## 11:26  London Paddington                       10A   On time
## 11:28  Plymouth                                7     On time
## 11:35  London Paddington                       11    On time
## 11:41  Redhill                                 6     On time
## 11:43  Bedwyn                                  1     On time
## 11:45  London Paddington                       11    12:01
## 11:48  Oxford                                  9     On time
## 11:54  Abbey Wood                              14    On time
## 11:54  London Waterloo                         4     On time
## 11:55  Bristol Temple Meads                    9     On time
## 11:59  London Paddington                       11    On time
## 12:02  London Paddington                       10A   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:38  Basingstoke                             BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:38  Bramley (Hampshire)                     BUS   On time
## 11:52  Winchester                              BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
```
