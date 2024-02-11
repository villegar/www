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

## Example (Last rendered on 2024-02-11 17:06)

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
## Reading (RDG) Station Board on 2024-02-11 17:06:34.174731
## Time   From                                    Plat  Expected
## 16:56  Hereford                                10    17:03
## 16:58  Penzance                                11    On time
## 17:00  Birmingham New Street                   13    17:05
## 17:07  Southampton Central                     8     17:12
## 17:08  London Paddington                       9     On time
## 17:09  Weston-super-Mare                       10    17:15
## 17:10  Abbey Wood                              14    On time
## 17:13  London Paddington                       9     On time
## 17:15  London Paddington                       12    On time
## 17:20  Bedwyn                                  3     On time
## 17:21  Swindon                                 11    On time
## 17:22  Oxford                                  15A   On time
## 17:23  London Paddington                       9     On time
## 17:26  London Paddington                       7     On time
## 17:32  Basingstoke                             2     On time
## 17:35  Bristol Temple Meads                    10    On time
## 17:35  Didcot Parkway                          15    On time
## 17:36  Paignton                                11    17:51
## 17:38  London Paddington                       9     On time
## 17:39  Manchester Piccadilly                   8B    17:47
## 17:40  Abbey Wood                              14    On time
## 17:44  Carmarthen                              10    17:54
## 17:45  London Paddington                       9B    On time
## 17:48  Yeovil Pen Mill                         2     On time
## 17:53  London Paddington                       9     On time
## 17:56  London Paddington                       8     On time
## 17:58  Hereford                                10    On time
## 17:58  Plymouth                                11    On time
## 18:06  Bournemouth                             8B    On time
## 18:08  London Paddington                       9     On time
## 18:09  Plymouth                                10    18:13
## 18:10  Abbey Wood                              14    On time
## 18:13  London Paddington                       9     On time
## 18:15  London Paddington                       12    On time
## 18:16  London Paddington                       7     On time
## 18:21  Newbury                                 1     On time
## 18:22  Cardiff Central                         10    On time
## 18:22  Oxford                                  15A   On time
## 18:26  London Paddington                       7     On time
## 18:29  Cheltenham Spa                          10    On time
## 18:32  Basingstoke                             2     On time
## 18:35  Bristol Temple Meads                    11    On time
## 18:35  Didcot Parkway                          15    On time
## 18:38  London Paddington                       9     On time
## 18:40  Abbey Wood                              14    On time
## 18:40  Manchester Piccadilly                   7     On time
## 18:44  Swansea                                 10    On time
## 18:45  London Paddington                       8B    On time
## 18:47  Gillingham (Dorset)                     2     On time
## 18:53  London Paddington                       9     On time
## 18:58  Penzance                                11    On time
## 18:59  Great Malvern                           10A   On time
## 18:59  London Paddington                       7     On time
## 17:05  Guildford                               BUS   On time
## 17:12  Ascot                                   BUS   On time
## 17:18  Heathrow Airport T3 (Bus)               BUS   On time
## 17:28  Ascot                                   BUS   On time
## 17:42  Ascot                                   BUS   On time
## 17:48  Heathrow Airport T3 (Bus)               BUS   On time
## 17:55  Gatwick Airport                         BUS   On time
## 17:58  Ascot                                   BUS   On time
## 18:05  Guildford                               BUS   On time
## 18:12  Ascot                                   BUS   On time
## 18:18  Heathrow Airport T3 (Bus)               BUS   On time
## 18:28  Ascot                                   BUS   On time
## 18:42  Ascot                                   BUS   On time
## 18:48  Heathrow Airport T3 (Bus)               BUS   On time
## 18:55  Gatwick Airport                         BUS   On time
## 18:58  Ascot                                   BUS   On time
## 19:05  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-02-11 17:06:36.841739
## Time   To                                      Plat  Expected
## 16:56  London Paddington                       10    17:07
## 17:01  London Paddington                       11    17:07
## 17:10  Swansea                                 9     On time
## 17:11  London Paddington                       10    17:16
## 17:12  Salisbury                               2     On time
## 17:14  Great Malvern                           9     On time
## 17:14  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 17:22  London Paddington                       11    On time
## 17:23  London Paddington                       15A   On time
## 17:25  Bristol Temple Meads                    9     On time
## 17:25  Didcot Parkway                          12    On time
## 17:28  Penzance                                7     On time
## 17:29  Abbey Wood                              14    On time
## 17:35  London Paddington                       10    On time
## 17:37  Basingstoke                             2     On time
## 17:37  London Paddington                       15    On time
## 17:40  London Paddington                       11    17:52
## 17:40  Swindon                                 9     On time
## 17:42  Birmingham New Street                   13B   On time
##        via Coventry                            
## 17:45  Bedwyn                                  3     On time
## 17:46  London Paddington                       10    17:55
## 17:48  Oxford                                  9B    On time
## 17:52  Bournemouth                             8B    On time
## 17:55  Weston-super-Mare                       9     On time
## 17:58  Cheltenham Spa                          8     On time
## 17:59  Abbey Wood                              14    On time
## 17:59  London Paddington                       10    On time
## 17:59  London Paddington                       11    On time
## 18:10  Swansea                                 9     On time
## 18:11  London Paddington                       10    18:14
## 18:12  Salisbury                               2     On time
## 18:14  Great Malvern                           9     On time
## 18:14  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 18:21  Plymouth                                7     On time
##        via Bristol                             
## 18:23  London Paddington                       15A   On time
## 18:23  London Paddington                       10    On time
## 18:25  Didcot Parkway                          12    On time
## 18:28  Penzance                                7     On time
## 18:29  Abbey Wood                              14    On time
## 18:29  London Paddington                       10    On time
## 18:35  London Paddington                       11    On time
## 18:37  Basingstoke                             2     On time
## 18:37  London Paddington                       15    On time
## 18:40  Swindon                                 9     On time
## 18:43  Newbury                                 1     On time
## 18:46  London Paddington                       10    On time
## 18:48  Oxford                                  8B    On time
## 18:52  Bournemouth                             7     On time
## 18:55  Weston-super-Mare                       9     On time
## 18:59  Abbey Wood                              14    On time
## 19:00  London Paddington                       11    On time
## 19:01  Plymouth                                7     On time
## 19:02  London Paddington                       10A   On time
## 17:15  Ascot                                   BUS   On time
## 17:20  Gatwick Airport                         BUS   On time
##        via Guildford                           
## 17:20  Guildford                               BUS   On time
## 17:29  Ascot                                   BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:45  Ascot                                   BUS   On time
## 17:59  Ascot                                   BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:15  Ascot                                   BUS   On time
## 18:20  Gatwick Airport                         BUS   On time
##        via Guildford                           
## 18:20  Guildford                               BUS   On time
## 18:29  Ascot                                   BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:45  Ascot                                   BUS   On time
## 18:59  Ascot                                   BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
```
