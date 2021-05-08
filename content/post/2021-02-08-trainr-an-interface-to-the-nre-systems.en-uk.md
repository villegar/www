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

## Example (Last rendered on 2021-05-08 14:10)

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
## Reading (RDG) Station Board on 2021-05-08 14:10:13
## Time   From                                    Plat  Expected
## 14:55  London Paddington                       9     15:14
## 15:01  Didcot Parkway                          15    On time
## 15:10  Bournemouth                             13    On time
## 15:11  London Paddington                       8     On time
## 15:13  London Paddington                       14    15:06
## 15:14  London Waterloo                         4     On time
## 15:16  London Paddington                       -     Cancelled
## 15:22  Penzance                                -     Cancelled
## 15:31  Cheltenham Spa                          -     Cancelled
## 15:33  Redhill                                 5     On time
## 15:39  Manchester Piccadilly                   13    On time
## 15:40  Bristol Temple Meads                    -     Cancelled
## 15:43  London Paddington                       14    On time
## 15:44  Didcot Parkway                          -     On time
## 15:44  London Paddington                       12    On time
## 15:44  London Waterloo                         6     On time
## 15:47  Swansea                                 10    On time
## 15:51  Gatwick Airport                         4     On time
## 15:53  London Paddington                       -     Cancelled
## 15:54  Hereford                                -     Cancelled
## 15:55  London Paddington                       -     On time
## 15:56  London Paddington                       -     Cancelled
## 15:57  Basingstoke                             2     On time
## 16:01  Didcot Parkway                          15    On time
## 16:07  London Paddington                       -     Cancelled
## 16:11  London Paddington                       -     Cancelled
## 16:13  London Paddington                       14    On time
## 16:14  London Waterloo                         5     On time
## 16:16  London Paddington                       -     Cancelled
## 16:25  Plymouth                                -     Cancelled
## 16:32  Cheltenham Spa                          -     Cancelled
## 16:33  Redhill                                 4     On time
## 16:39  Manchester Piccadilly                   7     On time
## 16:40  Bristol Temple Meads                    -     Cancelled
## 16:43  London Paddington                       14    On time
## 16:44  Didcot Parkway                          -     On time
## 16:44  London Paddington                       12    On time
## 16:44  London Waterloo                         6     On time
## 16:46  Swansea                                 10    On time
## 16:51  Gatwick Airport                         5     On time
## 16:53  London Paddington                       -     Cancelled
## 16:54  Worcester Foregate Street               -     Cancelled
## 16:55  London Paddington                       -     On time
## 16:56  Basingstoke                             2     On time
## 16:56  London Paddington                       -     Cancelled
## 15:12  Bedwyn                                  BUS   On time
## 15:19  Newbury                                 BUS   On time
## 15:55  Newbury                                 BUS   On time
## 16:12  Bedwyn                                  BUS   On time
## 16:17  Newbury                                 BUS   On time
## 16:55  Newbury                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-08 14:10:17
## Time   To                                      Plat  Expected
## 14:55  Didcot Parkway                          9     15:15
## 15:12  London Waterloo                         6     On time
## 15:13  Swansea                                 8     On time
## 15:15  Ealing Broadway                         15    On time
## 15:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 15:19  Great Malvern                           -     Cancelled
## 15:20  Redhill                                 5     On time
## 15:22  Ealing Broadway                         14    On time
## 15:29  London Paddington                       -     Cancelled
## 15:35  London Paddington                       -     Cancelled
## 15:41  London Paddington                       -     Cancelled
## 15:42  London Waterloo                         4     On time
## 15:44  London Paddington                       -     On time
## 15:50  London Paddington                       10    On time
## 15:52  Basingstoke                             2     On time
## 15:52  Ealing Broadway                         14    On time
## 15:53  Didcot Parkway                          12    On time
## 15:55  Bristol Temple Meads                    -     Cancelled
## 15:55  Didcot Parkway                          -     On time
## 15:56  London Paddington                       -     Cancelled
## 15:58  Cheltenham Spa                          -     Cancelled
## 16:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:08  Plymouth                                -     Cancelled
## 16:12  London Waterloo                         6     On time
## 16:13  Swansea                                 -     Cancelled
## 16:15  Ealing Broadway                         15    On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:19  Great Malvern                           -     Cancelled
## 16:20  Redhill                                 4     On time
## 16:22  Ealing Broadway                         14    On time
## 16:26  London Paddington                       -     Cancelled
## 16:35  London Paddington                       -     Cancelled
## 16:41  London Paddington                       -     Cancelled
## 16:42  London Waterloo                         5     On time
## 16:44  London Paddington                       -     On time
## 16:48  London Paddington                       10    On time
## 16:49  Bournemouth                             7     On time
## 16:52  Basingstoke                             2     On time
## 16:52  Ealing Broadway                         14    On time
## 16:53  Didcot Parkway                          12    On time
## 16:55  Bristol Temple Meads                    -     Cancelled
## 16:55  Didcot Parkway                          -     On time
## 16:56  London Paddington                       -     Cancelled
## 16:58  Cheltenham Spa                          -     Cancelled
## 17:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 15:10  Newbury                                 BUS   On time
## 15:34  Bedwyn                                  BUS   On time
## 15:36  Newbury                                 BUS   On time
## 16:10  Newbury                                 BUS   On time
## 16:34  Bedwyn                                  BUS   On time
## 16:36  Newbury                                 BUS   On time
```
