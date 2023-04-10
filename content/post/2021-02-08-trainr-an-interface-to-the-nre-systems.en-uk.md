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

## Example (Last rendered on 2023-04-10 20:03)

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
## Reading (RDG) Station Board on 2023-04-10 20:03:52
## Time   From                                    Plat  Expected
## 20:58  London Paddington                       -     Delayed
## 21:01  Bournemouth                             8B    On time
## 21:02  London Paddington                       -     21:11
## 21:03  Didcot Parkway                          15    20:59
## 21:03  London Paddington                       13    21:06
## 21:09  Bristol Temple Meads                    10    21:12
## 21:11  London Paddington                       9     On time
## 21:11  London Waterloo                         6     On time
## 21:20  London Paddington                       14    On time
## 21:20  Penzance                                11    On time
## 21:24  Didcot Parkway                          10A   On time
## 21:25  London Paddington                       9     On time
## 21:27  London Paddington                       8     On time
## 21:29  Didcot Parkway                          13A   On time
## 21:29  Redhill                                 -     Cancelled
## 21:33  Cheltenham Spa                          10A   On time
## 21:33  London Paddington                       14    On time
## 21:42  London Waterloo                         5     On time
## 21:44  Swansea                                 11    Delayed
## 21:45  London Paddington                       12    On time
## 21:51  London Paddington                       9B    On time
## 21:53  Great Malvern                           10    On time
## 21:56  Gatwick Airport                         15    On time
## 22:04  London Paddington                       14    On time
## 22:05  Didcot Parkway                          15A   On time
## 22:08  Taunton                                 10    On time
## 22:11  London Paddington                       9     On time
## 22:11  London Waterloo                         4     On time
## 22:12  Paignton                                11    On time
## 22:15  London Paddington                       12    On time
## 22:26  London Paddington                       9     On time
## 22:32  Cheltenham Spa                          10    On time
## 22:34  Shalford                                14A   On time
## 22:35  London Paddington                       14    On time
## 22:39  Didcot Parkway                          7B    On time
## 22:41  London Waterloo                         5     On time
## 22:43  Swansea                                 10    On time
## 22:45  London Paddington                       12    On time
## 22:47  Didcot Parkway                          15    On time
## 22:55  London Paddington                       9     On time
## 21:21  Bedwyn                                  BUS   On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
## 21:40  Bramley (Hampshire)                     BUS   On time
## 21:47  Newbury                                 BUS   On time
## 22:18  Bedwyn                                  BUS   On time
## 22:18  Heathrow Central Bus Stn                BUS   On time
## 22:40  Basingstoke                             BUS   On time
## 22:47  Newbury                                 BUS   On time
## 22:48  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-10 20:03:56
## Time   To                                      Plat  Expected
## 21:07  Ealing Broadway                         15    On time
## 21:11  London Paddington                       10    21:13
## 21:12  London Waterloo                         4     On time
## 21:13  Swansea                                 9     On time
## 21:14  Didcot Parkway                          8B    On time
## 21:22  London Paddington                       11    On time
## 21:23  Didcot Parkway                          14    On time
## 21:24  Ealing Broadway                         13A   On time
## 21:26  London Paddington                       10A   On time
## 21:27  Bristol Temple Meads                    9     On time
## 21:29  Plymouth                                8     On time
## 21:34  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:37  Ealing Broadway                         13A   On time
## 21:42  London Waterloo                         6     On time
## 21:43  London Paddington                       10A   On time
## 21:46  London Paddington                       11    Delayed
## 21:49  Didcot Parkway                          12    On time
## 21:51  Ealing Broadway                         14A   On time
## 21:53  Cheltenham Spa                          9B    On time
## 21:56  London Paddington                       10    On time
## 22:08  Ealing Broadway                         15A   On time
## 22:10  London Paddington                       10    On time
## 22:12  London Waterloo                         5     On time
## 22:13  London Paddington                       11    On time
## 22:13  Swansea                                 9     On time
## 22:18  Didcot Parkway                          12    On time
## 22:22  Ealing Broadway                         14A   On time
## 22:27  Plymouth                                9     On time
##        via Bristol                             
## 22:35  London Paddington                       10    On time
## 22:42  Staines                                 4     On time
## 22:46  London Paddington                       10    On time
## 22:47  Didcot Parkway                          12    On time
## 22:49  Southampton Central                     7B    On time
## 22:52  Ealing Broadway                         14A   On time
## 22:59  Bristol Temple Meads                    9     On time
## 21:10  Newbury                                 -     Cancelled
## 21:38  Bramley (Hampshire)                     BUS   On time
## 21:40  Bedwyn                                  BUS   On time
## 21:55  Winchester                              BUS   On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
## 22:10  Bedwyn                                  BUS   On time
## 22:38  Bramley (Hampshire)                     BUS   On time
## 22:55  Winchester                              BUS   On time
## 23:00  Heathrow Airport T3 (Bus)               BUS   On time
```
