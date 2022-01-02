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

## Example (Last rendered on 2022-01-02 08:03)

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
## Reading (RDG) Station Board on 2022-01-02 08:03:06
## Time   From                                    Plat  Expected
## 07:33  London Paddington                       13    08:01
## 08:15  London Paddington                       8     08:18
## 08:23  London Paddington                       13B   On time
## 08:23  London Paddington                       9     08:25
## 08:55  Salisbury                               1     On time
## 08:57  London Paddington                       9B    On time
## 08:59  Swindon                                 10A   On time
## 09:03  London Paddington                       14    On time
## 09:07  London Paddington                       12B   On time
## 09:10  Didcot Parkway                          15A   On time
## 09:12  London Paddington                       12B   On time
## 09:14  London Paddington                       7     On time
## 09:23  London Paddington                       7     On time
## 09:24  Oxford                                  15A   On time
## 09:26  Newbury                                 1     On time
## 09:29  Bristol Parkway                         15    On time
## 09:33  London Paddington                       14    On time
## 09:39  Bristol Temple Meads                    15    On time
## 09:41  Redhill                                 13A   On time
## 09:47  Salisbury                               2     On time
## 08:02  Staines                                 BUS   On time
## 08:21  Heathrow Central Bus Stn                BUS   On time
## 08:31  Virginia Water                          BUS   On time
## 08:52  Virginia Water                          BUS   On time
## 09:01  Virginia Water                          BUS   On time
## 09:20  Basingstoke                             BUS   On time
## 09:21  Heathrow Central Bus Stn                BUS   On time
## 09:22  Virginia Water                          BUS   On time
## 09:31  Virginia Water                          BUS   On time
## 09:52  Virginia Water                          BUS   On time
## 10:01  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-02 08:03:09
## Time   To                                      Plat  Expected
## 08:10  London Paddington                       15A   On time
## 08:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 08:20  Penzance                                8     On time
## 08:25  London Paddington                       14    On time
## 08:31  Exeter St Davids                        9     On time
##        via Bristol                             
## 08:40  Redhill                                 14A   On time
## 08:50  Newbury                                 15B   On time
## 08:52  Ealing Broadway                         14    On time
## 08:53  Didcot Parkway                          13B   On time
## 08:59  Swansea                                 9B    On time
## 09:01  London Paddington                       10A   On time
## 09:09  Great Malvern                           12B   On time
## 09:10  Ealing Broadway                         15A   On time
## 09:12  Salisbury                               1     On time
## 09:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:18  Didcot Parkway                          12B   On time
## 09:18  Gatwick Airport                         13A   On time
##        via Guildford                           
## 09:18  Plymouth                                7     On time
## 09:22  Ealing Broadway                         14    On time
## 09:25  London Paddington                       15A   On time
## 09:29  Bristol Temple Meads                    7     On time
## 09:30  London Paddington                       15    On time
## 09:38  Basingstoke                             13B   On time
## 09:41  London Paddington                       15    On time
## 09:41  Redhill                                 6     On time
## 09:44  Bedwyn                                  1     On time
## 09:52  Ealing Broadway                         14    On time
## 08:05  Virginia Water                          BUS   On time
## 08:24  Virginia Water                          BUS   On time
## 08:35  Virginia Water                          BUS   On time
## 08:54  Virginia Water                          BUS   On time
## 09:00  Heathrow Central Bus Stn                BUS   On time
## 09:05  Virginia Water                          BUS   On time
## 09:24  Virginia Water                          BUS   On time
## 09:35  Virginia Water                          BUS   On time
## 09:54  Virginia Water                          BUS   On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
```
