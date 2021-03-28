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

## Example (Last rendered on 2021-03-28 18:13)

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
## Reading (RDG) Station Board on 2021-03-28 18:13:06
## Time   From                                    Plat  Expected
## 19:09  Paignton                                11    On time
## 19:09  Southampton Central                     8B    On time
## 19:12  London Paddington                       9B    On time
## 19:14  Didcot Parkway                          15    19:11
## 19:14  London Paddington                       14    19:08
## 19:15  Slough                                  12    On time
## 19:16  Ash                                     -     Cancelled
## 19:21  Bedwyn                                  1     On time
## 19:33  Basingstoke                             2     On time
## 19:38  Exeter St Davids                        11A   On time
## 19:39  Manchester Piccadilly                   8B    On time
## 19:40  Bristol Temple Meads                    10    On time
## 19:40  London Paddington                       9     On time
## 19:44  London Paddington                       14    On time
## 19:48  Swansea                                 10    On time
## 19:54  London Paddington                       9     On time
## 19:58  Hereford                                10A   On time
## 19:59  London Paddington                       9B    On time
## 19:59  Plymouth                                11    On time
## 20:12  London Paddington                       9B    On time
## 20:13  Didcot Parkway                          15    On time
## 20:14  London Paddington                       14    On time
## 20:15  Slough                                  12    On time
## 20:16  Ash                                     5     On time
## 20:20  Newbury                                 1     On time
## 20:27  London Paddington                       7     On time
## 20:33  Basingstoke                             2     On time
## 20:39  Manchester Piccadilly                   7B    On time
## 20:40  Plymouth                                11    On time
## 20:44  London Paddington                       14    On time
## 20:49  Swansea                                 10    On time
## 20:54  London Paddington                       9     On time
## 20:58  Plymouth                                11    On time
## 20:59  London Paddington                       9     On time
## 20:59  Worcester Foregate Street               10    On time
## 19:35  Staines                                 BUS   On time
## 19:50  Staines                                 BUS   On time
## 19:54  Staines                                 BUS   On time
## 20:09  Staines                                 BUS   On time
## 20:35  Staines                                 BUS   On time
## 20:50  Staines                                 BUS   On time
## 20:54  Staines                                 BUS   On time
## 21:09  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-28 18:13:09
## Time   To                                      Plat  Expected
## 19:14  Hereford                                9B    On time
## 19:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 19:15  Slough                                  15    On time
## 19:20  London Paddington                       11    On time
## 19:25  Didcot Parkway                          12    On time
## 19:35  Bedwyn                                  1     On time
## 19:36  Ealing Broadway                         14    On time
## 19:38  Basingstoke                             2     On time
## 19:41  Ash                                     5     On time
## 19:42  London Paddington                       11A   On time
## 19:45  London Paddington                       10    On time
## 19:48  Oxford                                  9     On time
## 19:50  London Paddington                       10    On time
## 19:52  Southampton Central                     8B    On time
## 19:55  Bristol Temple Meads                    9     On time
## 20:05  London Paddington                       11    On time
## 20:06  Ealing Broadway                         14    On time
## 20:07  London Paddington                       10A   On time
## 20:09  Swansea                                 9B    On time
## 20:14  Great Malvern                           9B    On time
## 20:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 20:15  Slough                                  15    On time
## 20:25  Didcot Parkway                          12    On time
## 20:27  Plymouth                                7     On time
## 20:36  Ealing Broadway                         14    On time
## 20:38  Basingstoke                             2     On time
## 20:41  Ash                                     5     On time
## 20:42  Newbury                                 1     On time
## 20:45  London Paddington                       11    On time
## 20:50  London Paddington                       10    On time
## 20:52  Southampton Central                     7B    On time
## 20:55  Weston-super-Mare                       9     On time
## 21:05  London Paddington                       11    On time
## 21:06  Ealing Broadway                         14    On time
## 21:07  London Paddington                       10    On time
## 21:09  Swansea                                 9     On time
## 19:15  Staines                                 BUS   On time
## 19:30  Staines                                 BUS   On time
## 19:50  Staines                                 BUS   On time
## 19:55  Staines                                 BUS   On time
## 20:15  Staines                                 BUS   On time
## 20:30  Staines                                 BUS   On time
## 20:50  Staines                                 BUS   On time
## 20:55  Staines                                 BUS   On time
```
