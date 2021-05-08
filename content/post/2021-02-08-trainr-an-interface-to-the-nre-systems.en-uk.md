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

## Example (Last rendered on 2021-05-08 18:14)

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
## Reading (RDG) Station Board on 2021-05-08 18:14:02
## Time   From                                    Plat  Expected
## 19:01  Didcot Parkway                          15    On time
## 19:08  Bournemouth                             13    On time
## 19:11  London Paddington                       -     Cancelled
## 19:14  London Waterloo                         5     19:10
## 19:16  London Paddington                       -     Cancelled
## 19:22  Penzance                                11    19:12
## 19:33  Redhill                                 6     On time
## 19:34  Cheltenham Spa                          -     Cancelled
## 19:39  Manchester Piccadilly                   13    On time
## 19:40  Bristol Temple Meads                    -     Cancelled
## 19:43  London Paddington                       14    On time
## 19:43  London Paddington                       -     On time
## 19:44  Didcot Parkway                          -     On time
## 19:44  Didcot Parkway                          -     Cancelled
## 19:44  London Paddington                       12    On time
## 19:44  London Waterloo                         4     On time
## 19:46  Swansea                                 10    On time
## 19:51  Gatwick Airport                         5     On time
## 19:53  London Paddington                       9     On time
## 19:54  Great Malvern                           -     Cancelled
## 19:55  London Paddington                       -     Cancelled
## 19:56  London Paddington                       -     Cancelled
## 19:57  Basingstoke                             2     On time
## 20:01  Didcot Parkway                          15    On time
## 20:10  Bristol Temple Meads                    -     Cancelled
## 20:11  London Paddington                       -     Cancelled
## 20:13  London Paddington                       14    On time
## 20:14  London Waterloo                         6     20:16
## 20:16  London Paddington                       -     Cancelled
## 20:16  Plymouth                                -     Cancelled
## 20:26  London Paddington                       9     On time
## 20:33  Redhill                                 14B   On time
## 20:34  Cheltenham Spa                          -     Cancelled
## 20:39  Manchester Piccadilly                   8     On time
## 20:43  London Paddington                       -     On time
## 20:43  London Paddington                       14    On time
## 20:44  Didcot Parkway                          -     On time
## 20:44  London Paddington                       12    On time
## 20:44  London Waterloo                         4     On time
## 20:46  Swansea                                 10    On time
## 20:53  Gatwick Airport                         5     On time
## 20:53  London Paddington                       -     Cancelled
## 20:54  Great Malvern                           -     Cancelled
## 20:55  London Paddington                       -     Cancelled
## 20:56  London Paddington                       -     Cancelled
## 20:57  Basingstoke                             2     On time
## 21:08  Bristol Temple Meads                    -     Cancelled
## 19:12  Bedwyn                                  BUS   On time
## 19:19  Newbury                                 BUS   On time
## 20:12  Bedwyn                                  BUS   On time
## 20:17  Newbury                                 BUS   On time
## 20:24  Newbury                                 BUS   On time
## 21:09  Bedwyn                                  BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-08 18:14:05
## Time   To                                      Plat  Expected
## 19:13  Swansea                                 -     Cancelled
## 19:15  Ealing Broadway                         15    On time
## 19:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 19:19  Hereford                                -     Cancelled
## 19:20  Redhill                                 7A    On time
## 19:22  Ealing Broadway                         14    On time
## 19:26  London Paddington                       11    On time
## 19:35  London Paddington                       -     Cancelled
## 19:41  London Paddington                       -     Cancelled
## 19:42  London Waterloo                         5     On time
## 19:43  Didcot Parkway                          -     On time
## 19:44  London Paddington                       -     Cancelled
## 19:44  London Paddington                       -     On time
## 19:48  London Paddington                       10    On time
## 19:52  Basingstoke                             2     On time
## 19:52  Ealing Broadway                         14    On time
## 19:53  Didcot Parkway                          12    On time
## 19:55  Didcot Parkway                          -     Cancelled
## 19:55  Weston-super-Mare                       9     On time
## 19:56  London Paddington                       -     Cancelled
## 19:58  Cheltenham Spa                          -     Cancelled
## 20:01  Redhill                                 6     On time
## 20:11  London Paddington                       -     Cancelled
## 20:12  London Waterloo                         4     On time
## 20:13  Swansea                                 -     Cancelled
## 20:15  Ealing Broadway                         15    On time
## 20:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 20:18  London Paddington                       -     Cancelled
## 20:19  Great Malvern                           -     Cancelled
## 20:22  Ealing Broadway                         14    On time
## 20:28  Plymouth                                9     On time
## 20:30  Banbury                                 13B   On time
## 20:33  Gatwick Airport                         5     On time
##        via Guildford                           
## 20:35  London Paddington                       -     Cancelled
## 20:42  London Waterloo                         6     On time
## 20:43  Didcot Parkway                          -     On time
## 20:44  London Paddington                       -     On time
## 20:48  London Paddington                       10    On time
## 20:49  Bournemouth                             8     On time
## 20:52  Basingstoke                             2     On time
## 20:52  Ealing Broadway                         14    On time
## 20:53  Didcot Parkway                          12    On time
## 20:55  Didcot Parkway                          -     Cancelled
## 20:55  Exeter St Davids                        -     Cancelled
##        via Bristol                             
## 20:56  London Paddington                       -     Cancelled
## 20:58  Cheltenham Spa                          -     Cancelled
## 21:10  London Paddington                       -     Cancelled
## 21:12  London Waterloo                         4     On time
## 19:36  Newbury                                 BUS   On time
## 20:10  Bedwyn                                  BUS   On time
## 20:40  Newbury                                 BUS   On time
## 21:10  Bedwyn                                  BUS   On time
```
