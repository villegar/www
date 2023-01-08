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

## Example (Last rendered on 2023-01-08 18:03)

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
## Reading (RDG) Station Board on 2023-01-08 18:03:31
## Time   From                                    Plat  Expected
## 17:57  Hereford                                10A   18:00
## 17:57  Plymouth                                11    On time
## 18:03  Abbey Wood                              14    On time
## 18:08  Redhill                                 6     On time
## 18:12  London Paddington                       9     On time
## 18:13  Didcot Parkway                          15    On time
## 18:13  London Paddington                       12    On time
## 18:16  London Paddington                       7     On time
## 18:21  Newbury                                 1     On time
## 18:25  Oxford                                  10    On time
## 18:26  London Paddington                       7     On time
## 18:27  Plymouth                                11    On time
## 18:33  Abbey Wood                              14    On time
## 18:33  Basingstoke                             2     On time
## 18:35  Carmarthen                              10    On time
## 18:35  Virginia Water                          4     On time
## 18:38  Gatwick Airport                         5     On time
## 18:38  London Paddington                       7     On time
## 18:39  Macclesfield                            12    On time
## 18:45  London Paddington                       8     On time
## 18:50  Gillingham (Dorset)                     1     On time
## 18:56  Great Malvern                           10    On time
## 18:58  London Waterloo                         4     On time
## 18:58  Penzance                                11    On time
## 18:59  London Paddington                       7     On time
## 19:03  Abbey Wood                              14    19:09
## 19:06  Bournemouth                             8     On time
## 19:08  Redhill                                 15    On time
## 19:12  London Paddington                       9     On time
## 19:13  Didcot Parkway                          13    On time
## 19:13  London Paddington                       12    On time
## 19:16  London Paddington                       7     On time
## 19:19  Bedwyn                                  1     On time
## 19:25  Oxford                                  10    On time
## 19:26  London Paddington                       7     On time
## 19:28  Bristol Temple Meads                    11    On time
## 19:33  Abbey Wood                              14    On time
## 19:33  Basingstoke                             2     On time
## 19:35  Virginia Water                          4     On time
## 19:38  Gatwick Airport                         5     On time
## 19:38  London Paddington                       8     On time
## 19:39  Manchester Piccadilly                   7B    On time
## 19:44  Paignton                                10    On time
## 19:45  London Paddington                       9     On time
## 19:49  Salisbury                               1     On time
## 19:49  Swansea                                 11    On time
## 19:55  Hereford                                10    On time
## 19:57  Penzance                                11    On time
## 19:58  London Waterloo                         4     On time
## 18:04  Heathrow Central Bus Stn                BUS   On time
## 18:34  Heathrow Central Bus Stn                BUS   On time
## 18:50  Chippenham                              BUS   On time
## 19:00  Swindon                                 BUS   On time
## 19:04  Heathrow Central Bus Stn                BUS   On time
## 19:32  Heathrow Central Bus Stn                BUS   On time
## 19:50  Chippenham                              BUS   On time
## 19:58  Heathrow Central Bus Stn                BUS   On time
## 20:00  Swindon                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2023-01-08 18:03:34
## Time   To                                      Plat  Expected
## 17:59  London Paddington                       11    18:01
## 18:01  London Paddington                       10A   18:03
## 18:12  Salisbury                               1     On time
## 18:14  Ealing Broadway                         15    On time
## 18:14  Great Malvern                           9     On time
## 18:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 18:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:22  Swansea                                 7     On time
## 18:24  Abbey Wood                              14    On time
## 18:24  Virginia Water                          4     On time
## 18:25  Didcot Parkway                          12    On time
## 18:27  London Paddington                       10    On time
## 18:28  Penzance                                7     On time
## 18:32  London Paddington                       11    On time
## 18:37  Basingstoke                             2     On time
## 18:41  Redhill                                 6     On time
## 18:42  London Paddington                       10    On time
## 18:42  Weston-super-Mare                       7     On time
## 18:46  Newbury                                 1     On time
## 18:48  Oxford                                  8     On time
## 18:51  London Waterloo                         4     On time
## 18:54  Abbey Wood                              14    On time
## 19:00  London Paddington                       11    On time
## 19:02  London Paddington                       10    On time
## 19:02  Plymouth                                7     On time
## 19:12  Salisbury                               1     On time
## 19:13  Ealing Broadway                         13    On time
## 19:14  Hereford                                9     On time
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:22  Swansea                                 7     On time
## 19:24  Abbey Wood                              14    On time
## 19:24  Virginia Water                          4     On time
## 19:25  Didcot Parkway                          12    On time
## 19:27  London Paddington                       10    On time
## 19:30  Plymouth                                7     On time
## 19:32  London Paddington                       11    On time
## 19:37  Basingstoke                             2     On time
## 19:42  Bristol Temple Meads                    8     On time
## 19:45  London Paddington                       10    On time
## 19:46  Bedwyn                                  1     On time
## 19:48  Oxford                                  9     On time
## 19:50  London Paddington                       11    On time
## 19:51  London Waterloo                         4     On time
## 19:52  Bournemouth                             7B    On time
## 19:54  Abbey Wood                              14    On time
## 19:58  London Paddington                       11    On time
## 20:01  London Paddington                       10    On time
## 18:05  Swindon                                 BUS   On time
## 18:15  Chippenham                              BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:05  Swindon                                 BUS   On time
## 19:25  Chippenham                              BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
```
