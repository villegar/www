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

## Example (Last rendered on 2021-04-11 18:10)

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
## Reading (RDG) Station Board on 2021-04-11 18:10:54
## Time   From                                    Plat  Expected
## 19:09  Southampton Central                     8     19:06
## 19:10  Paignton                                11    19:07
## 19:12  London Paddington                       9B    19:14
## 19:13  London Paddington                       14    19:07
## 19:14  Didcot Parkway                          15    On time
## 19:15  London Paddington                       12    On time
## 19:16  Ash                                     5     On time
## 19:21  Bedwyn                                  1     On time
## 19:32  Ascot                                   6     On time
## 19:33  Basingstoke                             2     On time
## 19:38  Exeter St Davids                        11    On time
## 19:39  Manchester Piccadilly                   8     On time
## 19:42  Chippenham                              10A   On time
## 19:43  London Paddington                       14    On time
## 19:46  London Paddington                       9     On time
## 19:48  Carmarthen                              10    On time
## 19:53  London Paddington                       9     On time
## 19:57  Hereford                                10    On time
## 19:59  Penzance                                11    On time
## 20:02  Ascot                                   4     On time
## 20:07  London Paddington                       9     On time
## 20:12  London Paddington                       9     On time
## 20:13  Didcot Parkway                          15    On time
## 20:13  London Paddington                       14    On time
## 20:14  London Paddington                       12    On time
## 20:16  Ash                                     5     On time
## 20:20  Newbury                                 1     On time
## 20:27  London Paddington                       7     On time
## 20:32  Ascot                                   6     On time
## 20:33  Basingstoke                             2     On time
## 20:39  Manchester Piccadilly                   7     On time
## 20:40  Plymouth                                11    On time
## 20:43  London Paddington                       14    On time
## 20:49  Swansea                                 10    On time
## 20:53  London Paddington                       9     On time
## 20:58  Penzance                                11    On time
## 20:59  Worcester Foregate Street               10A   On time
## 21:02  Ascot                                   4     On time
## 21:07  London Paddington                       9     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-04-11 18:10:56
## Time   To                                      Plat  Expected
## 19:13  London Paddington                       11    On time
## 19:14  Ealing Broadway                         15    On time
## 19:14  Hereford                                9B    19:15
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:22  Ealing Broadway                         14    On time
## 19:24  Ascot                                   4     On time
## 19:25  Didcot Parkway                          12    On time
## 19:35  Bedwyn                                  1     On time
## 19:38  Basingstoke                             2     On time
## 19:41  Ash                                     5     On time
## 19:42  London Paddington                       11    On time
## 19:45  London Paddington                       10A   On time
## 19:47  Oxford                                  9     On time
## 19:50  London Paddington                       10    On time
## 19:51  Ascot                                   4     On time
## 19:52  Ealing Broadway                         14    On time
## 19:52  Southampton Central                     8     On time
## 19:54  Bristol Temple Meads                    9     On time
## 19:59  London Paddington                       11    On time
## 20:01  London Paddington                       10    On time
## 20:09  Swansea                                 9     On time
## 20:14  Ealing Broadway                         15    On time
## 20:14  Great Malvern                           9     On time
## 20:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 20:22  Ealing Broadway                         14    On time
## 20:24  Ascot                                   4     On time
## 20:25  Didcot Parkway                          12    On time
## 20:27  Plymouth                                7     On time
## 20:38  Basingstoke                             2     On time
## 20:40  London Paddington                       11    On time
## 20:41  Ash                                     5     On time
## 20:42  Newbury                                 1     On time
## 20:50  London Paddington                       10    On time
## 20:51  Ascot                                   4     On time
## 20:52  Ealing Broadway                         14    On time
## 20:52  Southampton Central                     7     On time
## 20:54  Weston-super-Mare                       9     On time
## 20:58  London Paddington                       11    On time
## 20:59  London Paddington                       10A   On time
## 21:09  Swansea                                 9     On time
```
