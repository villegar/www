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

## Example (Last rendered on 2021-04-18 16:04)

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
## Reading (RDG) Station Board on 2021-04-18 16:04:47
## Time   From                                    Plat  Expected
## 16:56  London Paddington                       7     17:01
## 16:59  London Paddington                       9     17:03
## 17:07  Bournemouth                             7     On time
## 17:10  Weston-super-Mare                       10    On time
## 17:13  Didcot Parkway                          15    On time
## 17:13  London Paddington                       9B    On time
## 17:14  London Paddington                       14    17:16
## 17:15  Slough                                  12    17:18
## 17:23  London Paddington                       9B    On time
## 17:26  London Paddington                       7B    On time
## 17:29  Bedwyn                                  8B    On time
## 17:33  Basingstoke                             2     On time
## 17:39  Manchester Piccadilly                   7     On time
## 17:40  Bristol Temple Meads                    10    On time
## 17:44  London Paddington                       14    On time
## 17:46  Carmarthen                              11    17:54
## 17:53  London Paddington                       9     On time
## 17:56  Hereford                                11    On time
## 17:59  London Paddington                       9     On time
## 18:09  Bristol Temple Meads                    10    On time
## 18:12  London Paddington                       9B    On time
## 18:13  Didcot Parkway                          15    On time
## 18:14  London Paddington                       14    On time
## 18:14  Plymouth                                11    On time
## 18:15  Slough                                  12    On time
## 18:23  London Paddington                       9B    On time
## 18:26  London Paddington                       7     On time
## 18:33  Basingstoke                             2     On time
## 18:35  Newbury                                 1     On time
## 18:39  Manchester Piccadilly                   13    On time
## 18:40  Chippenham                              10A   On time
## 18:44  London Paddington                       14    On time
## 18:45  Swansea                                 11    On time
## 18:53  London Paddington                       8     On time
## 18:56  London Paddington                       7     On time
## 18:56  Worcester Foregate Street               10    On time
## 18:58  Penzance                                11    On time
## 17:16  Wokingham                               BUS   On time
## 17:22  Wokingham                               BUS   On time
## 17:45  Wokingham                               BUS   On time
## 17:49  Wokingham                               BUS   On time
## 17:55  Wokingham                               BUS   On time
## 18:16  Wokingham                               BUS   On time
## 18:22  Wokingham                               BUS   On time
## 18:45  Wokingham                               BUS   On time
## 18:49  Wokingham                               BUS   On time
## 18:55  Wokingham                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-04-18 16:04:50
## Time   To                                      Plat  Expected
## 17:01  Plymouth                                7     On time
## 17:09  Swansea                                 9     On time
## 17:12  Salisbury                               1     On time
## 17:13  London Paddington                       10    On time
## 17:14  Slough                                  15    On time
## 17:14  Worcester Foregate Street               9B    On time
## 17:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 17:24  Chippenham                              9B    On time
## 17:25  Didcot Parkway                          12    On time
## 17:27  Penzance                                7B    On time
## 17:31  Ealing Broadway                         14    On time
## 17:35  Bedwyn                                  8B    On time
## 17:38  Basingstoke                             2     On time
## 17:45  London Paddington                       10    On time
## 17:50  London Paddington                       11    17:55
## 17:52  Bournemouth                             7     On time
## 17:54  Weston-super-Mare                       9     On time
## 17:58  London Paddington                       11    On time
## 18:01  Ealing Broadway                         14    On time
## 18:09  Swansea                                 9     On time
## 18:14  Great Malvern                           9B    On time
## 18:14  Slough                                  15    On time
## 18:15  London Paddington                       10    On time
## 18:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 18:20  London Paddington                       11    On time
## 18:24  Plymouth                                9B    On time
##        via Bristol                             
## 18:25  Didcot Parkway                          12    On time
## 18:27  Penzance                                7     On time
## 18:31  Ealing Broadway                         14    On time
## 18:38  Basingstoke                             2     On time
## 18:43  London Paddington                       10A   On time
## 18:43  Newbury                                 1     On time
## 18:47  London Paddington                       11    On time
## 18:54  Weston-super-Mare                       8     On time
## 18:58  London Paddington                       11    On time
## 18:59  London Paddington                       10    On time
## 19:00  Plymouth                                7     On time
## 19:01  Ealing Broadway                         14    On time
## 17:05  Wokingham                               BUS   On time
## 17:20  Wokingham                               BUS   On time
## 17:25  Wokingham                               BUS   On time
## 17:38  Wokingham                               BUS   On time
## 18:00  Wokingham                               BUS   On time
## 18:05  Wokingham                               BUS   On time
## 18:20  Wokingham                               BUS   On time
## 18:25  Wokingham                               BUS   On time
## 18:43  Wokingham                               BUS   On time
## 19:00  Wokingham                               BUS   On time
```
