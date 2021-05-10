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

## Example (Last rendered on 2021-05-10 12:18)

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
## Reading (RDG) Station Board on 2021-05-10 12:18:02
## Time   From                                    Plat  Expected
## 13:14  London Paddington                       12    On time
## 13:16  London Paddington                       -     Cancelled
## 13:18  Basingstoke                             2     On time
## 13:24  Bedwyn                                  -     Cancelled
## 13:25  London Paddington                       -     Cancelled
## 13:27  London Paddington                       -     Cancelled
## 13:30  Cheltenham Spa                          -     Cancelled
## 13:31  London Paddington                       -     Cancelled
## 13:33  Redhill                                 5     On time
## 13:36  Newbury                                 1     On time
## 13:39  Bristol Temple Meads                    -     Cancelled
## 13:40  Manchester Piccadilly                   7B    On time
## 13:41  London Waterloo                         6     On time
## 13:43  London Paddington                       14    On time
## 13:44  Didcot Parkway                          -     On time
## 13:44  Swansea                                 -     Cancelled
## 13:51  London Paddington                       -     Cancelled
## 13:54  Great Malvern                           -     Cancelled
## 13:55  London Paddington                       -     Cancelled
## 13:58  London Paddington                       -     On time
## 14:03  Didcot Parkway                          15    On time
## 14:07  Penzance                                -     Cancelled
## 14:09  Bristol Temple Meads                    -     Cancelled
## 14:10  London Waterloo                         4     On time
## 14:13  London Paddington                       14    On time
## 14:14  London Paddington                       12    On time
## 14:16  London Paddington                       -     Cancelled
## 14:18  Basingstoke                             2     On time
## 14:22  Bedwyn                                  -     Cancelled
## 14:25  London Paddington                       -     Cancelled
## 14:27  London Paddington                       -     Cancelled
## 14:29  Cheltenham Spa                          -     Cancelled
## 14:32  London Paddington                       -     Cancelled
## 14:33  Redhill                                 5     On time
## 14:40  Bristol Temple Meads                    -     Cancelled
## 14:40  London Waterloo                         6     On time
## 14:40  Manchester Piccadilly                   13B   On time
## 14:40  Newbury                                 1     On time
## 14:43  London Paddington                       14    On time
## 14:45  Newport (South Wales)                   10    On time
## 14:46  Didcot Parkway                          -     On time
## 14:51  London Paddington                       -     Cancelled
## 14:55  London Paddington                       -     Cancelled
## 14:55  Worcester Shrub Hill                    -     Cancelled
## 14:58  London Paddington                       -     On time
## 14:59  Didcot Parkway                          14    On time
## 14:59  Penzance                                -     Cancelled
## 15:00  London Paddington                       -     Cancelled
## 15:06  Bournemouth                             8B    On time
## 15:10  London Waterloo                         4     On time
## 15:13  London Paddington                       13    On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-10 12:18:05
## Time   To                                      Plat  Expected
## 13:18  Worcester Foregate Street               -     Cancelled
## 13:20  Redhill                                 5     On time
## 13:22  Ealing Broadway                         14    On time
## 13:23  Didcot Parkway                          12    On time
## 13:27  Bristol Temple Meads                    -     Cancelled
## 13:29  Plymouth                                -     Cancelled
## 13:31  London Paddington                       -     Cancelled
## 13:34  London Paddington                       -     Cancelled
## 13:36  Redhill                                 14    On time
## 13:37  Bedwyn                                  -     Cancelled
## 13:42  London Paddington                       -     Cancelled
## 13:42  London Waterloo                         4     On time
## 13:44  London Paddington                       -     On time
## 13:52  Ealing Broadway                         14    On time
## 13:53  Cheltenham Spa                          -     Cancelled
## 13:57  Bristol Temple Meads                    -     Cancelled
## 13:57  Gatwick Airport                         15A   On time
##        via Guildford                           
## 13:57  London Paddington                       -     Cancelled
## 13:58  Didcot Parkway                          -     On time
## 14:07  Basingstoke                             2     On time
## 14:09  Ealing Broadway                         15    On time
## 14:11  London Paddington                       -     Cancelled
## 14:12  London Waterloo                         6     On time
## 14:12  Newbury                                 1     On time
## 14:13  London Paddington                       -     Cancelled
## 14:13  Swansea                                 -     Cancelled
## 14:15  Manchester Piccadilly                   7B    On time
##        via Coventry & Stoke-on-Trent           
## 14:18  Great Malvern                           -     Cancelled
## 14:20  Redhill                                 5     On time
## 14:22  Ealing Broadway                         14    On time
## 14:24  London Paddington                       -     Cancelled
## 14:25  Didcot Parkway                          12    On time
## 14:27  Bristol Temple Meads                    -     Cancelled
## 14:29  Penzance                                -     Cancelled
## 14:32  Basingstoke                             2     On time
## 14:35  London Paddington                       -     Cancelled
## 14:37  Bedwyn                                  -     Cancelled
## 14:42  London Waterloo                         4     On time
## 14:43  London Paddington                       -     Cancelled
## 14:46  London Paddington                       -     On time
## 14:49  Bournemouth                             13B   On time
## 14:52  Ealing Broadway                         14    On time
## 14:53  Cheltenham Spa                          -     Cancelled
## 14:57  Bristol Temple Meads                    -     Cancelled
## 14:57  London Paddington                       -     Cancelled
## 14:58  Didcot Parkway                          -     On time
## 15:01  Gatwick Airport                         15    On time
##        via Guildford                           
## 15:02  Penzance                                -     Cancelled
## 15:04  London Paddington                       -     Cancelled
## 15:05  Basingstoke                             15B   On time
## 15:10  Ealing Broadway                         14    On time
## 15:10  Newbury                                 1     On time
## 15:12  London Waterloo                         6     On time
## 15:13  Newport (South Wales)                   9     On time
## 15:15  Manchester Piccadilly                   8B    On time
##        via Coventry & Stoke-on-Trent
```
