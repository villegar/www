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

## Example (Last rendered on 2021-08-08 16:13)

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
## Reading (RDG) Station Board on 2021-08-08 16:13:58
## Time   From                                    Plat  Expected
## 15:39  Manchester Piccadilly                   7B    17:06
## 16:39  Manchester Piccadilly                   13    17:28
## 16:52  London Paddington                       9     17:14
## 16:58  Penzance                                11    17:18
## 17:07  Bournemouth                             8     17:17
## 17:10  Bath Spa                                11    17:07
## 17:13  Didcot Parkway                          15A   17:17
## 17:13  London Paddington                       9     17:32
## 17:15  London Paddington                       12B   17:12
## 17:20  Bedwyn                                  3     17:25
## 17:23  London Paddington                       9     Delayed
## 17:26  London Paddington                       7     On time
## 17:33  Basingstoke                             2     17:36
## 17:35  London Waterloo                         4     On time
## 17:38  Exeter St Davids                        11    On time
## 17:38  Gatwick Airport                         5     On time
## 17:39  Manchester Piccadilly                   8     17:58
## 17:40  Bristol Parkway                         -     Cancelled
## 17:43  London Paddington                       14    On time
## 17:45  Carmarthen                              11    On time
## 17:47  Yeovil Pen Mill                         1     On time
## 17:53  London Paddington                       -     Cancelled
## 17:54  Plymouth                                10    On time
## 17:56  Hereford                                11A   On time
## 18:06  London Waterloo                         4     On time
## 18:07  London Paddington                       9     On time
## 18:07  Redhill                                 6     On time
## 18:10  Swindon                                 11A   On time
## 18:12  London Paddington                       9B    On time
## 18:13  Didcot Parkway                          15A   On time
## 18:13  London Paddington                       14    On time
## 18:14  Bath Spa                                10    On time
## 18:15  London Paddington                       12B   On time
## 18:21  Newbury                                 1     On time
## 18:23  London Paddington                       9     On time
## 18:26  London Paddington                       7     On time
## 18:33  Basingstoke                             2     On time
## 18:35  London Waterloo                         4     On time
## 18:38  Gatwick Airport                         5     On time
## 18:39  Manchester Piccadilly                   12    On time
## 18:40  Bristol Parkway                         11    On time
## 18:43  London Paddington                       14    On time
## 18:44  Swansea                                 10    On time
## 18:45  London Paddington                       8     On time
## 18:47  Salisbury                               1     On time
## 18:53  London Paddington                       9     On time
## 18:55  Great Malvern                           10A   On time
## 18:58  London Paddington                       7     On time
## 18:58  Penzance                                11    On time
## 19:06  Bath Spa                                10    On time
## 19:06  London Waterloo                         4     On time
## 19:07  London Paddington                       -     Cancelled
## 19:07  Redhill                                 15    On time
## 17:21  Heathrow Central Bus Stn                BUS   On time
## 18:21  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-08-08 16:14:02
## Time   To                                      Plat  Expected
## 15:52  Southampton Central                     7B    17:12
## 16:53  Bath Spa                                9     17:15
## 16:59  London Paddington                       11    17:19
## 17:12  London Paddington                       11    On time
## 17:14  Ealing Broadway                         15A   17:18
## 17:14  Great Malvern                           9     17:33
## 17:15  Manchester Piccadilly                   8     17:18
##        via Coventry & Stoke-on-Trent           
## 17:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:22  Ealing Broadway                         14    On time
## 17:24  Bristol Parkway                         9     Delayed
## 17:24  London Waterloo                         4     On time
## 17:25  Didcot Parkway                          12B   On time
## 17:27  Penzance                                7     On time
## 17:38  Basingstoke                             2     On time
## 17:40  London Paddington                       11    On time
## 17:41  Redhill                                 6     On time
## 17:44  Bedwyn                                  3     On time
## 17:45  London Paddington                       -     Cancelled
## 17:50  London Paddington                       11    On time
## 17:52  Bournemouth                             8     17:59
## 17:52  Ealing Broadway                         14    On time
## 17:54  Bath Spa                                -     Cancelled
## 17:54  London Paddington                       10    On time
## 17:54  London Waterloo                         4     On time
## 18:00  London Paddington                       11A   On time
## 18:09  Swansea                                 9     On time
## 18:11  London Paddington                       11A   On time
## 18:12  Salisbury                               1     On time
## 18:14  Ealing Broadway                         15A   On time
## 18:14  Great Malvern                           9B    On time
## 18:15  London Paddington                       10    On time
## 18:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 18:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:22  Ealing Broadway                         14    On time
## 18:24  Bristol Parkway                         9     On time
## 18:24  London Waterloo                         4     On time
## 18:25  Didcot Parkway                          12B   On time
## 18:27  Penzance                                7     On time
## 18:39  Basingstoke                             2     On time
## 18:40  London Paddington                       11    On time
## 18:41  Redhill                                 6     On time
## 18:44  Newbury                                 1     On time
## 18:46  London Paddington                       10    On time
## 18:48  Oxford                                  8     On time
## 18:52  Ealing Broadway                         14    On time
## 18:54  Bath Spa                                9     On time
## 18:54  London Waterloo                         4     On time
## 18:58  London Paddington                       11    On time
## 18:59  London Paddington                       10A   On time
## 19:00  Plymouth                                7     On time
## 19:09  Bristol Parkway                         -     Cancelled
## 19:11  London Paddington                       10    On time
## 19:12  Salisbury                               1     On time
## 18:00  Heathrow Central Bus Stn                BUS   On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
```
