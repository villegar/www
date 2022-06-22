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

## Example (Last rendered on 2022-06-22 18:04)

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
## Reading (RDG) Station Board on 2022-06-22 18:04:28
## Time   From                                    Plat  Expected
## 18:57  Penzance                                11    19:16
## 19:02  London Waterloo                         4     On time
## 19:05  Didcot Parkway                          15    19:01
## 19:10  London Paddington                       13    On time
## 19:11  London Paddington                       9     On time
## 19:15  London Paddington                       14    On time
## 19:15  Newbury                                 1     On time
## 19:16  Cardiff Central                         10    19:21
## 19:28  Didcot Parkway                          15    On time
## 19:29  London Paddington                       7     On time
## 19:32  London Waterloo                         6     On time
## 19:33  Redhill                                 5     On time
## 19:34  Basingstoke                             2     On time
## 19:39  Bristol Temple Meads                    10    On time
## 19:41  London Paddington                       13    On time
## 19:41  Manchester Piccadilly                   7     On time
## 19:45  London Paddington                       14    On time
## 19:46  Swansea                                 10    19:51
## 19:54  Newquay                                 11    20:31
## 19:54  Worcester Foregate Street               10A   On time
## 19:56  London Paddington                       9     On time
## 20:00  Didcot Parkway                          15    On time
## 20:02  London Waterloo                         4     On time
## 20:07  Bournemouth                             8     On time
## 20:11  London Paddington                       9B    On time
## 20:14  London Paddington                       14    On time
## 20:17  London Paddington                       9     On time
## 20:26  London Paddington                       8     On time
## 20:32  London Waterloo                         6     On time
## 20:33  Didcot Parkway                          13A   On time
## 20:34  Basingstoke                             2     On time
## 20:35  Redhill                                 14A   On time
## 20:43  London Paddington                       14    On time
## 20:43  Manchester Piccadilly                   7     On time
## 20:44  Newbury                                 1     On time
## 20:44  Swansea                                 10    On time
## 20:53  Great Malvern                           11A   On time
## 20:55  London Paddington                       9     On time
## 21:00  Penzance                                10    21:12
## 21:02  London Waterloo                         4     On time
## 19:34  Heathrow Central Bus Stn                BUS   On time
## 20:05  Heathrow Central Bus Stn                BUS   On time
## 20:38  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-06-22 18:04:32
## Time   To                                      Plat  Expected
## 18:58  London Paddington                       11    19:17
## 19:10  Newbury                                 1     On time
## 19:13  Swansea                                 9     On time
## 19:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 19:18  London Paddington                       10    19:22
## 19:20  Redhill                                 5     On time
## 19:23  Didcot Parkway                          15A   On time
## 19:24  London Waterloo                         4     On time
## 19:25  Basingstoke                             2     On time
## 19:27  Ealing Broadway                         14    On time
## 19:31  Plymouth                                7     On time
## 19:41  London Paddington                       10    On time
## 19:49  London Paddington                       10    19:52
## 19:50  Bournemouth                             7     On time
## 19:54  London Waterloo                         6     On time
## 19:55  London Paddington                       11    20:32
## 19:57  Didcot Parkway                          15    On time
## 19:57  Ealing Broadway                         13    On time
## 19:58  London Paddington                       10A   On time
## 19:58  Weston-super-Mare                       9     On time
## 20:08  Castle Cary                             7     On time
## 20:12  Newbury                                 1     On time
## 20:13  Swansea                                 9B    On time
## 20:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 20:19  Hereford                                9     On time
## 20:20  Redhill                                 5     On time
## 20:21  Basingstoke                             2     On time
## 20:23  Didcot Parkway                          15    On time
## 20:24  London Waterloo                         4     On time
## 20:27  Ealing Broadway                         14    On time
## 20:29  Plymouth                                8     On time
## 20:47  London Paddington                       10    On time
## 20:51  Didcot Parkway                          13    On time
## 20:54  London Waterloo                         6     On time
## 20:56  London Paddington                       11A   On time
## 20:57  Ealing Broadway                         14    On time
## 20:57  Weston-super-Mare                       9     On time
## 21:03  London Paddington                       10    21:13
## 20:00  Heathrow Central Bus Stn                BUS   On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
```
