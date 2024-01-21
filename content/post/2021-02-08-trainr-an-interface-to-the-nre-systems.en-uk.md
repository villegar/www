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

## Example (Last rendered on 2024-01-21 09:03)

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
## Reading (RDG) Station Board on 2024-01-21 09:04:00.808795
## Time   From                                    Plat  Expected
## 09:01  Bristol Temple Meads                    14A   09:31
## 09:02  London Paddington                       15    On time
## 09:13  London Paddington                       14    On time
## 09:15  London Paddington                       13    On time
## 09:18  Newbury                                 1     On time
## 09:23  London Paddington                       15    On time
## 09:25  London Paddington                       12    On time
## 09:27  London Waterloo                         -     Cancelled
## 09:28  London Paddington                       14    On time
## 09:38  Guildford                               13    On time
## 09:43  London Paddington                       14    On time
## 09:54  Clapham Junction                        4     Delayed
## 09:58  London Paddington                       15    On time
## 09:58  Southampton Central                     13    On time
## 10:00  London Paddington                       12    On time
## 10:11  Guildford                               5     On time
## 10:13  London Paddington                       14    On time
## 10:15  London Paddington                       12    On time
## 10:18  Bedwyn                                  13    On time
## 10:26  London Paddington                       12    On time
## 10:27  London Waterloo                         4     10:40
## 10:28  Swansea                                 13    On time
## 10:34  Bristol Parkway                         14    On time
## 10:37  Exeter St Davids                        13    On time
## 10:38  Guildford                               5     On time
## 10:39  Birmingham New Street                   15    On time
## 10:42  London Paddington                       14    On time
## 10:46  Bristol Parkway                         13    On time
## 10:47  London Paddington                       12    On time
## 10:52  London Paddington                       13    On time
## 10:53  Didcot Parkway                          15    On time
## 10:54  London Waterloo                         4     On time
## 10:55  London Paddington                       12    On time
## 10:58  London Paddington                       13    On time
## 09:15  Chippenham                              BUS   On time
## 09:15  Heathrow Airport T3 (Bus)               BUS   On time
## 09:45  Heathrow Airport T3 (Bus)               BUS   On time
## 09:55  Oxford                                  BUS   On time
## 10:00  Basingstoke                             BUS   On time
## 10:00  Oxford                                  BUS   On time
## 10:10  Swindon                                 BUS   On time
## 10:15  Heathrow Airport T3 (Bus)               BUS   On time
## 10:16  Bramley (Hampshire)                     BUS   On time
## 10:45  Heathrow Airport T3 (Bus)               BUS   On time
## 11:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-21 09:04:02.201413
## Time   To                                      Plat  Expected
## 09:03  London Paddington                       14A   09:33
## 09:16  London Paddington                       15    On time
## 09:18  Guildford                               5     On time
## 09:24  Ealing Broadway                         14    On time
## 09:24  London Waterloo                         4     On time
## 09:26  Penzance                                12    On time
## 09:30  Bristol Temple Meads                    14    On time
## 09:30  London Paddington                       13    On time
## 09:43  Bedwyn                                  3     On time
## 09:48  London Waterloo                         -     Cancelled
## 09:56  Guildford                               6     On time
## 09:59  Ealing Broadway                         14    On time
## 10:01  Carmarthen                              12    On time
## 10:08  London Paddington                       15    On time
## 10:14  Manchester Piccadilly                   13    On time
##        via Coventry & Wilmslow                 
## 10:15  London Paddington                       15    On time
## 10:19  Hereford                                12    On time
## 10:21  Guildford                               5     On time
## 10:24  London Waterloo                         4     Delayed
## 10:28  Penzance                                12    On time
## 10:29  Ealing Broadway                         14    On time
## 10:30  Didcot Parkway                          15A   On time
## 10:31  London Paddington                       13    On time
## 10:36  London Paddington                       14    On time
## 10:40  London Paddington                       13    On time
## 10:43  Newbury                                 1     On time
## 10:46  Bournemouth                             15    On time
## 10:47  London Paddington                       13    On time
## 10:48  Bristol Parkway                         12    On time
## 10:50  London Waterloo                         4     On time
## 10:53  Oxford                                  13    On time
## 10:56  Guildford                               5     On time
## 10:57  Bristol Temple Meads                    12    On time
## 10:59  Ealing Broadway                         14    On time
## 11:00  Paignton                                13    On time
## 09:07  Basingstoke                             BUS   On time
## 09:10  Didcot Parkway                          BUS   On time
## 09:25  Oxford                                  BUS   On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:52  Winchester                              BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:37  Bramley (Hampshire)                     BUS   On time
## 10:52  Winchester                              BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
```
