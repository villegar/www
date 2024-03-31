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

## Example (Last rendered on 2024-03-31 17:06)

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
## Reading (RDG) Station Board on 2024-03-31 17:06:04.317069
## Time   From                                    Plat  Expected
## 17:48  Carmarthen                              11    18:04
## 17:57  Hereford                                10    18:10
## 18:06  Southampton Airport Parkway             8B    On time
## 18:07  London Paddington                       7     18:10
## 18:09  Plymouth                                11    18:20
## 18:12  London Paddington                       14    On time
## 18:12  London Paddington                       9     On time
## 18:14  Cardiff Central                         10A   18:18
## 18:17  Plymouth                                11    18:19
## 18:21  Newbury                                 1     On time
## 18:24  London Paddington                       9     On time
## 18:32  Basingstoke                             2     On time
## 18:34  Virginia Water                          4     On time
## 18:35  Didcot Parkway                          12    On time
## 18:40  Manchester Piccadilly                   7     On time
## 18:42  London Paddington                       14    On time
## 18:44  Swansea                                 11    On time
## 18:48  London Paddington                       13    On time
## 18:52  Ash                                     15    On time
## 18:55  London Paddington                       9     On time
## 18:57  Great Malvern                           10    On time
## 18:59  London Paddington                       8     On time
## 19:02  London Waterloo                         4     On time
## 19:06  Southampton Airport Parkway             8B    On time
## 19:07  London Paddington                       9     On time
## 19:08  Bristol Temple Meads                    10    On time
## 19:12  London Paddington                       14    On time
## 19:12  London Paddington                       7     On time
## 19:14  Swindon                                 11    On time
## 19:17  Penzance                                10    On time
## 19:19  Bedwyn                                  1     On time
## 19:32  Basingstoke                             2     On time
## 19:32  Virginia Water                          6     On time
## 19:35  Didcot Parkway                          15    On time
## 19:39  Manchester Piccadilly                   7     On time
## 19:42  London Paddington                       14    On time
## 19:47  London Paddington                       12    On time
## 19:48  Carmarthen                              11    On time
## 19:51  Ash                                     5     On time
## 19:54  London Paddington                       9     On time
## 19:57  Hereford                                10A   On time
## 19:58  London Paddington                       8     On time
## 20:02  London Waterloo                         4     On time
## 18:18  Heathrow Airport T3 (Bus)               BUS   On time
## 18:48  Heathrow Airport T3 (Bus)               BUS   On time
## 19:18  Heathrow Airport T3 (Bus)               BUS   On time
## 19:48  Heathrow Airport T3 (Bus)               BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2024-03-31 17:06:07.289424
## Time   To                                      Plat  Expected
## 17:55  London Paddington                       11    18:06
## 18:03  London Paddington                       10    18:11
## 18:10  Swansea                                 7     18:11
## 18:12  London Paddington                       11    18:21
## 18:14  Great Malvern                           9     On time
## 18:14  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 18:15  London Paddington                       10A   18:19
## 18:19  London Paddington                       11    18:20
## 18:24  Virginia Water                          4     On time
## 18:26  Didcot Parkway                          12    On time
## 18:26  Plymouth                                9     On time
##        via Bristol                             
## 18:29  Ealing Broadway                         14    On time
## 18:37  Basingstoke                             2     On time
## 18:43  Newbury                                 1     On time
## 18:48  Swindon                                 13    On time
## 18:51  Ash                                     5     On time
## 18:52  Southampton Airport Parkway             7     On time
## 18:54  London Waterloo                         4     On time
## 18:55  London Paddington                       11    On time
## 18:58  Bristol Temple Meads                    9     On time
## 18:59  Ealing Broadway                         14    On time
## 19:01  Plymouth                                8     On time
##        via Bristol                             
## 19:03  London Paddington                       10    On time
## 19:10  Swansea                                 9     On time
## 19:12  London Paddington                       10    On time
## 19:12  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent           
## 19:15  London Paddington                       11    On time
## 19:16  Hereford                                7     On time
## 19:19  London Paddington                       10    On time
## 19:24  Virginia Water                          4     On time
## 19:26  Didcot Parkway                          12    On time
## 19:29  Ealing Broadway                         14    On time
## 19:37  Basingstoke                             2     On time
## 19:43  Newbury                                 1     On time
## 19:48  Didcot Parkway                          12    On time
## 19:52  Southampton Airport Parkway             7     On time
## 19:54  London Waterloo                         6     On time
## 19:55  London Paddington                       11    On time
## 19:59  Ealing Broadway                         14    On time
## 20:00  Bristol Temple Meads                    9     On time
## 20:02  Plymouth                                8     On time
##        via Bristol                             
## 20:03  London Paddington                       10A   On time
## 18:30  Heathrow Airport T3 (Bus)               BUS   On time
## 19:00  Heathrow Airport T3 (Bus)               BUS   On time
## 19:30  Heathrow Airport T3 (Bus)               BUS   On time
## 20:00  Heathrow Airport T3 (Bus)               BUS   On time
```
