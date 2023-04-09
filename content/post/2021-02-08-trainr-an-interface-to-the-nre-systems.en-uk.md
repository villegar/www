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

## Example (Last rendered on 2023-04-09 08:03)

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
## Reading (RDG) Station Board on 2023-04-09 08:03:52
## Time   From                                    Plat  Expected
## 09:08  Didcot Parkway                          15A   On time
## 09:15  London Paddington                       12    On time
## 09:23  London Paddington                       7     On time
## 09:23  Swindon                                 10    On time
## 09:28  London Paddington                       14    On time
## 09:32  Virginia Water                          4     On time
## 09:37  Bristol Parkway                         10    On time
## 09:41  Gatwick Airport                         13    On time
## 09:53  London Paddington                       8     On time
## 09:56  London Paddington                       7     On time
## 09:57  Southampton Central                     -     On time
## 09:58  Didcot Parkway                          15    On time
## 09:58  London Paddington                       12    On time
## 10:02  Weybridge                               4     On time
## 10:09  Weston-super-Mare                       10A   On time
## 10:10  Redhill                                 6     On time
## 10:16  London Paddington                       13    On time
## 10:25  Swansea                                 11    On time
## 10:28  London Paddington                       14    On time
## 10:32  Virginia Water                          4     On time
## 10:38  Gatwick Airport                         5     On time
## 10:42  London Paddington                       9     On time
## 10:43  Didcot Parkway                          -     On time
## 10:45  Exeter St Davids                        11    On time
## 10:47  London Paddington                       8     On time
## 10:53  Bristol Parkway                         10    On time
## 10:53  London Paddington                       9     On time
## 10:58  London Paddington                       14    On time
## 11:02  Weybridge                               4     On time
## 09:04  Heathrow Central Bus Stn                BUS   On time
## 09:17  Newbury                                 BUS   On time
## 09:23  Basingstoke                             BUS   On time
## 09:34  Andover                                 BUS   On time
## 09:34  Heathrow Central Bus Stn                BUS   On time
## 09:45  Newbury                                 BUS   On time
## 10:00  Basingstoke                             BUS   On time
## 10:04  Heathrow Central Bus Stn                BUS   On time
## 10:34  Andover                                 BUS   On time
## 10:34  Heathrow Central Bus Stn                BUS   On time
## 10:53  Bramley (Hampshire)                     BUS   On time
## 11:00  Winchester                              BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-04-09 08:03:57
## Time   To                                      Plat  Expected
## 09:10  Ealing Broadway                         15A   On time
## 09:15  Didcot Parkway                          8     On time
## 09:18  Didcot Parkway                          12    On time
## 09:21  Gatwick Airport                         13B   On time
##        via Guildford                           
## 09:24  Ealing Broadway                         14    On time
## 09:24  Virginia Water                          4     On time
## 09:26  London Paddington                       10    On time
## 09:29  Bristol Temple Meads                    7     On time
## 09:31  London Paddington                       15    On time
## 09:40  London Paddington                       10    On time
## 09:41  Redhill                                 6     On time
## 09:53  Ealing Broadway                         14    On time
## 09:54  Weybridge                               4     On time
## 09:55  Penzance                                8     On time
## 09:58  Carmarthen                              7     On time
## 10:11  London Paddington                       10A   On time
## 10:14  Ealing Broadway                         15    On time
## 10:15  Didcot Parkway                          -     On time
## 10:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:22  Ealing Broadway                         12    On time
## 10:24  Virginia Water                          4     On time
## 10:26  Didcot Parkway                          13    On time
## 10:27  London Paddington                       11    On time
## 10:41  Redhill                                 6     On time
## 10:43  Bristol Parkway                         9     On time
## 10:46  Bournemouth                             15    On time
## 10:46  Bournemouth                             -     On time
## 10:46  London Paddington                       11    On time
## 10:49  Didcot Parkway                          8     On time
## 10:54  Ealing Broadway                         14    On time
## 10:54  London Paddington                       10    On time
## 10:54  Weybridge                               4     On time
## 10:55  Bristol Temple Meads                    9     On time
## 09:08  Basingstoke                             BUS   On time
## 09:30  Andover                                 BUS   On time
## 09:30  Heathrow Airport T3 (Bus)               BUS   On time
## 09:43  Bedwyn                                  BUS   On time
## 09:52  Winchester                              BUS   On time
## 10:00  Heathrow Airport T3 (Bus)               BUS   On time
## 10:30  Andover                                 BUS   On time
## 10:30  Heathrow Airport T3 (Bus)               BUS   On time
## 10:38  Basingstoke                             BUS   On time
## 10:43  Newbury                                 BUS   On time
## 11:00  Heathrow Airport T3 (Bus)               BUS   On time
```
