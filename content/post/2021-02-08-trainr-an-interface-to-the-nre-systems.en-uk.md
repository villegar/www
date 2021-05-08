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

## Example (Last rendered on 2021-05-08 10:13)

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
## Reading (RDG) Station Board on 2021-05-08 10:13:06
## Time   From                                    Plat  Expected
## 09:17  London Paddington                       -     08:54
## 10:44  Didcot Parkway                          -     Delayed
## 11:01  Didcot Parkway                          15    On time
## 11:10  Bournemouth                             13    11:34
## 11:11  London Paddington                       8     On time
## 11:13  London Paddington                       14    11:09
## 11:14  London Waterloo                         4     11:11
## 11:16  London Paddington                       9     11:22
## 11:19  London Paddington                       7     On time
## 11:23  Penzance                                -     Cancelled
## 11:33  Redhill                                 5     On time
## 11:34  Cheltenham Spa                          -     Cancelled
## 11:39  Manchester Piccadilly                   13    On time
## 11:40  Bristol Temple Meads                    -     Cancelled
## 11:43  London Paddington                       14    On time
## 11:44  Didcot Parkway                          -     On time
## 11:44  London Paddington                       12    On time
## 11:44  London Waterloo                         6     On time
## 11:46  Swansea                                 -     Cancelled
## 11:51  Gatwick Airport                         4     On time
## 11:53  London Paddington                       -     Cancelled
## 11:54  Worcester Foregate Street               10    On time
## 11:55  London Paddington                       -     On time
## 11:56  London Paddington                       -     Cancelled
## 11:57  Basingstoke                             2     On time
## 12:02  Didcot Parkway                          15    On time
## 12:07  London Paddington                       -     Cancelled
## 12:11  London Paddington                       -     Cancelled
## 12:13  London Paddington                       14    On time
## 12:14  London Waterloo                         5     On time
## 12:16  London Paddington                       -     Cancelled
## 12:30  Penzance                                -     Cancelled
## 12:33  Redhill                                 4     On time
## 12:39  Manchester Piccadilly                   7     On time
## 12:41  Weston-super-Mare                       -     Cancelled
## 12:43  London Paddington                       14    On time
## 12:44  Didcot Parkway                          -     On time
## 12:44  London Paddington                       12    On time
## 12:44  London Waterloo                         6     On time
## 12:48  Swansea                                 10    On time
## 12:51  Gatwick Airport                         5     On time
## 12:53  London Paddington                       -     Cancelled
## 12:54  Great Malvern                           -     Cancelled
## 12:55  London Paddington                       -     On time
## 12:57  Basingstoke                             2     On time
## 11:13  Bedwyn                                  BUS   On time
## 11:19  Newbury                                 BUS   On time
## 11:55  Newbury                                 BUS   On time
## 12:12  Bedwyn                                  BUS   On time
## 12:17  Newbury                                 BUS   On time
## 12:55  Newbury                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-08 10:13:09
## Time   To                                      Plat  Expected
## 09:26  Didcot Parkway                          -     11:13
## 10:44  London Paddington                       -     Delayed
## 11:12  London Waterloo                         6     On time
## 11:13  Swansea                                 8     On time
## 11:15  Ealing Broadway                         15    On time
## 11:15  Manchester Piccadilly                   13    11:35
##        via Coventry & Stoke-on-Trent           
## 11:19  Oxford                                  9     11:23
## 11:20  Redhill                                 5     On time
## 11:22  Ealing Broadway                         14    On time
## 11:22  Plymouth                                7     On time
## 11:26  London Paddington                       -     Cancelled
## 11:35  London Paddington                       -     Cancelled
## 11:42  London Paddington                       -     Cancelled
## 11:42  London Waterloo                         4     On time
## 11:44  London Paddington                       -     On time
## 11:48  London Paddington                       -     Cancelled
## 11:50  Basingstoke                             2     On time
## 11:52  Ealing Broadway                         14    On time
## 11:54  Didcot Parkway                          12    On time
## 11:55  Bristol Temple Meads                    -     Cancelled
## 11:55  Didcot Parkway                          -     On time
## 11:57  London Paddington                       10    On time
## 11:58  Cheltenham Spa                          -     Cancelled
## 12:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 12:08  Penzance                                -     Cancelled
## 12:11  Ealing Broadway                         15    On time
## 12:12  London Waterloo                         6     On time
## 12:13  Swansea                                 -     Cancelled
## 12:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 12:19  Hereford                                -     Cancelled
## 12:20  Redhill                                 4     On time
## 12:22  Ealing Broadway                         14    On time
## 12:31  London Paddington                       -     Cancelled
## 12:42  London Waterloo                         5     On time
## 12:43  London Paddington                       -     Cancelled
## 12:44  London Paddington                       -     On time
## 12:49  Bournemouth                             7     On time
## 12:50  London Paddington                       10    On time
## 12:52  Basingstoke                             2     On time
## 12:52  Ealing Broadway                         14    On time
## 12:53  Didcot Parkway                          12    On time
## 12:55  Bristol Temple Meads                    -     Cancelled
## 12:55  Didcot Parkway                          -     On time
## 12:57  London Paddington                       -     Cancelled
## 13:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 11:34  Bedwyn                                  BUS   On time
## 11:36  Newbury                                 BUS   On time
## 12:10  Newbury                                 BUS   On time
## 12:34  Bedwyn                                  BUS   On time
## 12:36  Newbury                                 BUS   On time
## 13:10  Newbury                                 BUS   On time
```
