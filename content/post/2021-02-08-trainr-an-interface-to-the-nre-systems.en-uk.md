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

## Example (Last rendered on 2021-05-08 12:13)

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
## Reading (RDG) Station Board on 2021-05-08 12:13:23
## Time   From                                    Plat  Expected
## 12:44  Didcot Parkway                          10    Delayed
## 13:02  Didcot Parkway                          15    On time
## 13:10  Bournemouth                             13    On time
## 13:11  London Paddington                       8B    On time
## 13:14  London Waterloo                         4     On time
## 13:15  Plymouth                                11A   13:07
## 13:16  London Paddington                       -     Cancelled
## 13:19  London Paddington                       -     Cancelled
## 13:33  Redhill                                 5     On time
## 13:39  Manchester Piccadilly                   7     On time
## 13:40  Bristol Temple Meads                    -     Cancelled
## 13:43  London Paddington                       14    On time
## 13:44  Didcot Parkway                          -     On time
## 13:44  London Paddington                       13    On time
## 13:44  London Waterloo                         6     On time
## 13:46  Swansea                                 10    On time
## 13:51  Gatwick Airport                         4     On time
## 13:53  London Paddington                       -     Cancelled
## 13:54  Great Malvern                           -     Cancelled
## 13:55  London Paddington                       -     On time
## 13:56  Basingstoke                             2     On time
## 13:56  London Paddington                       -     Cancelled
## 14:02  Didcot Parkway                          15    On time
## 14:06  London Paddington                       -     Cancelled
## 14:11  London Paddington                       9     On time
## 14:13  London Paddington                       14    On time
## 14:14  London Waterloo                         5     On time
## 14:16  London Paddington                       -     Cancelled
## 14:27  Penzance                                -     Cancelled
## 14:33  Cheltenham Spa                          -     Cancelled
## 14:33  Redhill                                 4     On time
## 14:40  Bristol Temple Meads                    -     Cancelled
## 14:40  Manchester Piccadilly                   7     On time
## 14:41  London Paddington                       -     Cancelled
## 14:43  London Paddington                       14    On time
## 14:44  Didcot Parkway                          -     On time
## 14:44  London Paddington                       12    On time
## 14:44  London Waterloo                         6     On time
## 14:46  Swansea                                 -     Cancelled
## 14:51  Gatwick Airport                         5     On time
## 14:53  London Paddington                       -     Cancelled
## 14:53  Worcester Foregate Street               -     Cancelled
## 14:55  London Paddington                       -     On time
## 14:56  London Paddington                       -     Cancelled
## 14:57  Basingstoke                             2     On time
## 15:07  London Paddington                       9     On time
## 13:12  Bedwyn                                  BUS   On time
## 13:19  Newbury                                 BUS   On time
## 13:55  Newbury                                 BUS   On time
## 14:12  Bedwyn                                  BUS   On time
## 14:17  Newbury                                 BUS   On time
## 14:55  Newbury                                 BUS   On time
## 15:12  Bedwyn                                  BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-08 12:13:26
## Time   To                                      Plat  Expected
## 12:44  London Paddington                       10    Delayed
## 13:12  London Waterloo                         6     On time
## 13:13  Swansea                                 8B    On time
## 13:15  Ealing Broadway                         15    On time
## 13:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 13:17  London Paddington                       11A   On time
## 13:19  Worcester Foregate Street               -     Cancelled
## 13:20  Redhill                                 5     On time
## 13:22  Ealing Broadway                         14    On time
## 13:22  Penzance                                -     Cancelled
## 13:41  London Paddington                       -     Cancelled
## 13:42  London Waterloo                         4     On time
## 13:44  London Paddington                       -     On time
## 13:48  London Paddington                       10    On time
## 13:49  Oxford                                  -     Cancelled
## 13:52  Basingstoke                             2     On time
## 13:52  Ealing Broadway                         14    On time
## 13:54  Didcot Parkway                          13    On time
## 13:55  Bristol Temple Meads                    -     Cancelled
## 13:55  Didcot Parkway                          -     On time
## 13:56  London Paddington                       -     Cancelled
## 13:58  Cheltenham Spa                          -     Cancelled
## 14:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 14:08  Penzance                                -     Cancelled
## 14:12  London Waterloo                         6     On time
## 14:13  Swansea                                 9     On time
## 14:15  Ealing Broadway                         15    On time
## 14:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 14:19  Great Malvern                           -     Cancelled
## 14:20  Redhill                                 4     On time
## 14:22  Ealing Broadway                         14    On time
## 14:29  London Paddington                       -     Cancelled
## 14:35  London Paddington                       -     Cancelled
## 14:41  London Paddington                       -     Cancelled
## 14:42  London Waterloo                         5     On time
## 14:43  Plymouth                                -     Cancelled
## 14:44  London Paddington                       -     On time
## 14:48  London Paddington                       -     Cancelled
## 14:49  Bournemouth                             7     On time
## 14:49  Oxford                                  -     On time
## 14:52  Basingstoke                             2     On time
## 14:52  Ealing Broadway                         14    On time
## 14:53  Didcot Parkway                          12    On time
## 14:55  Bristol Temple Meads                    -     Cancelled
## 14:55  Didcot Parkway                          -     On time
## 14:56  London Paddington                       -     Cancelled
## 14:58  Cheltenham Spa                          -     Cancelled
## 15:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 15:08  Plymouth                                9     On time
## 15:12  London Waterloo                         6     On time
## 13:34  Bedwyn                                  BUS   On time
## 13:36  Newbury                                 BUS   On time
## 14:10  Newbury                                 BUS   On time
## 14:34  Bedwyn                                  BUS   On time
## 14:36  Newbury                                 BUS   On time
## 15:10  Newbury                                 BUS   On time
```
