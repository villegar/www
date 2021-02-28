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

## Example (Last rendered on 2021-02-28 16:18)

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
## Reading (RDG) Station Board on 2021-02-28 16:18:19
## Time   From                                    Plat  Expected
## 16:15  London Paddington                       8     On time
## 16:18  London Paddington                       9B    On time
## 16:23  London Paddington                       9     On time
## 16:27  Newbury                                 3     On time
## 16:32  Ascot                                   4     On time
## 16:33  Basingstoke                             2     On time
## 16:39  Manchester Piccadilly                   7     On time
## 16:43  London Paddington                       14    On time
## 16:45  Salisbury                               1     On time
## 16:50  Swansea                                 13    On time
## 16:53  London Paddington                       8     On time
## 16:57  Oxford                                  15A   On time
## 17:02  Ascot                                   4     On time
## 17:07  London Paddington                       9     On time
## 17:07  Reigate                                 6     On time
## 17:10  Didcot Parkway                          15    On time
## 17:10  Eastleigh                               8     On time
## 17:13  London Paddington                       14    On time
## 17:14  Weston-super-Mare                       13    On time
## 17:15  London Paddington                       7     On time
## 17:17  London Paddington                       9     On time
## 17:19  London Paddington                       8     On time
## 17:23  London Paddington                       9     On time
## 17:28  London Paddington                       8     On time
## 17:28  Penzance                                13    On time
## 17:29  Bedwyn                                  1     On time
## 17:32  Ascot                                   4     On time
## 17:33  Basingstoke                             2     On time
## 17:39  Manchester Piccadilly                   7     On time
## 17:41  Bristol Temple Meads                    13    On time
## 17:43  London Paddington                       14    On time
## 17:47  Carmarthen                              15    On time
## 17:53  London Paddington                       8     On time
## 17:54  Westbury                                11    On time
## 17:56  Oxford                                  15    On time
## 18:02  Ascot                                   4     On time
## 18:07  London Paddington                       8     On time
## 18:07  Reigate                                 6     On time
## 18:10  Didcot Parkway                          15    On time
## 18:13  London Paddington                       14    On time
## 18:14  Bristol Temple Meads                    13    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-02-28 16:18:22
## Time   To                                      Plat  Expected
## 16:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 16:20  Oxford                                  9B    On time
## 16:22  Ealing Broadway                         14    On time
## 16:24  Ascot                                   5     On time
## 16:24  Bristol Temple Meads                    9     On time
## 16:28  Didcot Parkway                          8     On time
## 16:34  Newbury                                 3     On time
## 16:38  Basingstoke                             2     On time
## 16:41  Reigate                                 6     On time
## 16:51  Ascot                                   4     On time
## 16:52  Ealing Broadway                         14    On time
## 16:54  Bristol Temple Meads                    8     On time
## 16:55  London Paddington                       13    On time
## 17:01  London Paddington                       15A   On time
## 17:10  Swansea                                 9     On time
## 17:12  Salisbury                               1     On time
## 17:14  Ealing Broadway                         15    On time
## 17:15  London Paddington                       13    On time
## 17:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 17:19  Penzance                                9     On time
## 17:22  Ealing Broadway                         14    On time
## 17:22  Oxford                                  8     On time
## 17:24  Ascot                                   4     On time
## 17:24  Bristol Temple Meads                    9     On time
## 17:28  Didcot Parkway                          7     On time
## 17:31  Westbury                                8     On time
## 17:35  Bedwyn                                  1     On time
## 17:35  London Paddington                       13    On time
## 17:38  Basingstoke                             2     On time
## 17:41  Reigate                                 6     On time
## 17:45  London Paddington                       13    On time
## 17:49  London Paddington                       15    On time
## 17:51  Ascot                                   4     On time
## 17:52  Ealing Broadway                         14    On time
## 17:52  Eastleigh                               7     On time
## 17:54  Weston-super-Mare                       8     On time
## 17:56  London Paddington                       11    On time
## 18:01  London Paddington                       15    On time
## 18:10  Swansea                                 8     On time
## 18:14  Ealing Broadway                         15    On time
## 18:15  London Paddington                       13    On time
## 18:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent
```
