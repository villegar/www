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

## Example (Last rendered on 2022-04-15 08:04)

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
## Reading (RDG) Station Board on 2022-04-15 08:04:14
## Time   From                                    Plat  Expected
## 09:01  Didcot Parkway                          15A   On time
## 09:04  Redhill                                 6     On time
## 09:05  Bournemouth                             8     On time
## 09:09  Bedwyn                                  11A   09:11
## 09:09  Taunton                                 10A   09:14
## 09:11  London Paddington                       9     On time
## 09:13  London Paddington                       14    On time
## 09:14  London Paddington                       12B   On time
## 09:14  Moreton-in-Marsh                        11A   On time
## 09:16  London Paddington                       9B    On time
## 09:19  Swansea                                 10    09:23
## 09:24  Gatwick Airport                         6     On time
## 09:24  Oxford                                  10A   On time
## 09:25  London Paddington                       9     On time
## 09:27  London Paddington                       7     On time
## 09:30  Penzance                                11    09:37
## 09:32  Hereford                                10A   On time
## 09:32  London Paddington                       7B    On time
## 09:37  Didcot Parkway                          15A   On time
## 09:39  Taunton                                 10    On time
## 09:40  Nottingham                              7     On time
## 09:43  London Paddington                       14    On time
## 09:44  London Paddington                       12B   On time
## 09:45  Swansea                                 10    09:47
## 09:46  Basingstoke                             2     On time
## 09:46  London Paddington                       9     On time
## 09:52  London Paddington                       8B    On time
## 09:54  Gatwick Airport                         4     On time
## 09:55  Moreton-in-Marsh                        10    On time
## 09:55  Newbury                                 1     On time
## 09:56  London Paddington                       9     On time
## 10:00  London Paddington                       8     On time
## 10:01  Plymouth                                11    On time
## 10:05  Didcot Parkway                          13A   On time
## 10:06  Swansea                                 10    On time
## 10:11  London Paddington                       9     On time
## 10:12  Newbury                                 11A   On time
## 10:13  London Paddington                       14    On time
## 10:14  Bristol Temple Meads                    10    On time
## 10:15  London Paddington                       12B   On time
## 10:17  London Paddington                       9B    On time
## 10:19  Basingstoke                             2     On time
## 10:23  Oxford                                  11    On time
## 10:25  London Paddington                       9     On time
## 10:28  Cheltenham Spa                          10A   On time
## 10:33  London Paddington                       7B    On time
## 10:35  Newbury                                 1     On time
## 10:36  Didcot Parkway                          15A   On time
## 10:39  Bristol Temple Meads                    10    On time
## 10:41  London Paddington                       9     On time
## 10:43  London Paddington                       14    On time
## 10:44  Manchester Piccadilly                   8     On time
## 10:45  Carmarthen                              11    On time
## 10:45  London Paddington                       13B   On time
## 10:45  Redhill                                 4     On time
## 10:46  London Paddington                       9B    On time
## 10:49  Newbury                                 3     On time
## 10:52  London Paddington                       9B    On time
## 10:53  Gatwick Airport                         6     On time
## 10:54  Moreton-in-Marsh                        10A   On time
## 10:55  Basingstoke                             2     On time
## 10:55  London Paddington                       8     On time
## 10:59  London Paddington                       7     On time
## 09:05  Staines                                 BUS   On time
## 09:07  Staines                                 BUS   On time
## 09:33  Staines                                 BUS   On time
## 09:37  Staines                                 BUS   On time
## 09:45  Heathrow Central Bus Stn                BUS   On time
## 10:03  Staines                                 BUS   On time
## 10:07  Staines                                 BUS   On time
## 10:33  Staines                                 BUS   On time
## 10:37  Staines                                 BUS   On time
## 10:45  Heathrow Central Bus Stn                BUS   On time
## 11:03  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-04-15 08:04:17
## Time   To                                      Plat  Expected
## 09:01  Gatwick Airport                         5     09:03
##        via Guildford                           
## 09:08  Ealing Broadway                         15A   On time
## 09:11  London Paddington                       11A   09:12
## 09:13  London Paddington                       10A   09:15
## 09:13  Manchester Piccadilly                   8     On time
##        via Stoke-on-Trent                      
## 09:13  Newbury                                 3     On time
## 09:13  Swansea                                 9     On time
## 09:16  London Paddington                       11A   On time
## 09:18  Moreton-in-Marsh                        9B    On time
## 09:20  Redhill                                 6     On time
## 09:21  London Paddington                       10    09:24
## 09:22  Ealing Broadway                         14    On time
## 09:23  Didcot Parkway                          12B   On time
## 09:26  London Paddington                       10A   On time
## 09:27  Bristol Temple Meads                    9     On time
## 09:29  Plymouth                                7     On time
## 09:32  Basingstoke                             1     On time
## 09:32  London Paddington                       11    09:38
## 09:35  London Paddington                       10A   On time
## 09:36  Bedwyn                                  7B    On time
## 09:42  London Paddington                       10    On time
## 09:45  Ealing Broadway                         15A   On time
## 09:47  London Paddington                       10    09:47
## 09:48  Oxford                                  9     On time
## 09:52  Ealing Broadway                         14    On time
## 09:54  Cheltenham Spa                          8B    On time
## 09:55  Didcot Parkway                          12B   On time
## 09:57  London Paddington                       10    On time
## 09:58  Bristol Temple Meads                    9     On time
## 10:02  Paignton                                8     On time
## 10:04  Gatwick Airport                         6     On time
##        via Guildford                           
## 10:04  London Paddington                       11    On time
## 10:07  Basingstoke                             2     On time
## 10:08  London Paddington                       10    On time
## 10:12  Newbury                                 1     On time
## 10:13  London Paddington                       11A   On time
## 10:13  Swansea                                 9     On time
## 10:15  Ealing Broadway                         13A   On time
## 10:15  Manchester Piccadilly                   7     On time
##        via Stoke-on-Trent                      
## 10:17  London Paddington                       10    On time
## 10:19  Moreton-in-Marsh                        9B    On time
## 10:20  Redhill                                 4     On time
## 10:22  Ealing Broadway                         14    On time
## 10:23  Didcot Parkway                          12B   On time
## 10:26  London Paddington                       11    On time
## 10:27  Bristol Temple Meads                    9     On time
## 10:29  Penzance                                7     On time
## 10:32  Basingstoke                             2     On time
## 10:34  London Paddington                       10A   On time
## 10:38  Bedwyn                                  7B    On time
## 10:38  Ealing Broadway                         15A   On time
## 10:42  London Paddington                       10    On time
## 10:43  Cardiff Central                         9     On time
## 10:48  London Paddington                       11    On time
## 10:48  Oxford                                  9B    On time
## 10:52  Bournemouth                             8     On time
## 10:52  Ealing Broadway                         14    On time
## 10:53  Cheltenham Spa                          9B    On time
## 10:53  Didcot Parkway                          13B   On time
## 10:57  London Paddington                       10A   On time
## 10:58  Bristol Temple Meads                    8     On time
## 11:01  Exeter St Davids                        7     On time
## 11:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 09:13  Staines                                 BUS   On time
## 09:13  Staines                                 BUS   On time
## 09:43  Staines                                 BUS   On time
## 09:43  Staines                                 BUS   On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
## 10:13  Staines                                 BUS   On time
## 10:13  Staines                                 BUS   On time
## 10:43  Staines                                 BUS   On time
## 10:43  Staines                                 BUS   On time
## 11:00  Heathrow Central Bus Stn                BUS   On time
```
