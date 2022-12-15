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

## Example (Last rendered on 2022-12-15 20:07)

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
## Reading (RDG) Station Board on 2022-12-15 20:07:41
## Time   From                                    Plat  Expected
## 19:46  Swansea                                 10    20:39
## 19:54  Plymouth                                11    20:09
## 20:07  Bournemouth                             8     20:14
## 20:11  London Paddington                       9     On time
## 20:12  London Waterloo                         6     20:26
## 20:14  Abbey Wood                              14    On time
## 20:17  London Paddington                       9     On time
## 20:26  London Paddington                       8     On time
## 20:33  Didcot Parkway                          13A   On time
## 20:34  Basingstoke                             2     On time
## 20:35  Redhill                                 14A   On time
## 20:42  London Waterloo                         4     20:47
## 20:42  Manchester Piccadilly                   8     On time
## 20:43  Abbey Wood                              14    On time
## 20:44  Newbury                                 1     On time
## 20:45  Swansea                                 15    20:49
## 20:53  Great Malvern                           11A   On time
## 20:55  London Paddington                       9     On time
## 20:59  Penzance                                15    21:04
## 21:03  Didcot Parkway                          14A   On time
## 21:07  Bournemouth                             8B    On time
## 21:09  Bristol Temple Meads                    15    On time
## 21:11  London Waterloo                         6     On time
## 21:13  London Paddington                       13    On time
## 21:16  London Paddington                       9B    On time
## 21:19  London Paddington                       8B    On time
## 21:28  Basingstoke                             2     On time
## 21:29  Didcot Parkway                          14A   On time
## 21:29  London Paddington                       9     On time
## 21:29  Redhill                                 5     On time
## 21:34  London Paddington                       7B    On time
## 21:36  Newbury                                 1     On time
## 21:41  Manchester Piccadilly                   7     On time
## 21:42  Abbey Wood                              14    On time
## 21:42  London Waterloo                         4     On time
## 21:46  Swansea                                 15    On time
## 21:53  Great Malvern                           10A   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-12-15 20:07:45
## Time   To                                      Plat  Expected
## 19:49  London Paddington                       10    20:40
## 19:55  London Paddington                       11    20:10
## 20:12  London Waterloo                         5     On time
## 20:12  Newbury                                 1     On time
## 20:13  Swansea                                 9     On time
## 20:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 20:19  Hereford                                9     On time
## 20:20  Redhill                                 4     On time
## 20:21  Basingstoke                             2     On time
## 20:23  Didcot Parkway                          13A   On time
## 20:27  Abbey Wood                              14    On time
## 20:29  Plymouth                                8     On time
## 20:42  London Waterloo                         6     On time
## 20:51  Didcot Parkway                          13A   On time
## 20:52  London Paddington                       15    On time
## 20:57  London Paddington                       11A   On time
## 20:57  Weston-super-Mare                       9     On time
## 20:59  Abbey Wood                              14    On time
## 21:04  London Paddington                       15    21:04
## 21:07  Ealing Broadway                         14A   On time
## 21:10  Newbury                                 1     On time
## 21:12  London Waterloo                         4     On time
## 21:14  Birmingham New Street                   8B    On time
##        via Coventry                            
## 21:15  London Paddington                       15    On time
## 21:18  Swansea                                 9B    On time
## 21:21  Great Malvern                           8B    On time
## 21:22  Basingstoke                             2     On time
## 21:25  Didcot Parkway                          14A   On time
## 21:27  Abbey Wood                              13    On time
## 21:31  Bristol Temple Meads                    9     On time
## 21:34  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:37  Ealing Broadway                         14A   On time
## 21:37  Plymouth                                7B    On time
## 21:42  London Waterloo                         6     On time
## 21:49  Didcot Parkway                          13A   On time
## 21:52  Bournemouth                             7     On time
## 21:52  London Paddington                       15    On time
## 21:56  London Paddington                       10A   On time
## 21:57  Abbey Wood                              14    On time
```
