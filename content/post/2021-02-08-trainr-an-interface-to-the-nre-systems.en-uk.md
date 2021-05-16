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

## Example (Last rendered on 2021-05-16 18:24)

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
## Reading (RDG) Station Board on 2021-05-16 18:24:56
## Time   From                                    Plat  Expected
## 19:15  London Paddington                       12B   On time
## 19:23  Swindon                                 14    On time
## 19:26  London Paddington                       8     On time
## 19:32  London Paddington                       13    On time
## 19:34  Basingstoke                             2     On time
## 19:39  Manchester Piccadilly                   7     On time
## 19:40  Exeter St Davids                        11    On time
## 19:42  Bristol Temple Meads                    14A   On time
## 19:43  London Paddington                       14    On time
## 19:49  Carmarthen                              15    19:53
## 19:53  London Paddington                       8     On time
## 19:58  London Paddington                       8     On time
## 19:58  Penzance                                11    20:09
## 20:06  Ash                                     5     On time
## 20:07  London Paddington                       8     On time
## 20:13  Didcot Parkway                          15A   On time
## 20:13  London Paddington                       14    On time
## 20:18  London Paddington                       13B   On time
## 20:20  Newbury                                 1     On time
## 20:23  Swindon                                 15    On time
## 20:26  London Paddington                       12    On time
## 20:28  London Paddington                       7B    On time
## 20:33  Basingstoke                             2     On time
## 20:39  Manchester Piccadilly                   7     On time
## 20:40  Plymouth                                11A   On time
## 20:43  London Paddington                       14    On time
## 20:49  Swansea                                 15    On time
## 20:53  London Paddington                       8     On time
## 20:57  London Paddington                       8     On time
## 20:58  Penzance                                11A   On time
## 21:06  Ash                                     5     On time
## 21:07  Bournemouth                             7     On time
## 21:07  London Paddington                       8     On time
## 21:13  Didcot Parkway                          15A   On time
## 21:13  London Paddington                       14    On time
## 21:14  London Paddington                       12B   On time
## 21:15  Taunton                                 14A   On time
## 21:19  Bedwyn                                  1     On time
## 19:40  Staines                                 BUS   On time
## 19:54  Staines                                 BUS   On time
## 19:55  Staines                                 BUS   On time
## 20:09  Staines                                 BUS   On time
## 20:40  Staines                                 BUS   On time
## 20:54  Staines                                 BUS   On time
## 20:55  Staines                                 BUS   On time
## 21:09  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-16 18:24:59
## Time   To                                      Plat  Expected
## 19:25  Didcot Parkway                          12B   On time
## 19:25  London Paddington                       14    On time
## 19:27  Plymouth                                8     On time
## 19:38  Basingstoke                             2     On time
## 19:42  London Paddington                       11    On time
## 19:44  Bedwyn                                  1     On time
## 19:45  London Paddington                       14A   On time
## 19:51  London Paddington                       15    19:54
## 19:52  Bournemouth                             7     On time
## 19:52  Ealing Broadway                         9     On time
## 19:54  Bristol Temple Meads                    8     On time
## 19:58  London Paddington                       11    20:10
## 20:00  Swindon                                 8     On time
## 20:09  Swansea                                 8     On time
## 20:12  Ash                                     5     On time
## 20:14  Ealing Broadway                         15A   On time
## 20:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 20:22  Ealing Broadway                         9     On time
## 20:25  Didcot Parkway                          13B   On time
## 20:25  London Paddington                       15    On time
## 20:33  Plymouth                                7B    On time
## 20:38  Basingstoke                             2     On time
## 20:40  London Paddington                       11A   On time
## 20:42  Newbury                                 1     On time
## 20:51  London Paddington                       15    On time
## 20:52  Bournemouth                             7     On time
## 20:52  Ealing Broadway                         9     On time
## 20:54  Weston-super-Mare                       8     On time
## 20:58  London Paddington                       11A   On time
## 21:00  Swindon                                 8     On time
## 21:09  Swansea                                 8     On time
## 21:12  Birmingham New Street                   7     On time
##        via Coventry                            
## 21:13  Ash                                     5     On time
## 21:14  Ealing Broadway                         15A   On time
## 21:16  Didcot Parkway                          12B   On time
## 21:16  London Paddington                       14A   On time
## 19:30  Staines                                 BUS   On time
## 19:50  Staines                                 BUS   On time
## 19:55  Staines                                 BUS   On time
## 20:15  Staines                                 BUS   On time
## 20:30  Staines                                 BUS   On time
## 20:50  Staines                                 BUS   On time
## 20:55  Staines                                 BUS   On time
## 21:15  Staines                                 BUS   On time
```
