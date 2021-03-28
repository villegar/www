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

## Example (Last rendered on 2021-03-28 12:04)

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
## Reading (RDG) Station Board on 2021-03-28 12:04:05
## Time   From                                    Plat  Expected
## 12:57  Oxford                                  10    12:54
## 12:59  London Paddington                       9B    On time
## 13:00  Plymouth                                11    On time
## 13:06  Southampton Central                     7     13:03
## 13:09  Weston-super-Mare                       11    13:11
## 13:10  Didcot Parkway                          15    On time
## 13:12  London Paddington                       9     On time
## 13:14  London Paddington                       14    On time
## 13:15  Slough                                  12    On time
## 13:16  Ash                                     6     On time
## 13:23  Bedwyn                                  1     On time
## 13:26  London Paddington                       7     On time
## 13:33  Basingstoke                             2     On time
## 13:39  Manchester Piccadilly                   7B    On time
## 13:40  Bristol Temple Meads                    10    On time
## 13:42  London Paddington                       14    On time
## 13:47  Swansea                                 11    On time
## 13:54  London Paddington                       9     On time
## 13:57  Great Malvern                           11    On time
## 13:59  London Paddington                       9     On time
## 14:09  Bristol Temple Meads                    10    On time
## 14:12  Didcot Parkway                          14    On time
## 14:12  London Paddington                       9     On time
## 14:14  London Paddington                       14    On time
## 14:15  Slough                                  12    On time
## 14:16  Ash                                     6     On time
## 14:17  Plymouth                                11    On time
## 14:26  London Paddington                       7     On time
## 14:33  Basingstoke                             2     On time
## 14:35  Newbury                                 3     On time
## 14:39  Manchester Piccadilly                   13    On time
## 14:44  London Paddington                       14    On time
## 14:48  Swansea                                 10    On time
## 14:54  London Paddington                       9     On time
## 14:57  London Paddington                       8     On time
## 13:09  Staines                                 BUS   On time
## 13:35  Staines                                 BUS   On time
## 13:50  Staines                                 BUS   On time
## 13:54  Staines                                 BUS   On time
## 14:09  Staines                                 BUS   On time
## 14:35  Staines                                 BUS   On time
## 14:50  Staines                                 BUS   On time
## 14:54  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-28 12:04:08
## Time   To                                      Plat  Expected
## 13:05  London Paddington                       11    On time
## 13:06  Ealing Broadway                         14    On time
## 13:07  London Paddington                       10    On time
## 13:09  Swansea                                 9B    On time
## 13:14  Worcester Foregate Street               9     On time
## 13:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 13:15  Slough                                  15    On time
## 13:19  London Paddington                       11    On time
## 13:26  Didcot Parkway                          12    On time
## 13:27  Plymouth                                7     On time
## 13:35  Bedwyn                                  1     On time
## 13:36  Ealing Broadway                         14    On time
## 13:38  Basingstoke                             2     On time
## 13:41  Ash                                     6     On time
## 13:45  London Paddington                       10    On time
## 13:50  London Paddington                       11    On time
## 13:52  Southampton Central                     7B    On time
## 13:55  Bristol Temple Meads                    9     On time
## 14:06  Ealing Broadway                         14    On time
## 14:07  London Paddington                       11    On time
## 14:09  Swansea                                 9     On time
## 14:13  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 14:15  London Paddington                       10    On time
## 14:15  Slough                                  14    On time
## 14:17  Hereford                                9     On time
## 14:20  London Paddington                       11    On time
## 14:25  Didcot Parkway                          12    On time
## 14:27  Plymouth                                7     On time
## 14:36  Ealing Broadway                         14    On time
## 14:38  Basingstoke                             2     On time
## 14:41  Ash                                     6     On time
## 14:42  Newbury                                 3     On time
## 14:50  London Paddington                       10    On time
## 14:55  Bristol Temple Meads                    9     On time
## 15:01  Exeter St Davids                        8     On time
## 13:15  Staines                                 BUS   On time
## 13:30  Staines                                 BUS   On time
## 13:50  Staines                                 BUS   On time
## 13:55  Staines                                 BUS   On time
## 14:15  Staines                                 BUS   On time
## 14:30  Staines                                 BUS   On time
## 14:50  Staines                                 BUS   On time
## 14:55  Staines                                 BUS   On time
```
