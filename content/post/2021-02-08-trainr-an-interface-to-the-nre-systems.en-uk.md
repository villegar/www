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

## Example (Last rendered on 2021-05-09 18:14)

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
## Reading (RDG) Station Board on 2021-05-09 18:14:10
## Time   From                                    Plat  Expected
## 19:09  Paignton                                -     Cancelled
## 19:09  Southampton Central                     7     19:06
## 19:11  Didcot Parkway                          8     19:15
## 19:14  Didcot Parkway                          15    On time
## 19:14  Penzance                                -     Cancelled
## 19:15  Slough                                  12    On time
## 19:22  London Paddington                       -     On time
## 19:33  Basingstoke                             2     On time
## 19:35  London Waterloo                         6     On time
## 19:38  Gatwick Airport                         5     On time
## 19:39  Manchester Piccadilly                   8     On time
## 19:40  Bristol Temple Meads                    -     Cancelled
## 19:44  London Paddington                       14    On time
## 19:46  London Paddington                       -     Cancelled
## 19:48  Carmarthen                              -     Cancelled
## 19:53  London Paddington                       -     Cancelled
## 19:57  Worcester Shrub Hill                    10    On time
## 20:05  London Waterloo                         4     On time
## 20:07  London Paddington                       -     Cancelled
## 20:07  Redhill                                 15    On time
## 20:11  Didcot Parkway                          -     On time
## 20:13  Didcot Parkway                          15    On time
## 20:13  London Paddington                       14    On time
## 20:14  London Paddington                       12    On time
## 20:22  London Paddington                       -     On time
## 20:25  Penzance                                -     Cancelled
## 20:27  London Paddington                       -     Cancelled
## 20:33  Basingstoke                             2     On time
## 20:35  London Waterloo                         6     On time
## 20:38  Gatwick Airport                         5     On time
## 20:39  Manchester Piccadilly                   7     On time
## 20:43  London Paddington                       14    On time
## 20:49  Swansea                                 -     Cancelled
## 20:53  London Paddington                       -     Cancelled
## 20:57  Worcester Foregate Street               10    On time
## 21:02  Plymouth                                -     Cancelled
## 21:05  London Waterloo                         4     On time
## 21:07  Bournemouth                             7     On time
## 21:07  London Paddington                       -     Cancelled
## 21:07  Redhill                                 15B   On time
## 21:11  Didcot Parkway                          -     On time
## 21:13  London Paddington                       14    On time
## 19:17  Newbury                                 BUS   On time
## 19:57  Bedwyn                                  BUS   On time
## 20:35  Newbury                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-09 18:14:13
## Time   To                                      Plat  Expected
## 19:12  London Paddington                       8     19:16
## 19:13  London Paddington                       -     Cancelled
## 19:14  Ealing Broadway                         15    On time
## 19:14  Worcester Shrub Hill                    3     On time
## 19:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 19:16  London Paddington                       -     Cancelled
## 19:20  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:22  Ealing Broadway                         14    On time
## 19:23  Didcot Parkway                          -     On time
## 19:24  London Waterloo                         4     On time
## 19:25  Didcot Parkway                          12    On time
## 19:38  Basingstoke                             2     On time
## 19:45  London Paddington                       -     Cancelled
## 19:47  Oxford                                  -     Cancelled
## 19:50  London Paddington                       -     Cancelled
## 19:52  Bournemouth                             8     On time
## 19:52  Ealing Broadway                         14    On time
## 19:54  Bristol Temple Meads                    -     Cancelled
## 19:54  London Waterloo                         6     On time
## 20:09  Swansea                                 -     Cancelled
## 20:12  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:12  London Paddington                       -     On time
## 20:14  Ealing Broadway                         15    On time
## 20:14  Great Malvern                           -     Cancelled
## 20:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 20:22  Ealing Broadway                         14    On time
## 20:23  Didcot Parkway                          -     On time
## 20:24  London Waterloo                         4     On time
## 20:25  Didcot Parkway                          12    On time
## 20:27  London Paddington                       -     Cancelled
## 20:27  Plymouth                                -     Cancelled
## 20:38  Basingstoke                             2     On time
## 20:50  London Paddington                       -     Cancelled
## 20:52  Bournemouth                             7     On time
## 20:52  Ealing Broadway                         14    On time
## 20:54  London Waterloo                         6     On time
## 20:54  Weston-super-Mare                       -     Cancelled
## 21:09  Swansea                                 -     Cancelled
## 21:10  London Paddington                       -     Cancelled
## 21:12  Birmingham New Street                   7     On time
##        via Coventry                            
## 21:12  London Paddington                       -     On time
## 21:13  Gatwick Airport                         5     On time
##        via Guildford                           
## 19:35  Bedwyn                                  BUS   On time
## 19:40  Newbury                                 BUS   On time
## 20:42  Newbury                                 BUS   On time
## 21:06  Newbury                                 BUS   On time
```
