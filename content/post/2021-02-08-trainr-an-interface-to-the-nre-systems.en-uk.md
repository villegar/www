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

## Example (Last rendered on 2022-11-27 20:04)

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
## Reading (RDG) Station Board on 2022-11-27 20:04:49
## Time   From                                    Plat  Expected
## 19:57  Plymouth                                11    20:24
## 20:04  Abbey Wood                              12    On time
## 20:06  London Paddington                       8     On time
## 20:10  Didcot Parkway                          15A   20:12
## 20:10  London Paddington                       7B    On time
## 20:14  Exeter St Davids                        14    20:18
## 20:15  London Paddington                       8B    On time
## 20:20  Newbury                                 1     On time
## 20:24  Oxford                                  15A   On time
## 20:27  London Paddington                       7     On time
## 20:30  London Waterloo                         4     On time
## 20:33  Abbey Wood                              14    On time
## 20:33  Basingstoke                             2     On time
## 20:39  Manchester Piccadilly                   7     On time
## 20:42  Plymouth                                11    On time
## 20:47  London Paddington                       8B    On time
## 20:49  Carmarthen                              13    20:57
## 20:56  Great Malvern                           15A   On time
## 20:58  London Waterloo                         6     On time
## 20:58  Plymouth                                11    21:02
## 21:03  Abbey Wood                              14    On time
## 21:05  Southampton Central                     7     On time
## 21:06  London Paddington                       8     On time
## 21:10  Didcot Parkway                          13A   On time
## 21:12  London Paddington                       12B   On time
## 21:12  London Paddington                       8     On time
## 21:14  Bristol Temple Meads                    15    On time
## 21:22  Bedwyn                                  1     On time
## 21:25  London Waterloo                         4     On time
## 21:26  London Paddington                       7B    On time
## 21:33  Abbey Wood                              14    On time
## 21:33  Basingstoke                             2     On time
## 21:39  Manchester Piccadilly                   7     On time
## 21:42  London Paddington                       8B    On time
## 21:49  Swansea                                 15    On time
## 21:53  London Paddington                       8     On time
## 21:55  Great Malvern                           15    On time
## 21:58  London Waterloo                         6     On time
## 22:03  Abbey Wood                              14    On time
## 20:04  Guildford                               BUS   On time
## 20:25  Heathrow Central Bus Stn                BUS   On time
## 20:38  Guildford                               BUS   On time
## 20:55  Heathrow Central Bus Stn                BUS   On time
## 21:18  Guildford                               BUS   On time
## 21:25  Heathrow Central Bus Stn                BUS   On time
## 22:00  Guildford                               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-11-27 20:04:52
## Time   To                                      Plat  Expected
## 19:58  London Paddington                       11    20:25
## 20:08  Swansea                                 8     On time
## 20:12  Great Malvern                           7B    On time
## 20:14  Ealing Broadway                         15A   On time
## 20:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 20:16  London Paddington                       14    20:19
## 20:21  London Waterloo                         6     On time
## 20:24  Abbey Wood                              12    On time
## 20:26  London Paddington                       15A   On time
## 20:28  Didcot Parkway                          8B    On time
## 20:28  Plymouth                                7     On time
## 20:38  Basingstoke                             2     On time
## 20:43  Newbury                                 1     On time
## 20:44  London Paddington                       11    On time
## 20:49  Oxford                                  8B    On time
## 20:50  London Paddington                       13    20:58
## 20:51  London Waterloo                         4     On time
## 20:52  Bournemouth                             7     On time
## 20:54  Abbey Wood                              14    On time
## 20:55  Weston-super-Mare                       8     On time
## 20:59  London Paddington                       11    21:03
## 21:02  London Paddington                       15A   On time
## 21:09  Swansea                                 8     On time
## 21:12  Birmingham New Street                   7     On time
##        via Coventry                            
## 21:14  Ealing Broadway                         13A   On time
## 21:15  Worcester Shrub Hill                    8     On time
## 21:17  London Paddington                       15    On time
## 21:20  Didcot Parkway                          12B   On time
## 21:21  London Waterloo                         6     On time
## 21:24  Ealing Broadway                         14    On time
## 21:28  Exeter St Davids                        7B    On time
## 21:38  Basingstoke                             2     On time
## 21:43  Bedwyn                                  1     On time
## 21:48  Oxford                                  8B    On time
## 21:50  London Paddington                       15    On time
## 21:51  London Waterloo                         4     On time
## 21:52  Southampton Central                     7     On time
## 21:54  Ealing Broadway                         14    On time
## 21:55  Bristol Temple Meads                    8     On time
## 21:57  London Paddington                       15    On time
## 20:12  Guildford                               BUS   On time
## 20:35  Guildford                               BUS   On time
## 21:00  Heathrow Airport T3 (Bus)               BUS   On time
## 21:30  Guildford                               BUS   On time
## 21:58  Guildford                               BUS   On time
## 22:00  Heathrow Airport T3 (Bus)               BUS   On time
```
