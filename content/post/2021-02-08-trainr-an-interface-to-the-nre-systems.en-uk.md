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

## Example (Last rendered on 2021-03-14 18:08)

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
## Reading (RDG) Station Board on 2021-03-14 18:08:03
## Time   From                                    Plat  Expected
## 17:57  Hereford                                11A   On time
## 17:59  London Paddington                       9     On time
## 18:10  Bristol Temple Meads                    10    18:07
## 18:12  London Paddington                       9B    On time
## 18:13  Didcot Parkway                          15    On time
## 18:14  London Paddington                       15    18:06
## 18:14  Plymouth                                11    18:16
## 18:16  Slough                                  12    On time
## 18:23  London Paddington                       9     On time
## 18:26  London Paddington                       7B    On time
## 18:32  Basingstoke                             2     On time
## 18:35  Newbury                                 1     On time
## 18:39  Manchester Piccadilly                   13    On time
## 18:40  Bristol Temple Meads                    10    On time
## 18:44  London Paddington                       14    On time
## 18:45  Swansea                                 11    On time
## 18:54  London Paddington                       8B    On time
## 18:58  Plymouth                                11    On time
## 18:58  Worcester Foregate Street               10A   On time
## 18:59  London Paddington                       9B    On time
## 19:07  Gatwick Airport                         5     On time
## 19:09  Bournemouth                             8B    On time
## 19:09  Paignton                                10    On time
## 19:12  London Paddington                       9     On time
## 19:14  Didcot Parkway                          15    On time
## 19:14  London Paddington                       14    On time
## 19:16  Slough                                  12    On time
## 19:21  Bedwyn                                  1     On time
## 19:33  Basingstoke                             2     On time
## 19:38  Exeter St Davids                        11A   On time
## 19:39  Manchester Piccadilly                   8B    On time
## 19:40  Bristol Temple Meads                    10    On time
## 19:40  London Paddington                       9     On time
## 19:44  London Paddington                       14    On time
## 19:48  Swansea                                 11    On time
## 19:54  London Paddington                       9     On time
## 19:59  Plymouth                                11    On time
## 18:15  Virginia Water                          BUS   On time
## 18:25  Virginia Water                          BUS   On time
## 18:45  Virginia Water                          BUS   On time
## 18:55  Virginia Water                          BUS   On time
## 19:15  Virginia Water                          BUS   On time
## 19:25  Virginia Water                          BUS   On time
## 19:45  Virginia Water                          BUS   On time
## 19:55  Virginia Water                          BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-14 18:08:05
## Time   To                                      Plat  Expected
## 18:06  Ealing Broadway                         14    On time
## 18:07  London Paddington                       11A   On time
## 18:09  Swansea                                 9     On time
## 18:14  Great Malvern                           9B    On time
## 18:15  Manchester Piccadilly                   13B   On time
## 18:15  Slough                                  15    On time
## 18:19  London Paddington                       11    On time
## 18:21  London Paddington                       10    On time
## 18:24  Plymouth                                9     On time
##        via Bristol                             
## 18:25  Didcot Parkway                          12    On time
## 18:27  Liskeard                                7B    On time
## 18:36  Ealing Broadway                         15    On time
## 18:38  Basingstoke                             2     On time
## 18:41  Redhill                                 5     On time
## 18:45  London Paddington                       10    On time
## 18:50  London Paddington                       11    On time
## 18:50  Newbury                                 1     On time
## 18:55  Weston-super-Mare                       8B    On time
## 19:05  London Paddington                       11    On time
## 19:06  Ealing Broadway                         14    On time
## 19:07  London Paddington                       10A   On time
## 19:09  Swansea                                 9B    On time
## 19:14  Hereford                                9     On time
## 19:15  Manchester Piccadilly                   8B    On time
## 19:15  Slough                                  15    On time
## 19:20  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:20  London Paddington                       10    On time
## 19:25  Didcot Parkway                          12    On time
## 19:35  Bedwyn                                  1     On time
## 19:36  Ealing Broadway                         14    On time
## 19:38  Basingstoke                             2     On time
## 19:42  London Paddington                       11A   On time
## 19:45  London Paddington                       10    On time
## 19:48  Oxford                                  9     On time
## 19:50  London Paddington                       11    On time
## 19:52  Bournemouth                             8B    On time
## 19:55  Bristol Temple Meads                    9     On time
## 20:05  London Paddington                       11    On time
## 20:06  Ealing Broadway                         14    On time
## 18:06  Virginia Water                          BUS   On time
## 18:26  Virginia Water                          BUS   On time
## 18:36  Virginia Water                          BUS   On time
## 18:56  Virginia Water                          BUS   On time
## 19:06  Virginia Water                          BUS   On time
## 19:26  Virginia Water                          BUS   On time
## 19:36  Virginia Water                          BUS   On time
## 19:56  Virginia Water                          BUS   On time
## 20:06  Virginia Water                          BUS   On time
```
