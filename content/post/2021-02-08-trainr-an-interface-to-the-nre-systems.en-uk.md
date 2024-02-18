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

## Example (Last rendered on 2024-02-18 17:06)

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
## Reading (RDG) Station Board on 2024-02-18 17:06:16.257812
## Time   From                                    Plat  Expected
## 16:54  London Paddington                       9     17:05
## 16:58  Penzance                                -     Cancelled
## 16:59  Hereford                                11    17:18
## 16:59  London Paddington                       -     Cancelled
## 17:00  Birmingham New Street                   13    17:05
## 17:07  Bournemouth                             8B    17:03
## 17:07  London Paddington                       7     On time
## 17:09  Weston-super-Mare                       10    On time
## 17:12  London Paddington                       14    17:18
## 17:12  London Paddington                       9     On time
## 17:14  Swindon                                 11    17:16
## 17:20  Bedwyn                                  3     On time
## 17:22  Oxford                                  10A   17:26
## 17:24  London Paddington                       9     17:26
## 17:26  London Paddington                       -     Cancelled
## 17:32  Basingstoke                             2     On time
## 17:35  Bristol Temple Meads                    -     Cancelled
## 17:35  Didcot Parkway                          12    On time
## 17:39  Manchester Piccadilly                   8B    17:45
## 17:40  Paignton                                11    18:03
## 17:42  London Paddington                       14    On time
## 17:44  Swansea                                 10    17:55
## 17:48  London Paddington                       9     On time
## 17:48  Yeovil Pen Mill                         2     On time
## 17:51  London Paddington                       13    On time
## 17:54  London Paddington                       9     On time
## 17:57  London Paddington                       8     On time
## 17:58  Exeter St Davids                        11    18:00
## 17:59  Hereford                                10    On time
## 18:06  Bournemouth                             8B    On time
## 18:07  London Paddington                       7     On time
## 18:09  Swindon                                 10    On time
## 18:12  London Paddington                       14    On time
## 18:12  London Paddington                       9     On time
## 18:14  Bristol Temple Meads                    11    On time
## 18:21  Newbury                                 1     On time
## 18:22  Oxford                                  11A   On time
## 18:24  London Paddington                       9     On time
## 18:27  London Paddington                       7     On time
## 18:29  Cheltenham Spa                          10    On time
## 18:32  Basingstoke                             2     On time
## 18:35  Bristol Temple Meads                    11    On time
## 18:35  Didcot Parkway                          12    On time
## 18:40  Manchester Piccadilly                   7     On time
## 18:42  London Paddington                       14    On time
## 18:44  Swansea                                 10    18:55
## 18:47  Gillingham (Dorset)                     2     On time
## 18:47  London Paddington                       13    On time
## 18:47  London Paddington                       8     On time
## 18:57  London Paddington                       -     Cancelled
## 18:59  Great Malvern                           10    On time
## 18:59  London Paddington                       7     On time
## 17:05  Guildford                               BUS   On time
## 17:14  Ascot                                   BUS   On time
## 17:18  Heathrow Airport T3 (Bus)               BUS   On time
## 17:28  Ascot                                   BUS   On time
## 17:44  Ascot                                   BUS   On time
## 17:48  Heathrow Airport T3 (Bus)               BUS   On time
## 17:55  Gatwick Airport                         BUS   On time
## 17:58  Ascot                                   BUS   On time
## 18:05  Guildford                               BUS   On time
## 18:14  Ascot                                   BUS   On time
## 18:18  Heathrow Airport T3 (Bus)               BUS   On time
## 18:28  Ascot                                   BUS   On time
## 18:44  Ascot                                   BUS   On time
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
## Reading (RDG) Station Board on 2024-02-18 17:06:18.078043
## Time   To                                      Plat  Expected
## 16:56  Plymouth                                9     17:06
##        via Bristol                             
## 17:01  Plymouth                                10    Delayed
## 17:03  London Paddington                       11    17:19
## 17:06  London Paddington                       -     Cancelled
## 17:10  Swansea                                 7     On time
## 17:12  London Paddington                       10    On time
## 17:12  Salisbury                               2     On time
## 17:14  Great Malvern                           9     On time
## 17:14  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 17:15  London Paddington                       11    17:17
## 17:26  Bristol Temple Meads                    9     On time
## 17:26  Didcot Parkway                          12A   On time
## 17:28  Penzance                                -     Cancelled
## 17:29  Ealing Broadway                         14    On time
## 17:29  London Paddington                       10A   On time
## 17:36  London Paddington                       -     Cancelled
## 17:37  Basingstoke                             2     On time
## 17:42  Birmingham New Street                   13B   On time
##        via Coventry                            
## 17:42  London Paddington                       11    18:04
## 17:45  Bedwyn                                  3     On time
## 17:48  Swindon                                 9     On time
## 17:52  Bournemouth                             8B    On time
## 17:52  Oxford                                  13    On time
## 17:55  London Paddington                       10    17:55
## 17:56  Weston-super-Mare                       9     On time
## 17:59  Cheltenham Spa                          8     On time
## 17:59  Ealing Broadway                         14    On time
## 18:03  London Paddington                       10    On time
## 18:06  London Paddington                       11    On time
## 18:10  Swansea                                 7     On time
## 18:12  Salisbury                               2     On time
## 18:14  Great Malvern                           9     On time
## 18:14  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 18:15  London Paddington                       10    On time
## 18:18  London Paddington                       11    On time
## 18:26  Didcot Parkway                          12A   On time
## 18:26  Plymouth                                9     On time
##        via Bristol                             
## 18:28  Penzance                                7     On time
## 18:29  Ealing Broadway                         14    On time
## 18:29  London Paddington                       11A   On time
## 18:36  London Paddington                       10    On time
## 18:37  Basingstoke                             2     On time
## 18:42  London Paddington                       11    On time
## 18:43  Newbury                                 1     On time
## 18:48  Swindon                                 13    On time
## 18:52  Bournemouth                             7     On time
## 18:52  Oxford                                  8     On time
## 18:55  London Paddington                       10    18:55
## 18:59  Ealing Broadway                         14    On time
## 19:00  Weston-super-Mare                       -     Cancelled
## 19:01  Plymouth                                7     On time
## 19:03  London Paddington                       10    On time
## 17:15  Ascot                                   -     Cancelled
## 17:20  Gatwick Airport                         BUS   On time
##        via Guildford                           
## 17:20  Guildford                               BUS   On time
## 17:30  Heathrow Airport T3 (Bus)               BUS   On time
## 17:31  Ascot                                   BUS   On time
## 17:45  Ascot                                   BUS   On time
## 18:00  Heathrow Airport T3 (Bus)               BUS   On time
## 18:01  Ascot                                   BUS   On time
## 18:15  Ascot                                   BUS   On time
## 18:20  Gatwick Airport                         BUS   On time
##        via Guildford                           
## 18:20  Guildford                               BUS   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 18:31  Ascot                                   BUS   On time
## 18:45  Ascot                                   BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:01  Ascot                                   BUS   On time
```
