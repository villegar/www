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

## Example (Last rendered on 2024-01-07 07:04)

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
## Reading (RDG) Station Board on 2024-01-07 07:04:25.630312
## Time   From                                    Plat  Expected
## 07:18  London Paddington                       -     Cancelled
## 07:38  Ealing Broadway                         13    Delayed
## 07:41  Gatwick Airport                         4     On time
## 07:51  London Paddington                       14    Delayed
## 08:08  Ealing Broadway                         14    On time
## 08:18  London Paddington                       12    On time
## 08:19  Oxford                                  15    On time
## 08:29  London Paddington                       13    Delayed
## 08:32  London Paddington                       7     On time
## 08:33  Basingstoke                             2     On time
## 08:40  Didcot Parkway                          -     Cancelled
## 08:40  London Paddington                       14    On time
## 08:44  Salisbury                               2     On time
## 07:05  Heathrow Airport T3 (Bus)               BUS   On time
## 07:45  Heathrow Airport T3 (Bus)               BUS   On time
## 08:01  Staines                                 BUS   On time
## 08:15  Heathrow Airport T3 (Bus)               BUS   On time
## 08:31  Staines                                 BUS   On time
## 08:32  Staines                                 BUS   On time
## 08:45  Heathrow Airport T3 (Bus)               BUS   On time
## 09:01  Staines                                 BUS   On time
## 09:02  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-07 07:04:27.037179
## Time   To                                      Plat  Expected
## 07:05  Ealing Broadway                         13    On time
## 07:37  Basingstoke                             15B   On time
## 07:42  London Paddington                       15A   On time
## 07:48  Redhill                                 14    On time
## 07:53  London Paddington                       13    On time
## 08:03  Swansea                                 14    Delayed
## 08:06  Newbury                                 12B   On time
## 08:21  Gatwick Airport                         4     On time
##        via Guildford                           
## 08:21  Penzance                                12    On time
## 08:23  London Paddington                       14    On time
## 08:25  London Paddington                       15    On time
## 08:32  Didcot Parkway                          13    Delayed
## 08:34  Exeter St Davids                        7     On time
##        via Bristol                             
## 08:37  Basingstoke                             2     On time
## 08:41  Bedwyn                                  12    On time
## 08:42  London Paddington                       13    On time
## 08:48  Redhill                                 15    On time
## 08:53  Abbey Wood                              14    On time
## 07:25  Heathrow Airport T3 (Bus)               BUS   On time
## 07:25  Staines                                 BUS   On time
## 07:27  Staines                                 BUS   On time
## 07:55  Heathrow Airport T3 (Bus)               BUS   On time
## 07:55  Staines                                 BUS   On time
## 07:57  Staines                                 BUS   On time
## 08:05  Swindon                                 BUS   On time
## 08:25  Heathrow Airport T3 (Bus)               BUS   On time
## 08:25  Staines                                 BUS   On time
## 08:27  Staines                                 BUS   On time
## 08:35  Swindon                                 BUS   On time
## 08:55  Staines                                 BUS   On time
## 08:57  Staines                                 BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
```
