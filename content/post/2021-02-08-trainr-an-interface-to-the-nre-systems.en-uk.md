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

## Example (Last rendered on 2024-01-07 09:04)

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
## Reading (RDG) Station Board on 2024-01-07 09:04:36.499865
## Time   From                                    Plat  Expected
## 08:40  Didcot Parkway                          -     Cancelled
## 09:02  London Paddington                       -     Cancelled
## 09:05  Bristol Temple Meads                    11    Delayed
## 09:09  London Paddington                       7B    Delayed
## 09:10  Ealing Broadway                         14    On time
## 09:14  London Paddington                       10    Delayed
## 09:16  London Paddington                       12    Delayed
## 09:22  Newbury                                 1     08:47
## 09:25  Oxford                                  12A   On time
## 09:32  Basingstoke                             2     On time
## 09:39  Gatwick Airport                         7B    On time
## 09:41  Didcot Parkway                          8     On time
## 09:42  London Paddington                       -     Cancelled
## 09:48  Salisbury                               -     Cancelled
## 09:49  London Paddington                       7B    Delayed
## 10:02  Worcester Foregate Street               8     On time
## 10:06  Southampton Central                     12B   On time
## 10:08  Redhill                                 4     On time
## 10:12  Ealing Broadway                         9     On time
## 10:19  Bedwyn                                  12    On time
## 10:19  London Paddington                       8     Delayed
## 10:22  Bristol Temple Meads                    10    10:38
## 10:26  London Paddington                       7     Delayed
## 10:32  Basingstoke                             2     On time
## 10:36  Didcot Parkway                          8     On time
## 10:36  Exeter St Davids                        11    Delayed
## 10:39  Birmingham New Street                   12B   On time
## 10:40  Bristol Parkway                         10    On time
## 10:40  Gatwick Airport                         -     Cancelled
## 10:46  London Paddington                       9     Delayed
## 10:47  Salisbury                               2     On time
## 10:51  London Paddington                       8B    Delayed
## 10:57  London Paddington                       7     Delayed
## 10:59  Great Malvern                           8     On time
## 09:15  Chippenham                              BUS   On time
## 09:15  Heathrow Airport T3 (Bus)               BUS   On time
## 09:31  Staines                                 BUS   On time
## 09:32  Staines                                 BUS   On time
## 09:45  Heathrow Airport T3 (Bus)               BUS   On time
## 09:45  Swindon                                 BUS   On time
## 10:01  Staines                                 BUS   On time
## 10:02  Staines                                 BUS   On time
## 10:15  Heathrow Airport T3 (Bus)               BUS   On time
## 10:15  Swindon                                 BUS   On time
## 10:31  Staines                                 BUS   On time
## 10:32  Staines                                 BUS   On time
## 10:45  Heathrow Airport T3 (Bus)               BUS   On time
## 10:45  Swindon                                 BUS   On time
## 11:01  Staines                                 BUS   On time
## 11:02  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-07 09:04:40.863045
## Time   To                                      Plat  Expected
## 08:42  Slough                                  13    Delayed
## 09:06  London Paddington                       11    Delayed
## 09:08  Swansea                                 -     Cancelled
## 09:11  Great Malvern                           7B    Delayed
## 09:12  Salisbury                               2     On time
## 09:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 09:18  Didcot Parkway                          12    Delayed
## 09:18  Gatwick Airport                         15    On time
##        via Guildford                           
## 09:21  Penzance                                10    Delayed
## 09:23  Abbey Wood                              14    On time
## 09:26  London Paddington                       12A   On time
## 09:37  Basingstoke                             2     On time
## 09:43  Bedwyn                                  3     On time
## 09:43  London Paddington                       8     On time
## 09:50  Oxford                                  7B    Delayed
## 09:51  Redhill                                 4     On time
## 09:52  Bournemouth                             11B   On time
## 09:58  Abbey Wood                              9     On time
## 10:03  London Paddington                       8     On time
## 10:10  Hereford                                8B    Delayed
## 10:12  Salisbury                               -     Cancelled
## 10:14  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 10:17  Swansea                                 7     Delayed
## 10:21  Gatwick Airport                         4     On time
##        via Guildford                           
## 10:25  Didcot Parkway                          8     Delayed
## 10:28  Abbey Wood                              9     On time
## 10:28  Penzance                                7     Delayed
## 10:34  London Paddington                       10    10:39
## 10:37  Basingstoke                             2     On time
## 10:39  London Paddington                       8     On time
## 10:42  London Paddington                       11    Delayed
## 10:43  Newbury                                 1     On time
## 10:48  Bournemouth                             12B   On time
## 10:48  London Paddington                       10    On time
## 10:51  Oxford                                  8B    Delayed
## 10:51  Redhill                                 4     On time
## 10:58  Abbey Wood                              9     On time
## 11:01  Paignton                                7     Delayed
## 11:03  London Paddington                       8     On time
## 09:05  Swindon                                 BUS   On time
## 09:25  Staines                                 BUS   On time
## 09:27  Staines                                 BUS   On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:40  Swindon                                 BUS   On time
## 09:55  Staines                                 BUS   On time
## 09:57  Staines                                 BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
## 10:05  Swindon                                 BUS   On time
## 10:25  Staines                                 BUS   On time
## 10:27  Staines                                 BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:40  Swindon                                 BUS   On time
## 10:55  Staines                                 BUS   On time
## 10:57  Staines                                 BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
```
