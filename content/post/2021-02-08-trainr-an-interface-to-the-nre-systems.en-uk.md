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

## Example (Last rendered on 2021-10-09 04:04)

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
## Reading (RDG) Station Board on 2021-10-09 04:04:02
## Time   From                                    Plat  Expected
## 05:48  London Paddington                       9     On time
## 06:11  Didcot Parkway                          15    On time
## 06:13  London Paddington                       14    On time
## 06:14  Staines                                 4     On time
## 06:17  London Paddington                       8     On time
## 06:17  Oxford                                  10    On time
## 06:38  London Paddington                       9     On time
## 06:41  Bristol Temple Meads                    10    On time
## 06:43  London Paddington                       13    On time
## 06:44  London Waterloo                         6     On time
## 06:46  London Paddington                       12    On time
## 06:47  Basingstoke                             2     On time
## 06:47  London Paddington                       9     On time
## 06:53  London Paddington                       9     On time
## 06:54  Newbury                                 11    On time
## 06:55  Oxford                                  10    On time
## 06:03  Heathrow Central Bus Stn                -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-10-09 04:04:05
## Time   To                                      Plat  Expected
## 05:08  Bedwyn                                  13B   On time
## 05:21  Redhill                                 14A   On time
## 05:32  Newbury                                 7     On time
## 05:39  London Waterloo                         6     On time
## 05:43  Basingstoke                             12B   On time
## 05:50  Oxford                                  9     On time
## 05:52  London Paddington                       14    On time
## 05:59  Gatwick Airport                         15    On time
##        via Guildford                           
## 06:09  London Waterloo                         5     On time
## 06:12  Newbury                                 7     On time
## 06:14  London Paddington                       15    On time
## 06:15  Manchester Piccadilly                   12    On time
##        via Coventry & Stoke-on-Trent           
## 06:19  Great Malvern                           8     On time
## 06:19  Redhill                                 15A   On time
## 06:20  London Paddington                       10    On time
## 06:22  Ealing Broadway                         14    On time
## 06:34  Newbury                                 7     On time
## 06:37  Basingstoke                             13A   On time
## 06:40  Swansea                                 9     On time
## 06:42  London Paddington                       10    On time
## 06:42  London Waterloo                         4     On time
## 06:49  Oxford                                  9     On time
## 06:52  Ealing Broadway                         13    On time
## 06:55  Bristol Temple Meads                    9     On time
## 06:56  Didcot Parkway                          12    On time
## 06:56  London Paddington                       10    On time
## 06:59  London Paddington                       11    On time
## 07:01  Gatwick Airport                         14A   On time
##        via Guildford                           
## 06:00  Heathrow Central Bus Stn                BUS   On time
## 07:00  Heathrow Central Bus Stn                BUS   On time
```
