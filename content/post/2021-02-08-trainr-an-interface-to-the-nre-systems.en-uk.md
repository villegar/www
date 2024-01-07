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

## Example (Last rendered on 2024-01-07 11:04)

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
## Reading (RDG) Station Board on 2024-01-07 11:04:24.182715
## Time   From                                    Plat  Expected
## 09:05  Bristol Temple Meads                    11    10:54
## 10:22  Bristol Temple Meads                    10    11:30
## 10:36  Exeter St Davids                        11    Delayed
## 10:40  Bristol Parkway                         10    11:19
## 10:51  London Paddington                       8B    11:06
## 10:59  Great Malvern                           8     11:19
## 11:06  Bournemouth                             12    11:13
## 11:08  Redhill                                 4     11:10
## 11:12  Ealing Broadway                         9     On time
## 11:19  London Paddington                       7     11:23
## 11:20  Theale                                  1     On time
## 11:23  Oxford                                  8     Delayed
## 11:24  Bristol Temple Meads                    -     Cancelled
## 11:27  London Paddington                       7B    Delayed
## 11:33  Basingstoke                             2     On time
## 11:35  Totnes                                  11    12:09
## 11:36  Didcot Parkway                          8     On time
## 11:38  Gatwick Airport                         4     On time
## 11:38  Swansea                                 10    Delayed
## 11:39  Manchester Piccadilly                   7     On time
## 11:46  London Paddington                       9     11:56
## 11:47  Salisbury                               2     On time
## 11:49  London Paddington                       -     Cancelled
## 11:58  Totnes                                  11    12:22
## 11:59  Great Malvern                           8     On time
## 12:03  Bournemouth                             -     Cancelled
## 12:06  Swansea                                 10    Delayed
## 12:08  Redhill                                 4     On time
## 12:12  Abbey Wood                              9     12:15
## 12:19  London Paddington                       8     Delayed
## 12:20  Theale                                  1     On time
## 12:23  Bristol Temple Meads                    11    Delayed
## 12:23  Oxford                                  10    On time
## 12:27  London Paddington                       7     On time
## 12:31  London Paddington                       8     On time
## 12:32  Basingstoke                             2     On time
## 12:38  Didcot Parkway                          8     On time
## 12:38  Gatwick Airport                         4     On time
## 12:46  Maidenhead                              9     On time
## 12:47  Salisbury                               2     On time
## 12:49  Manchester Piccadilly                   3     On time
## 12:50  Swansea                                 11    On time
## 12:57  London Paddington                       7     On time
## 11:15  Heathrow Airport T3 (Bus)               BUS   On time
## 11:15  Swindon                                 BUS   On time
## 11:31  Staines                                 BUS   On time
## 11:32  Staines                                 BUS   On time
## 11:45  Heathrow Airport T3 (Bus)               BUS   On time
## 11:55  Swindon                                 BUS   On time
## 12:01  Staines                                 BUS   On time
## 12:02  Staines                                 BUS   On time
## 12:15  Heathrow Airport T3 (Bus)               BUS   On time
## 12:15  Swindon                                 BUS   On time
## 12:31  Staines                                 BUS   On time
## 12:32  Staines                                 BUS   On time
## 12:45  Heathrow Airport T3 (Bus)               BUS   On time
## 12:45  Swindon                                 BUS   On time
## 13:01  Staines                                 BUS   On time
## 13:02  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-07 11:04:26.200715
## Time   To                                      Plat  Expected
## 09:06  London Paddington                       11    Delayed
## 10:34  London Paddington                       10    11:31
## 10:42  London Paddington                       11    Delayed
## 10:48  London Paddington                       10    11:20
## 10:51  Oxford                                  8B    11:06
## 11:01  Paignton                                7     11:18
## 11:03  London Paddington                       8     11:20
## 11:11  Great Malvern                           7     11:20
## 11:12  Salisbury                               2     On time
## 11:14  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 11:17  Swansea                                 8     Delayed
## 11:21  Gatwick Airport                         4     On time
##        via Guildford                           
## 11:23  Didcot Parkway                          7     11:23
## 11:26  London Paddington                       -     Cancelled
## 11:28  Abbey Wood                              9     On time
## 11:28  Plymouth                                7B    Delayed
## 11:33  London Paddington                       8     Delayed
## 11:36  London Paddington                       11    12:10
## 11:37  Basingstoke                             2     On time
## 11:39  London Paddington                       8     On time
## 11:43  Theale                                  1     On time
## 11:48  London Paddington                       10    Delayed
## 11:51  Redhill                                 4     On time
## 11:52  Bournemouth                             -     Cancelled
## 11:52  Oxford                                  8     On time
## 11:58  Abbey Wood                              9     On time
## 12:03  London Paddington                       8     On time
## 12:06  London Paddington                       11    12:23
## 12:07  Manchester Piccadilly                   3     On time
##        via Coventry & Stoke-on-Trent           
## 12:12  London Paddington                       10    Delayed
## 12:12  Salisbury                               2     On time
## 12:14  Hereford                                8     Delayed
## 12:17  Swansea                                 7     On time
## 12:21  Gatwick Airport                         4     On time
##        via Guildford                           
## 12:25  London Paddington                       10    On time
## 12:28  Abbey Wood                              9     On time
## 12:28  Didcot Parkway                          8     Delayed
## 12:28  Penzance                                7     On time
## 12:34  Weston-super-Mare                       8     On time
## 12:36  London Paddington                       11    Delayed
## 12:37  Basingstoke                             2     On time
## 12:39  London Paddington                       8     On time
## 12:43  Newbury                                 1     On time
## 12:51  Redhill                                 4     On time
## 12:52  Oxford                                  12    On time
## 12:53  Bournemouth                             3     On time
## 12:54  London Paddington                       11    On time
## 12:58  Abbey Wood                              9     On time
## 13:01  Paignton                                7     On time
## 11:05  Swindon                                 BUS   On time
## 11:25  Staines                                 BUS   On time
## 11:27  Staines                                 BUS   On time
## 11:30  Heathrow Airport T3 (Bus)               BUS   On time
## 11:40  Swindon                                 BUS   On time
## 11:55  Staines                                 BUS   On time
## 11:57  Staines                                 BUS   On time
## 12:00  Heathrow Airport T3 (Bus)               BUS   On time
## 12:05  Swindon                                 BUS   On time
## 12:25  Staines                                 BUS   On time
## 12:27  Staines                                 BUS   On time
## 12:30  Heathrow Airport T3 (Bus)               BUS   On time
## 12:40  Swindon                                 BUS   On time
## 12:55  Staines                                 BUS   On time
## 12:57  Staines                                 BUS   On time
## 13:00  Heathrow Airport T3 (Bus)               BUS   On time
```
