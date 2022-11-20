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

## Example (Last rendered on 2022-11-20 08:07)

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
## Reading (RDG) Station Board on 2022-11-20 08:07:51
## Time   From                                    Plat  Expected
## 08:11  Ealing Broadway                         14    08:28
## 08:13  Staines                                 4     08:15
## 08:35  Clapham Junction                        6     08:39
## 08:37  London Paddington                       7     On time
## 08:40  Ealing Broadway                         14    08:45
## 08:58  London Paddington                       7     On time
## 09:04  Didcot Parkway                          15    On time
## 09:04  London Paddington                       7     On time
## 09:05  Richmond                                4     On time
## 09:10  Swindon                                 11    On time
## 09:12  London Paddington                       14    On time
## 09:15  London Paddington                       12    On time
## 09:15  Newbury                                 3     On time
## 09:19  London Paddington                       7     On time
## 09:23  London Paddington                       7     On time
## 09:24  Oxford                                  11    On time
## 09:28  Bristol Parkway                         10    On time
## 09:35  Clapham Junction                        4     Delayed
## 09:37  London Paddington                       14    On time
## 09:39  Bristol Temple Meads                    11    On time
## 09:40  Gatwick Airport                         7A    On time
## 09:47  London Paddington                       9     On time
## 09:57  Worcester Foregate Street               10    On time
## 10:01  London Paddington                       9     On time
## 10:05  Clapham Junction                        4     On time
## 08:27  Heathrow Central Bus Stn                BUS   On time
## 09:04  Heathrow Central Bus Stn                BUS   On time
## 09:20  Basingstoke                             BUS   On time
## 09:34  Heathrow Central Bus Stn                BUS   On time
## 10:00  Basingstoke                             BUS   On time
## 10:04  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-20 08:07:53
## Time   To                                      Plat  Expected
## 08:06  Newbury                                 12B   On time
## 08:11  London Paddington                       13    On time
## 08:18  Gatwick Airport                         4     On time
##        via Guildford                           
## 08:21  Clapham Junction                        4     On time
## 08:22  Plymouth                                8     On time
## 08:24  Didcot Parkway                          13    On time
## 08:30  London Paddington                       14    08:35
## 08:34  Bedwyn                                  15    On time
## 08:39  Exeter St Davids                        7     On time
##        via Bristol                             
## 08:40  Redhill                                 15    On time
## 08:51  Clapham Junction                        6     On time
## 09:00  Ealing Broadway                         14    On time
## 09:00  Swansea                                 7     On time
## 09:06  Ealing Broadway                         15    On time
## 09:10  Great Malvern                           7     On time
## 09:11  London Paddington                       11    On time
## 09:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:18  Gatwick Airport                         13    On time
##        via Guildford                           
## 09:19  Didcot Parkway                          12    On time
## 09:20  Plymouth                                7     On time
## 09:21  Clapham Junction                        4     On time
## 09:25  London Paddington                       11    On time
## 09:29  Bristol Temple Meads                    7     On time
## 09:30  Ealing Broadway                         14    On time
## 09:32  London Paddington                       10    On time
## 09:41  Redhill                                 5     On time
## 09:43  Bedwyn                                  13    On time
## 09:44  London Paddington                       11    On time
## 09:49  Oxford                                  9     On time
## 09:55  Clapham Junction                        4     On time
## 10:00  Ealing Broadway                         14    On time
## 10:02  London Paddington                       10    On time
## 10:03  Carmarthen                              9     On time
## 08:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:00  Heathrow Airport T3 (Bus)               BUS   On time
## 09:08  Basingstoke                             BUS   On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:52  Winchester                              BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
```
