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

## Example (Last rendered on 2024-01-21 21:05)

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
## Reading (RDG) Station Board on 2024-01-21 21:05:30.561378
## Time   From                                    Plat  Expected
## 20:39  Manchester Piccadilly                   8     21:11
## 20:47  London Paddington                       13B   21:27
## 20:54  London Paddington                       9     21:03
## 20:58  Bournemouth                             -     Cancelled
## 20:58  Penzance                                11    21:42
## 20:59  Great Malvern                           10    21:22
## 21:07  London Paddington                       9     21:28
## 21:09  Bristol Temple Meads                    10A   21:34
## 21:11  Guildford                               15B   21:13
## 21:12  London Paddington                       7     21:31
## 21:12  London Paddington                       14    21:16
## 21:19  Bedwyn                                  1     On time
## 21:27  London Paddington                       7     On time
## 21:27  London Waterloo                         6     On time
## 21:35  Didcot Parkway                          12    On time
## 21:39  Manchester Piccadilly                   8     21:58
## 21:42  London Paddington                       13    21:45
## 21:42  London Paddington                       9     On time
## 21:47  London Paddington                       14    On time
## 21:48  Swansea                                 11    On time
## 21:54  London Paddington                       9     On time
## 21:54  London Waterloo                         6     22:28
## 21:58  Great Malvern                           10    On time
## 22:04  Plymouth                                11    On time
## 22:09  Bristol Temple Meads                    10    On time
## 22:09  London Paddington                       9     On time
## 22:11  Guildford                               4     On time
## 22:12  London Paddington                       14    On time
## 22:19  London Paddington                       8     On time
## 22:24  Newbury                                 1     On time
## 22:27  Didcot Parkway                          7A    On time
## 22:27  London Waterloo                         6     On time
## 22:29  Henley-on-Thames                        13A   On time
## 22:35  London Paddington                       14    On time
## 22:39  Manchester Piccadilly                   8     22:57
## 22:40  London Paddington                       9     On time
## 22:44  Guildford                               4     On time
## 22:48  Carmarthen                              10    On time
## 22:48  Great Malvern                           13    On time
## 22:50  Penzance                                12    On time
## 22:53  London Waterloo                         5     On time
## 21:10  Heathrow Airport T3 (Bus)               BUS   On time
## 21:16  Bramley (Hampshire)                     BUS   On time
## 21:40  Heathrow Airport T3 (Bus)               BUS   On time
## 22:10  Heathrow Airport T3 (Bus)               BUS   On time
## 22:16  Basingstoke                             BUS   On time
## 22:40  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-01-21 21:05:33.58236
## Time   To                                      Plat  Expected
## 20:46  Southampton Central                     -     Cancelled
## 20:48  Swindon                                 13B   21:28
## 21:00  Bristol Temple Meads                    9     21:05
## 21:03  London Paddington                       10    21:23
## 21:06  London Paddington                       11    21:43
## 21:10  Swansea                                 9     21:29
## 21:12  Birmingham New Street                   8B    On time
##        via Coventry                            
## 21:12  London Paddington                       10A   21:35
## 21:13  Guildford                               5     On time
## 21:15  London Paddington                       13A   On time
## 21:16  Didcot Parkway                          12A   On time
## 21:16  Worcester Shrub Hill                    7     21:32
## 21:24  London Waterloo                         4     On time
## 21:28  Exeter St Davids                        7     On time
## 21:29  Ealing Broadway                         14    On time
## 21:43  Bedwyn                                  1     On time
## 21:46  Southampton Central                     8     21:59
## 21:48  Oxford                                  9     On time
## 21:50  London Waterloo                         6     On time
## 21:55  London Paddington                       11    On time
## 21:56  Bristol Temple Meads                    9     On time
## 21:59  Ealing Broadway                         13    On time
## 22:02  London Paddington                       10    On time
## 22:06  London Paddington                       11    On time
## 22:10  Swansea                                 9     On time
## 22:12  London Paddington                       10    On time
## 22:16  Didcot Parkway                          12A   On time
## 22:18  Guildford                               4     On time
## 22:20  Worcester Shrub Hill                    8     On time
## 22:24  Staines                                 6     22:31
## 22:28  Ealing Broadway                         14    On time
## 22:28  London Paddington                       7A    On time
## 22:41  Bristol Temple Meads                    9     On time
## 22:43  Newbury                                 1     On time
## 22:50  London Paddington                       10    On time
## 22:52  London Paddington                       12    On time
## 22:53  London Paddington                       13    On time
## 22:54  London Waterloo                         6     On time
## 22:58  Ealing Broadway                         14    On time
## 23:03  Guildford                               4     On time
## 21:05  Heathrow Airport T3 (Bus)               BUS   On time
## 21:37  Bramley (Hampshire)                     BUS   On time
## 21:52  Winchester                              BUS   On time
## 22:05  Heathrow Airport T3 (Bus)               BUS   On time
```
