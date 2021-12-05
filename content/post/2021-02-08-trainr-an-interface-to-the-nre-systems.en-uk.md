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

## Example (Last rendered on 2021-12-05 08:04)

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
## Reading (RDG) Station Board on 2021-12-05 08:04:02
## Time   From                                    Plat  Expected
## 08:05  Staines                                 4     On time
## 08:08  London Paddington                       14    08:14
## 08:28  London Paddington                       7     On time
## 08:33  Basingstoke                             -     Cancelled
## 08:57  London Waterloo                         4     On time
## 09:00  London Paddington                       7B    On time
## 09:00  Salisbury                               1     On time
## 09:14  London Paddington                       14    On time
## 09:17  Didcot Parkway                          15    On time
## 09:23  London Paddington                       7     On time
## 09:24  London Paddington                       12    On time
## 09:25  Newbury                                 3     On time
## 09:27  London Paddington                       9     On time
## 09:27  London Waterloo                         4     On time
## 09:29  Bristol Parkway                         10    09:40
## 09:33  Basingstoke                             2     On time
## 09:38  Gatwick Airport                         13    On time
## 09:46  London Paddington                       14    On time
## 09:47  Salisbury                               1     On time
## 10:03  London Waterloo                         4     On time
## 08:21  Heathrow Central Bus Stn                BUS   On time
## 09:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-12-05 08:04:04
## Time   To                                      Plat  Expected
## 07:38  Basingstoke                             -     Delayed
## 08:10  London Paddington                       15    On time
## 08:10  Newbury                                 7     On time
## 08:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 08:21  London Waterloo                         4     On time
## 08:24  London Paddington                       14    On time
## 08:33  Exeter St Davids                        7     On time
## 08:34  Bedwyn                                  13    On time
## 08:38  Basingstoke                             -     Cancelled
## 08:38  Didcot Parkway                          14    On time
## 08:40  Redhill                                 15    On time
## 08:51  London Waterloo                         6     On time
## 08:54  Ealing Broadway                         14    On time
## 09:05  Swansea                                 7B    On time
## 09:12  Salisbury                               1     On time
## 09:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:18  Ealing Broadway                         15    On time
## 09:18  Gatwick Airport                         13A   On time
##        via Guildford                           
## 09:21  London Waterloo                         4     On time
## 09:22  Ealing Broadway                         14    On time
## 09:25  Penzance                                7     On time
## 09:32  Weston-super-Mare                       9     On time
## 09:33  Didcot Parkway                          12    On time
## 09:38  Basingstoke                             2     On time
## 09:40  London Paddington                       10    09:45
## 09:41  Redhill                                 6     On time
## 09:44  Bedwyn                                  12    On time
## 09:52  Southampton Central                     8     On time
## 09:54  Ealing Broadway                         14    On time
## 09:54  London Waterloo                         4     On time
## 09:00  Heathrow Central Bus Stn                BUS   On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
```
