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

## Example (Last rendered on 2021-04-18 14:03)

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
## Reading (RDG) Station Board on 2021-04-18 14:04:00
## Time   From                                    Plat  Expected
## 14:44  Hayes & Harlington                      14    15:05
## 14:58  London Paddington                       9     15:00
## 15:09  Weston-super-Mare                       11    On time
## 15:10  Bournemouth                             8     On time
## 15:12  London Paddington                       9     On time
## 15:13  Didcot Parkway                          15    On time
## 15:14  Hayes & Harlington                      14    Delayed
## 15:15  Slough                                  12    On time
## 15:21  Bedwyn                                  1     On time
## 15:26  London Paddington                       8     On time
## 15:34  Basingstoke                             2     On time
## 15:39  Manchester Piccadilly                   8     On time
## 15:40  Bristol Temple Meads                    10    On time
## 15:44  London Paddington                       14    On time
## 15:45  Salisbury                               1     On time
## 15:46  Swansea                                 11    On time
## 15:53  London Paddington                       9     On time
## 15:56  Hereford                                10    On time
## 15:58  Plymouth                                11A   On time
## 15:59  London Paddington                       9     On time
## 16:09  Bristol Temple Meads                    10    On time
## 16:12  London Paddington                       9B    On time
## 16:13  Didcot Parkway                          15    On time
## 16:14  London Paddington                       14    On time
## 16:15  Slough                                  12    On time
## 16:23  London Paddington                       9B    On time
## 16:26  London Paddington                       7     On time
## 16:27  Newbury                                 1     On time
## 16:33  Basingstoke                             2     On time
## 16:39  Manchester Piccadilly                   13    On time
## 16:44  London Paddington                       14    On time
## 16:45  Salisbury                               1     On time
## 16:49  Swansea                                 10    On time
## 16:53  London Paddington                       9     On time
## 16:56  London Paddington                       7     On time
## 16:58  Oxford                                  10    On time
## 16:58  Penzance                                11    On time
## 15:16  Wokingham                               BUS   On time
## 15:22  Wokingham                               BUS   On time
## 15:45  Wokingham                               BUS   On time
## 15:49  Wokingham                               BUS   On time
## 15:55  Wokingham                               BUS   On time
## 16:16  Wokingham                               BUS   On time
## 16:22  Wokingham                               BUS   On time
## 16:45  Wokingham                               BUS   On time
## 16:49  Wokingham                               BUS   On time
## 16:55  Wokingham                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-04-18 14:04:03
## Time   To                                      Plat  Expected
## 15:01  Ealing Broadway                         14    15:08
## 15:09  Swansea                                 9     On time
## 15:12  Gillingham (Dorset)                     1     On time
## 15:13  London Paddington                       11    On time
## 15:14  Slough                                  15    On time
## 15:14  Worcester Foregate Street               9     On time
## 15:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 15:25  Didcot Parkway                          12    On time
## 15:27  Plymouth                                8     On time
## 15:31  Ealing Broadway                         14    On time
## 15:35  Bedwyn                                  1     On time
## 15:39  Basingstoke                             2     On time
## 15:43  London Paddington                       10    On time
## 15:50  London Paddington                       11    On time
## 15:52  Bournemouth                             8     On time
## 15:54  Taunton                                 9     On time
## 15:58  London Paddington                       11A   On time
## 15:59  London Paddington                       10    On time
## 16:01  Ealing Broadway                         14    On time
## 16:09  Swansea                                 9     On time
## 16:12  Salisbury                               1     On time
## 16:13  London Paddington                       10    On time
## 16:14  Hereford                                9B    On time
## 16:14  Slough                                  15    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:24  Chippenham                              9B    On time
## 16:25  Didcot Parkway                          12    On time
## 16:27  Penzance                                7     On time
## 16:31  Ealing Broadway                         14    On time
## 16:35  Newbury                                 1     On time
## 16:38  Basingstoke                             2     On time
## 16:50  London Paddington                       10    On time
## 16:54  Bristol Temple Meads                    9     On time
## 16:59  London Paddington                       11    On time
## 17:00  London Paddington                       10    On time
## 17:01  Ealing Broadway                         14    On time
## 17:01  Plymouth                                7     On time
## 15:05  Wokingham                               BUS   On time
## 15:20  Wokingham                               BUS   On time
## 15:25  Wokingham                               BUS   On time
## 15:38  Wokingham                               BUS   On time
## 16:00  Wokingham                               BUS   On time
## 16:05  Wokingham                               BUS   On time
## 16:20  Wokingham                               BUS   On time
## 16:25  Wokingham                               BUS   On time
## 16:38  Wokingham                               BUS   On time
## 17:00  Wokingham                               BUS   On time
```
