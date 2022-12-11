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

## Example (Last rendered on 2022-12-11 16:04)

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
## Reading (RDG) Station Board on 2022-12-11 16:04:01
## Time   From                                    Plat  Expected
## 15:58  Exeter St Davids                        11    On time
## 16:02  Ascot                                   4     On time
## 16:03  Abbey Wood                              14    On time
## 16:05  London Paddington                       9     16:01
## 16:08  Guildford                               6     16:11
## 16:10  Bristol Temple Meads                    10    16:14
## 16:10  London Paddington                       8B    On time
## 16:12  Newbury                                 3     On time
## 16:13  Didcot Parkway                          15A   On time
## 16:16  Salisbury                               1     16:19
## 16:17  London Paddington                       9     On time
## 16:20  London Paddington                       12B   16:23
## 16:25  Oxford                                  10A   On time
## 16:26  London Paddington                       7     On time
## 16:31  Cheltenham Spa                          10A   16:33
## 16:32  Ascot                                   4     On time
## 16:32  Basingstoke                             2     On time
## 16:33  Abbey Wood                              14    On time
## 16:38  Guildford                               5     On time
## 16:39  Manchester Piccadilly                   13    16:54
## 16:40  Bristol Temple Meads                    11    On time
## 16:44  Swansea                                 10A   On time
## 16:45  London Paddington                       8B    On time
## 16:48  London Paddington                       9     On time
## 16:57  Hereford                                10A   On time
## 16:58  London Paddington                       7     On time
## 16:58  Penzance                                11    On time
## 17:02  Ascot                                   4     On time
## 17:03  Abbey Wood                              14    On time
## 17:05  London Paddington                       9     On time
## 17:06  Southampton Central                     8     On time
## 17:08  Guildford                               6     On time
## 17:09  Weston-super-Mare                       10    On time
## 17:13  Didcot Parkway                          15A   On time
## 17:13  London Paddington                       9     On time
## 17:18  London Paddington                       9     On time
## 17:21  London Paddington                       12B   On time
## 17:23  Bedwyn                                  3     On time
## 17:25  Oxford                                  10A   On time
## 17:27  London Paddington                       7     On time
## 17:32  Ascot                                   4     On time
## 17:32  Basingstoke                             2     On time
## 17:33  Abbey Wood                              14    On time
## 17:36  Paignton                                11    On time
## 17:38  Guildford                               5     On time
## 17:39  Manchester Piccadilly                   8B    On time
## 17:40  Bristol Temple Meads                    10    On time
## 17:45  London Paddington                       7     On time
## 17:46  Swansea                                 11    On time
## 17:48  London Paddington                       9     On time
## 17:56  Hereford                                -     Cancelled
## 17:56  London Paddington                       8     On time
## 17:57  Plymouth                                11    On time
## 18:02  Ascot                                   4     On time
## 18:03  Abbey Wood                              14    On time
## 16:04  Heathrow Central Bus Stn                BUS   On time
## 16:34  Heathrow Central Bus Stn                BUS   On time
## 17:04  Heathrow Central Bus Stn                BUS   On time
## 17:34  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-11 16:04:06
## Time   To                                      Plat  Expected
## 16:00  London Paddington                       11    16:02
## 16:09  Swansea                                 9     On time
## 16:13  London Paddington                       10    16:15
## 16:14  Ealing Broadway                         15A   On time
## 16:14  Hereford                                8B    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:21  Guildford                               5     On time
## 16:24  Abbey Wood                              14    On time
## 16:24  Ascot                                   4     On time
## 16:25  Bristol Temple Meads                    9     On time
## 16:25  Didcot Parkway                          12B   On time
## 16:25  London Paddington                       10A   On time
## 16:28  Penzance                                7     On time
## 16:32  London Paddington                       10A   16:34
## 16:33  Salisbury                               1     On time
## 16:37  Basingstoke                             2     On time
## 16:41  Guildford                               6     On time
## 16:42  London Paddington                       11    On time
## 16:43  Newbury                                 3     On time
## 16:46  London Paddington                       10A   On time
## 16:48  Oxford                                  8B    On time
## 16:54  Abbey Wood                              14    On time
## 16:54  Ascot                                   4     On time
## 16:55  Plymouth                                9     On time
##        via Bristol                             
## 16:57  London Paddington                       10A   On time
## 17:01  Plymouth                                7     On time
## 17:02  London Paddington                       11    On time
## 17:09  Swansea                                 9     On time
## 17:13  London Paddington                       10    On time
## 17:14  Ealing Broadway                         15A   On time
## 17:14  Great Malvern                           9     On time
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 17:21  Guildford                               5     On time
## 17:24  Abbey Wood                              14    On time
## 17:24  Ascot                                   4     On time
## 17:25  Bristol Temple Meads                    9     On time
## 17:25  Didcot Parkway                          12B   On time
## 17:26  London Paddington                       10A   On time
## 17:28  Penzance                                7     On time
## 17:37  Basingstoke                             2     On time
## 17:41  Guildford                               6     On time
## 17:43  Bedwyn                                  3     On time
## 17:43  London Paddington                       11    On time
## 17:46  London Paddington                       10    On time
## 17:48  London Paddington                       11    On time
## 17:48  Oxford                                  7     On time
## 17:52  Southampton Central                     8B    On time
## 17:54  Abbey Wood                              14    On time
## 17:54  Ascot                                   4     On time
## 17:55  Weston-super-Mare                       9     On time
## 17:57  London Paddington                       -     Cancelled
## 17:58  Cheltenham Spa                          8     On time
## 18:02  London Paddington                       11    On time
## 16:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:00  Heathrow Airport T3 (Bus)               BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
```
