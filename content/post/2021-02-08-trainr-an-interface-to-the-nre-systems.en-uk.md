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

## Example (Last rendered on 2021-12-05 18:03)

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
## Reading (RDG) Station Board on 2021-12-05 18:03:48
## Time   From                                    Plat  Expected
## 17:43  Swansea                                 11    18:04
## 17:54  Plymouth                                11    17:59
## 17:57  Hereford                                10    18:00
## 18:06  Plymouth                                11    On time
## 18:07  London Paddington                       9     On time
## 18:08  Redhill                                 6     18:12
## 18:12  London Paddington                       8B    18:14
## 18:13  Didcot Parkway                          15A   18:15
## 18:15  London Paddington                       14    On time
## 18:21  Newbury                                 1     On time
## 18:23  London Paddington                       9     On time
## 18:23  London Paddington                       12B   On time
## 18:26  London Paddington                       7     On time
## 18:27  London Waterloo                         4     On time
## 18:33  Basingstoke                             2     On time
## 18:38  Gatwick Airport                         5     18:44
## 18:39  Manchester Piccadilly                   12    18:42
## 18:40  Bristol Temple Meads                    10    On time
## 18:43  Swansea                                 11    18:52
## 18:44  London Paddington                       8B    On time
## 18:46  London Paddington                       14    On time
## 18:53  London Paddington                       9     On time
## 18:56  Great Malvern                           13A   On time
## 18:57  London Waterloo                         4     On time
## 18:58  Penzance                                11    On time
## 19:01  London Paddington                       8     On time
## 19:06  Paignton                                11    On time
## 19:07  London Paddington                       9     On time
## 19:08  Redhill                                 15    On time
## 19:09  Southampton Central                     7     On time
## 19:12  London Paddington                       8     On time
## 19:13  Didcot Parkway                          14A   On time
## 19:16  London Paddington                       13    On time
## 19:19  Bedwyn                                  1     On time
## 19:23  London Paddington                       12B   On time
## 19:26  London Paddington                       7     On time
## 19:27  London Waterloo                         6     On time
## 19:34  Basingstoke                             2     On time
## 19:38  Exeter St Davids                        11    On time
## 19:38  Gatwick Airport                         5     On time
## 19:39  Manchester Piccadilly                   13    On time
## 19:40  Bristol Temple Meads                    10    On time
## 19:43  Swansea                                 11    19:49
## 19:44  London Paddington                       8     On time
## 19:46  London Paddington                       14    On time
## 19:53  London Paddington                       9     On time
## 19:57  London Waterloo                         4     On time
## 18:21  Heathrow Central Bus Stn                BUS   On time
## 19:19  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-12-05 18:03:51
## Time   To                                      Plat  Expected
## 17:47  London Paddington                       11    18:05
## 18:03  London Paddington                       11    On time
## 18:05  London Paddington                       10    On time
## 18:09  Swansea                                 9     On time
## 18:14  Ealing Broadway                         15A   18:16
## 18:14  Great Malvern                           8B    18:15
## 18:15  London Paddington                       11    On time
## 18:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 18:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 18:21  London Waterloo                         4     On time
## 18:22  Ealing Broadway                         14    On time
## 18:25  Didcot Parkway                          12B   On time
## 18:25  Plymouth                                9     On time
##        via Bristol                             
## 18:30  Penzance                                7     On time
## 18:39  Basingstoke                             2     On time
## 18:41  Redhill                                 6     On time
## 18:44  Newbury                                 1     On time
## 18:45  London Paddington                       10    On time
## 18:47  London Paddington                       11    18:56
## 18:50  Oxford                                  8B    On time
## 18:51  London Waterloo                         4     On time
## 18:53  Ealing Broadway                         14    On time
## 18:55  Weston-super-Mare                       9     On time
## 19:03  London Paddington                       11    On time
## 19:03  Plymouth                                8     On time
## 19:05  London Paddington                       13A   On time
## 19:09  Bristol Parkway                         9     On time
## 19:14  Ealing Broadway                         14A   On time
## 19:14  Hereford                                8     On time
## 19:15  London Paddington                       11    On time
## 19:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 19:18  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:21  London Waterloo                         4     On time
## 19:22  Ealing Broadway                         13    On time
## 19:25  Didcot Parkway                          12B   On time
## 19:30  Plymouth                                7     On time
## 19:38  Basingstoke                             2     On time
## 19:40  London Paddington                       11    On time
## 19:44  Bedwyn                                  1     On time
## 19:45  London Paddington                       10    On time
## 19:47  London Paddington                       11    19:52
## 19:50  Oxford                                  8     On time
## 19:51  London Waterloo                         6     On time
## 19:51  Southampton Central                     13    On time
## 19:53  Ealing Broadway                         14    On time
## 19:55  Bristol Temple Meads                    9     On time
## 19:00  Heathrow Central Bus Stn                BUS   On time
## 20:00  Heathrow Central Bus Stn                BUS   On time
```
