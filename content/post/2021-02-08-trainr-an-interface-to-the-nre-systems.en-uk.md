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

## Example (Last rendered on 2021-05-08 08:12)

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
## Reading (RDG) Station Board on 2021-05-08 08:12:01
## Time   From                                    Plat  Expected
## 09:01  Didcot Parkway                          15    On time
## 09:07  London Paddington                       -     Cancelled
## 09:10  Bournemouth                             13    On time
## 09:11  London Paddington                       -     Cancelled
## 09:13  London Paddington                       14    09:09
## 09:14  London Waterloo                         4     On time
## 09:15  Plymouth                                11    On time
## 09:16  London Paddington                       -     Cancelled
## 09:17  London Paddington                       -     08:54
## 09:17  London Paddington                       -     07:55
## 09:33  Cheltenham Spa                          -     Cancelled
## 09:33  Redhill                                 5     On time
## 09:40  Bristol Temple Meads                    10    On time
## 09:40  Nottingham                              13    On time
## 09:43  London Paddington                       14    On time
## 09:44  London Paddington                       12    On time
## 09:46  Swansea                                 -     Cancelled
## 09:48  London Waterloo                         4     On time
## 09:51  Gatwick Airport                         4     On time
## 09:53  London Paddington                       -     Cancelled
## 09:54  Hereford                                -     Cancelled
## 09:55  London Paddington                       -     On time
## 09:57  Basingstoke                             2     On time
## 10:01  Didcot Parkway                          15    On time
## 10:07  London Paddington                       -     Cancelled
## 10:11  London Paddington                       -     Cancelled
## 10:13  London Paddington                       14    On time
## 10:13  Worcester Foregate Street               11    On time
## 10:14  London Waterloo                         5     On time
## 10:16  London Paddington                       -     Cancelled
## 10:20  Plymouth                                -     Cancelled
## 10:33  Redhill                                 4     On time
## 10:40  Bristol Temple Meads                    -     Cancelled
## 10:40  Manchester Piccadilly                   7     On time
## 10:43  London Paddington                       14    On time
## 10:44  Didcot Parkway                          -     On time
## 10:44  London Paddington                       12    On time
## 10:44  London Waterloo                         6     On time
## 10:46  Carmarthen                              -     Cancelled
## 10:51  Gatwick Airport                         5     On time
## 10:53  London Paddington                       -     Cancelled
## 10:54  Great Malvern                           -     Cancelled
## 10:55  London Paddington                       -     On time
## 10:56  London Paddington                       -     Cancelled
## 11:06  Basingstoke                             2     On time
## 09:20  Newbury                                 BUS   On time
## 10:00  Newbury                                 BUS   On time
## 10:12  Bedwyn                                  BUS   On time
## 10:17  Newbury                                 BUS   On time
## 10:55  Newbury                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-08 08:12:04
## Time   To                                      Plat  Expected
## 09:08  Plymouth                                -     Cancelled
## 09:12  London Waterloo                         6     On time
## 09:13  Swansea                                 -     Cancelled
## 09:15  Ealing Broadway                         15    On time
## 09:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 09:17  London Paddington                       11    On time
## 09:20  Great Malvern                           -     Cancelled
## 09:20  Redhill                                 5     On time
## 09:22  Ealing Broadway                         14    On time
## 09:26  Didcot Parkway                          -     07:59
## 09:26  Didcot Parkway                          -     On time
## 09:35  London Paddington                       -     Cancelled
## 09:41  London Paddington                       10    On time
## 09:42  London Waterloo                         4     On time
## 09:44  London Paddington                       9     On time
## 09:48  London Paddington                       -     Cancelled
## 09:52  Basingstoke                             2     On time
## 09:52  Ealing Broadway                         14    On time
## 09:53  Didcot Parkway                          12    On time
## 09:55  Bristol Temple Meads                    -     Cancelled
## 09:55  Didcot Parkway                          -     On time
## 09:56  London Paddington                       -     Cancelled
## 10:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:08  Penzance                                -     Cancelled
## 10:12  London Waterloo                         4     On time
## 10:13  Swansea                                 -     Cancelled
## 10:14  Ealing Broadway                         15    On time
## 10:14  London Paddington                       11    On time
## 10:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 10:19  Hereford                                -     Cancelled
## 10:20  Redhill                                 4     On time
## 10:22  Ealing Broadway                         14    On time
## 10:26  London Paddington                       -     Cancelled
## 10:42  London Paddington                       -     Cancelled
## 10:42  London Waterloo                         5     On time
## 10:44  London Paddington                       -     On time
## 10:48  London Paddington                       -     Cancelled
## 10:49  Bournemouth                             7     On time
## 10:52  Didcot Parkway                          12    On time
## 10:52  Ealing Broadway                         14    On time
## 10:54  Basingstoke                             2     On time
## 10:55  Bristol Temple Meads                    -     Cancelled
## 10:55  Didcot Parkway                          -     On time
## 10:56  London Paddington                       -     Cancelled
## 10:58  Cheltenham Spa                          -     Cancelled
## 11:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 09:34  Bedwyn                                  BUS   On time
## 09:36  Newbury                                 BUS   On time
## 10:10  Newbury                                 BUS   On time
## 10:34  Bedwyn                                  BUS   On time
## 10:36  Newbury                                 BUS   On time
## 11:10  Newbury                                 BUS   On time
```
