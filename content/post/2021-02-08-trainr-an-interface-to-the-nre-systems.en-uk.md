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

## Example (Last rendered on 2023-03-26 18:03)

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
## Reading (RDG) Station Board on 2023-03-26 18:03:19
## Time   From                                    Plat  Expected
## 18:59  Penzance                                11    19:20
## 19:02  Didcot Parkway                          10A   On time
## 19:03  Abbey Wood                              14    On time
## 19:06  Bournemouth                             8     On time
## 19:07  London Paddington                       9     On time
## 19:08  Guildford                               15    19:10
## 19:11  Taunton                                 11    19:13
## 19:13  Didcot Parkway                          13A   On time
## 19:13  London Paddington                       12B   On time
## 19:19  Bedwyn                                  1     On time
## 19:19  London Paddington                       8     On time
## 19:23  London Paddington                       9     On time
## 19:26  London Paddington                       7     On time
## 19:32  Basingstoke                             2     On time
## 19:33  Abbey Wood                              14    On time
## 19:38  Guildford                               5     On time
## 19:39  Didcot Parkway                          7     On time
## 19:39  London Paddington                       9     On time
## 19:39  Paignton                                11    19:46
## 19:47  London Paddington                       8     On time
## 19:48  Swansea                                 10    On time
## 19:53  London Paddington                       9     On time
## 19:57  Penzance                                11    On time
## 20:02  Didcot Parkway                          10A   On time
## 20:04  Abbey Wood                              14    On time
## 20:07  London Paddington                       8     On time
## 20:08  Guildford                               15    On time
## 20:12  Exeter St Davids                        11    On time
## 20:13  Didcot Parkway                          13    On time
## 20:19  London Paddington                       9     On time
## 20:19  London Paddington                       12    On time
## 20:20  Newbury                                 1     On time
## 20:27  London Paddington                       7     On time
## 20:32  Basingstoke                             2     On time
## 20:33  Abbey Wood                              14    On time
## 20:38  Guildford                               5     On time
## 20:39  Didcot Parkway                          8     On time
## 20:41  Plymouth                                11    On time
## 20:46  London Paddington                       9     On time
## 20:49  Swansea                                 10    On time
## 20:58  Penzance                                11    On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:26  Staines                                 -     Cancelled
## 19:27  Staines                                 -     Cancelled
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:56  Staines                                 BUS   On time
## 19:57  Staines                                 -     Cancelled
## 19:58  Heathrow Central Bus Stn                BUS   On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:26  Staines                                 BUS   On time
## 20:27  Staines                                 BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
## 20:56  Staines                                 BUS   On time
## 20:57  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-03-26 18:03:24
## Time   To                                      Plat  Expected
## 19:00  London Paddington                       11    19:21
## 19:05  London Paddington                       10A   On time
## 19:09  Swansea                                 9     On time
## 19:13  Ealing Broadway                         13A   On time
## 19:15  Didcot Parkway                          8     On time
## 19:15  London Paddington                       11    On time
## 19:20  Didcot Parkway                          8     On time
## 19:21  Guildford                               5     On time
## 19:24  Abbey Wood                              14    On time
## 19:25  Bristol Temple Meads                    9     On time
## 19:28  Didcot Parkway                          12B   On time
## 19:28  Plymouth                                7     On time
## 19:37  Basingstoke                             2     On time
## 19:40  Swindon                                 9     On time
## 19:42  London Paddington                       11    19:47
## 19:43  Bedwyn                                  1     On time
## 19:50  Hereford                                8     On time
## 19:50  London Paddington                       10    On time
## 19:52  Bournemouth                             7     On time
## 19:54  Abbey Wood                              14    On time
## 19:55  Bristol Temple Meads                    9     On time
## 19:58  London Paddington                       11    On time
## 20:05  London Paddington                       10A   On time
## 20:09  Swansea                                 8     On time
## 20:13  Guildford                               5     On time
## 20:14  Ealing Broadway                         13    On time
## 20:15  Didcot Parkway                          12    On time
## 20:15  London Paddington                       11    On time
## 20:24  Abbey Wood                              14    On time
## 20:25  Didcot Parkway                          9     On time
## 20:28  Didcot Parkway                          12    On time
## 20:28  Plymouth                                7     On time
## 20:37  Basingstoke                             2     On time
## 20:42  London Paddington                       11    On time
## 20:43  Newbury                                 1     On time
## 20:50  London Paddington                       10    On time
## 20:52  Bournemouth                             8     On time
## 20:54  Abbey Wood                              14    On time
## 20:55  Weston-super-Mare                       9     On time
## 20:59  London Paddington                       11    On time
## 19:25  Staines                                 BUS   On time
## 19:27  Staines                                 BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:55  Staines                                 -     Cancelled
## 19:57  Staines                                 -     Cancelled
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
## 20:25  Staines                                 -     Cancelled
## 20:27  Staines                                 BUS   On time
## 20:55  Staines                                 BUS   On time
## 20:57  Staines                                 BUS   On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
```
