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

## Example (Last rendered on 2021-03-14 10:10)

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
## Reading (RDG) Station Board on 2021-03-14 10:10:40
## Time   From                                    Plat  Expected
## 09:58  Didcot Parkway                          15    On time
## 10:08  Southampton Central                     12B   On time
## 10:10  London Paddington                       9     On time
## 10:14  London Paddington                       14    10:10
## 10:16  Slough                                  13    On time
## 10:26  London Paddington                       7B    On time
## 10:28  Bedwyn                                  12    On time
## 10:30  Swansea                                 10    On time
## 10:33  Basingstoke                             2     On time
## 10:39  Birmingham New Street                   7     On time
## 10:41  Exeter St Davids                        11    On time
## 10:44  London Paddington                       14    On time
## 10:54  London Paddington                       9     On time
## 10:55  Bristol Parkway                         10    On time
## 10:57  Great Malvern                           12B   On time
## 10:59  London Paddington                       9     On time
## 11:07  Gatwick Airport                         5     On time
## 11:10  Bournemouth                             12B   On time
## 11:10  Didcot Parkway                          15    On time
## 11:12  London Paddington                       9B    On time
## 11:14  Bristol Parkway                         10    On time
## 11:14  London Paddington                       14    On time
## 11:16  Slough                                  13    On time
## 11:21  Bedwyn                                  1     On time
## 11:26  London Paddington                       8     On time
## 11:33  Basingstoke                             2     On time
## 11:39  Manchester Piccadilly                   8B    On time
## 11:44  London Paddington                       14    On time
## 11:45  Swansea                                 11    On time
## 11:54  London Paddington                       9B    On time
## 11:57  Great Malvern                           10A   On time
## 11:57  Plymouth                                11A   On time
## 11:59  London Paddington                       9     On time
## 12:07  Gatwick Airport                         5     On time
## 10:15  Virginia Water                          BUS   On time
## 10:25  Virginia Water                          BUS   On time
## 10:45  Virginia Water                          BUS   On time
## 10:55  Virginia Water                          BUS   On time
## 11:15  Virginia Water                          BUS   On time
## 11:25  Virginia Water                          BUS   On time
## 11:45  Virginia Water                          BUS   On time
## 11:55  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-14 10:10:42
## Time   To                                      Plat  Expected
## 10:11  Hereford                                9     On time
## 10:15  Manchester Piccadilly                   12B   On time
## 10:15  Slough                                  15    On time
## 10:26  Didcot Parkway                          13    On time
## 10:27  Plymouth                                7B    On time
## 10:35  Newbury                                 3     On time
## 10:36  Ealing Broadway                         14    On time
## 10:38  Basingstoke                             2     On time
## 10:40  London Paddington                       10    On time
## 10:41  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:45  London Paddington                       11    On time
## 10:55  Weston-super-Mare                       9     On time
## 11:05  London Paddington                       10    On time
## 11:06  Ealing Broadway                         14    On time
## 11:07  London Paddington                       12B   On time
## 11:09  Swansea                                 9     On time
## 11:14  Worcester Foregate Street               9B    On time
## 11:15  Manchester Piccadilly                   12B   On time
## 11:15  Slough                                  15    On time
## 11:19  London Paddington                       10    On time
## 11:26  Didcot Parkway                          13    On time
## 11:27  Plymouth                                8     On time
## 11:35  Bedwyn                                  1     On time
## 11:36  Ealing Broadway                         14    On time
## 11:38  Basingstoke                             2     On time
## 11:41  Gatwick Airport                         5     On time
##        via Guildford                           
## 11:49  London Paddington                       11    On time
## 11:52  Bournemouth                             8B    On time
## 11:55  Paignton                                9B    On time
##        via Bristol                             
## 12:05  London Paddington                       11A   On time
## 12:06  Ealing Broadway                         14    On time
## 12:07  London Paddington                       10A   On time
## 12:09  Swansea                                 9     On time
## 10:26  Virginia Water                          BUS   On time
## 10:36  Virginia Water                          BUS   On time
## 10:56  Virginia Water                          BUS   On time
## 11:06  Virginia Water                          BUS   On time
## 11:26  Virginia Water                          BUS   On time
## 11:36  Virginia Water                          BUS   On time
## 11:56  Virginia Water                          BUS   On time
## 12:06  Virginia Water                          BUS   On time
```
