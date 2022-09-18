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

## Example (Last rendered on 2022-09-18 08:04)

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
## Reading (RDG) Station Board on 2022-09-18 08:04:20
## Time   From                                    Plat  Expected
## 09:02  Richmond                                4     On time
## 09:04  Didcot Parkway                          15    On time
## 09:07  London Paddington                       12B   On time
## 09:10  Swindon                                 15    On time
## 09:12  London Paddington                       12    On time
## 09:14  London Paddington                       7     On time
## 09:15  Newbury                                 3     On time
## 09:23  London Paddington                       9     On time
## 09:24  Oxford                                  13    On time
## 09:28  Bristol Parkway                         10    On time
## 09:33  Basingstoke                             2     On time
## 09:33  Clapham Junction                        4     On time
## 09:33  London Paddington                       14    On time
## 09:39  Bristol Temple Meads                    10    On time
## 09:40  Gatwick Airport                         13    On time
## 09:45  London Paddington                       9     On time
## 09:47  Salisbury                               1     On time
## 09:57  Worcester Foregate Street               10A   On time
## 09:58  Didcot Parkway                          15    On time
## 10:00  London Paddington                       9     On time
## 10:03  London Paddington                       14    On time
## 10:03  London Waterloo                         4     On time
## 10:05  Southampton Central                     12B   On time
## 10:08  Redhill                                 6     On time
## 10:09  Weston-super-Mare                       10    On time
## 10:10  London Paddington                       9     On time
## 10:16  London Paddington                       13    On time
## 10:25  Swansea                                 11    On time
## 10:26  London Paddington                       7     On time
## 10:30  Bedwyn                                  13    On time
## 10:33  Basingstoke                             2     On time
## 10:33  London Paddington                       14    On time
## 10:33  London Waterloo                         4     On time
## 10:38  Gatwick Airport                         5     On time
## 10:39  Birmingham New Street                   13    On time
## 10:41  Exeter St Davids                        11    On time
## 10:42  London Paddington                       9     On time
## 10:45  London Paddington                       8     On time
## 10:47  Salisbury                               1     On time
## 10:53  Bristol Parkway                         10    On time
## 10:53  London Paddington                       9     On time
## 10:57  Great Malvern                           11    On time
## 10:59  London Paddington                       7     On time
## 11:03  London Paddington                       14    On time
## 11:03  London Waterloo                         4     On time
## 09:45  Heathrow Central Bus Stn                BUS   On time
## 10:45  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-09-18 08:04:24
## Time   To                                      Plat  Expected
## 09:06  Ealing Broadway                         15    On time
## 09:09  Great Malvern                           12B   On time
## 09:11  London Paddington                       15    On time
## 09:12  Salisbury                               1     On time
## 09:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:18  Didcot Parkway                          12    On time
## 09:18  Penzance                                7     On time
## 09:20  Gatwick Airport                         13    On time
##        via Guildford                           
## 09:24  Ealing Broadway                         14    On time
## 09:24  London Waterloo                         4     On time
## 09:25  London Paddington                       13    On time
## 09:29  Weston-super-Mare                       9     On time
## 09:30  London Paddington                       10    On time
## 09:38  Basingstoke                             2     On time
## 09:41  London Paddington                       10    On time
## 09:41  Redhill                                 5     On time
## 09:43  Bedwyn                                  1     On time
## 09:48  Oxford                                  9     On time
## 09:52  Bournemouth                             8     On time
## 09:54  Ealing Broadway                         14    On time
## 09:54  London Waterloo                         4     On time
## 09:59  London Paddington                       10A   On time
## 10:03  Carmarthen                              9     On time
## 10:11  Hereford                                9     On time
## 10:11  London Paddington                       10    On time
## 10:12  Salisbury                               1     On time
## 10:14  Ealing Broadway                         15    On time
## 10:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 10:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:24  Ealing Broadway                         14    On time
## 10:24  London Waterloo                         4     On time
## 10:26  Didcot Parkway                          13    On time
## 10:27  London Paddington                       11    On time
## 10:28  Penzance                                7     On time
## 10:38  Basingstoke                             2     On time
## 10:41  Redhill                                 6     On time
## 10:43  Bristol Parkway                         9     On time
## 10:43  Newbury                                 3     On time
## 10:46  London Paddington                       11    On time
## 10:48  Oxford                                  8     On time
## 10:54  Ealing Broadway                         14    On time
## 10:54  London Paddington                       10    On time
## 10:54  London Waterloo                         4     On time
## 10:55  Weston-super-Mare                       9     On time
## 10:59  London Paddington                       11    On time
## 11:01  Paignton                                7     On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
## 11:00  Heathrow Central Bus Stn                BUS   On time
```
