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

## Example (Last rendered on 2023-01-15 16:03)

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
## Reading (RDG) Station Board on 2023-01-15 16:03:57
## Time   From                                    Plat  Expected
## 15:45  Port Talbot Parkway                     11    Delayed
## 15:53  London Paddington                       9     16:13
## 15:57  Great Malvern                           10    16:08
## 16:07  London Paddington                       9     On time
## 16:08  Redhill                                 6     On time
## 16:10  Bristol Temple Meads                    10    16:18
## 16:12  London Paddington                       9B    On time
## 16:12  Newbury                                 3     On time
## 16:13  Didcot Parkway                          15A   On time
## 16:13  London Paddington                       12B   On time
## 16:15  London Waterloo                         4     On time
## 16:25  Oxford                                  10A   On time
## 16:26  London Paddington                       7     On time
## 16:32  Gloucester                              10A   On time
## 16:32  London Waterloo                         4     On time
## 16:33  Abbey Wood                              14    On time
## 16:38  Gatwick Airport                         5     On time
## 16:39  Stockport                               15A   On time
## 16:40  Swindon                                 11A   On time
## 16:45  Port Talbot Parkway                     10    17:06
## 16:46  London Paddington                       9B    On time
## 16:53  London Paddington                       9     On time
## 16:57  Hereford                                10    On time
## 16:58  Penzance                                11    On time
## 17:00  London Paddington                       7B    On time
## 17:02  London Waterloo                         4     On time
## 17:03  Abbey Wood                              14    On time
## 17:07  London Paddington                       9     On time
## 17:09  Weston-super-Mare                       10    On time
## 17:11  Redhill                                 6     On time
## 17:13  Didcot Parkway                          15    On time
## 17:13  London Paddington                       9     On time
## 17:13  London Paddington                       12B   On time
## 17:20  Bedwyn                                  3     On time
## 17:23  London Paddington                       9     On time
## 17:25  Oxford                                  10    On time
## 17:26  London Paddington                       7     On time
## 17:32  London Waterloo                         4     On time
## 17:33  Abbey Wood                              14    On time
## 17:36  Paignton                                11    On time
## 17:38  Gatwick Airport                         5     On time
## 17:39  Stockport                               7     On time
## 17:40  Swindon                                 10    On time
## 17:44  Port Talbot Parkway                     11    17:49
## 17:45  London Paddington                       9     On time
## 17:53  London Paddington                       9     On time
## 17:56  London Paddington                       8     On time
## 17:57  Hereford                                10    On time
## 17:57  Plymouth                                11    On time
## 18:02  London Waterloo                         4     On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:20  Basingstoke                             BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 17:00  Southampton Central                     BUS   On time
## 17:00  Winchester                              BUS   On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
## 17:20  Bramley (Hampshire)                     BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-01-15 16:04:03
## Time   To                                      Plat  Expected
## 15:47  London Paddington                       11    Delayed
## 15:55  Taunton                                 9     16:15
## 16:02  London Paddington                       10    16:09
## 16:09  Port Talbot Parkway                     9     On time
## 16:11  London Paddington                       10    16:19
## 16:14  Ealing Broadway                         15A   On time
## 16:14  Hereford                                9B    On time
## 16:15  Stockport                               7B    On time
##        via Coventry & Stoke-on-Trent           
## 16:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:24  Abbey Wood                              14    On time
## 16:24  London Waterloo                         4     On time
## 16:25  Didcot Parkway                          12B   On time
## 16:25  Swindon                                 9     On time
## 16:26  London Paddington                       10A   On time
## 16:28  Penzance                                7     On time
## 16:34  London Paddington                       10A   On time
## 16:41  Redhill                                 6     On time
## 16:42  London Paddington                       11A   On time
## 16:43  Newbury                                 3     On time
## 16:46  Bournemouth                             15A   On time
## 16:46  London Paddington                       10    17:07
## 16:48  Oxford                                  9B    On time
## 16:54  Abbey Wood                              14    On time
## 16:54  London Waterloo                         4     On time
## 16:55  Plymouth                                9     On time
##        via Bristol                             
## 16:59  London Paddington                       11    On time
## 17:00  London Paddington                       10    On time
## 17:01  Plymouth                                7B    On time
## 17:09  Port Talbot Parkway                     9     On time
## 17:11  London Paddington                       10    On time
## 17:14  Ealing Broadway                         15    On time
## 17:14  Great Malvern                           9     On time
## 17:15  Stockport                               15B   On time
##        via Coventry & Stoke-on-Trent           
## 17:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:24  Abbey Wood                              14    On time
## 17:24  London Waterloo                         4     On time
## 17:25  Didcot Parkway                          12B   On time
## 17:25  Swindon                                 9     On time
## 17:27  London Paddington                       10    On time
## 17:28  Penzance                                7     On time
## 17:40  London Paddington                       11    On time
## 17:41  Redhill                                 6     On time
## 17:42  London Paddington                       10    On time
## 17:43  Bedwyn                                  3     On time
## 17:46  London Paddington                       11    17:50
## 17:48  Oxford                                  9     On time
## 17:54  Abbey Wood                              14    On time
## 17:54  London Waterloo                         4     On time
## 17:55  Weston-super-Mare                       9     On time
## 17:58  Gloucester                              8     On time
## 17:59  London Paddington                       11    On time
## 18:01  London Paddington                       10    On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 16:38  Basingstoke                             BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:38  Bramley (Hampshire)                     BUS   On time
## 17:52  Winchester                              BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
```
