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

## Example (Last rendered on 2021-04-01 16:09)

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
## Reading (RDG) Station Board on 2021-04-01 16:09:30
## Time   From                                    Plat  Expected
## 17:00  London Paddington                       7     17:09
## 17:01  Didcot Parkway                          15A   17:08
## 17:05  Bournemouth                             13    On time
## 17:09  Bristol Temple Meads                    11    On time
## 17:09  London Paddington                       9     17:11
## 17:10  London Waterloo                         4     On time
## 17:11  London Paddington                       8     17:13
## 17:13  London Paddington                       14    17:07
## 17:22  Bedwyn                                  11A   On time
## 17:22  London Paddington                       12    On time
## 17:25  London Paddington                       8B    On time
## 17:26  Basingstoke                             2     On time
## 17:27  London Paddington                       7     On time
## 17:28  London Paddington                       14    On time
## 17:30  Cheltenham Spa                          10A   On time
## 17:33  London Paddington                       7B    On time
## 17:33  Newbury                                 1     On time
## 17:38  Bristol Temple Meads                    10    On time
## 17:39  Exeter St Davids                        11    On time
## 17:40  London Waterloo                         6     On time
## 17:40  Manchester Piccadilly                   7     On time
## 17:43  London Paddington                       14    On time
## 17:44  Redhill                                 5     On time
## 17:46  Swansea                                 11A   On time
## 17:47  Basingstoke                             12    On time
## 17:53  London Paddington                       9     On time
## 17:54  London Paddington                       13B   On time
## 17:55  Basingstoke                             12    On time
## 17:56  Hereford                                10A   On time
## 17:57  Plymouth                                11    On time
## 17:58  London Paddington                       9     On time
## 17:58  London Paddington                       14    On time
## 18:02  Gatwick Airport                         5     On time
## 18:03  Didcot Parkway                          15    On time
## 18:03  London Paddington                       7     On time
## 18:07  Bournemouth                             13B   On time
## 18:11  London Paddington                       9     On time
## 18:11  London Waterloo                         4     On time
## 18:13  London Paddington                       14    On time
## 18:20  Basingstoke                             2     On time
## 18:25  Bedwyn                                  11    On time
## 18:26  London Paddington                       8     On time
## 18:28  Didcot Parkway                          14    On time
## 18:28  London Paddington                       13    On time
## 18:30  Cheltenham Spa                          11A   On time
## 18:30  London Paddington                       12    On time
## 18:35  Newbury                                 1     On time
## 18:40  Bristol Temple Meads                    10    On time
## 18:40  London Waterloo                         6     On time
## 18:42  London Paddington                       9     On time
## 18:42  Manchester Piccadilly                   7     On time
## 18:43  London Paddington                       13    On time
## 18:44  London Paddington                       12    On time
## 18:47  Redhill                                 14B   On time
## 18:47  Swansea                                 10    On time
## 18:53  London Paddington                       12B   On time
## 18:56  London Waterloo                         6     On time
## 18:57  Great Malvern                           10A   On time
## 18:57  London Paddington                       9     On time
## 18:58  London Paddington                       14    On time
## 19:05  Basingstoke                             3     On time
## 19:05  Gatwick Airport                         5     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-04-01 16:09:33
## Time   To                                      Plat  Expected
## 17:03  Plymouth                                7     17:10
## 17:06  Ealing Broadway                         15A   17:09
## 17:10  Newbury                                 1     On time
## 17:11  London Paddington                       11    On time
## 17:12  London Waterloo                         6     On time
## 17:13  Swansea                                 8     17:14
## 17:15  Basingstoke                             3     On time
## 17:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 17:20  Redhill                                 5     On time
## 17:22  Ealing Broadway                         14    On time
## 17:24  London Paddington                       11A   On time
## 17:25  Didcot Parkway                          12    On time
## 17:27  Bristol Temple Meads                    8B    On time
## 17:29  Penzance                                7     On time
## 17:32  London Paddington                       10A   On time
## 17:33  Ealing Broadway                         14    On time
## 17:35  Bedwyn                                  7B    On time
## 17:37  London Paddington                       15    On time
## 17:40  London Paddington                       10    On time
## 17:42  London Paddington                       11    On time
## 17:42  London Waterloo                         4     On time
## 17:50  Gatwick Airport                         5     On time
##        via Guildford                           
## 17:52  Bournemouth                             7     On time
## 17:52  Ealing Broadway                         14    On time
## 17:53  London Paddington                       11A   On time
## 17:55  Bristol Temple Meads                    9     On time
## 17:58  Didcot Parkway                          13B   On time
## 17:58  London Paddington                       11    On time
## 18:00  Basingstoke                             2     On time
## 18:00  Hereford                                9     On time
## 18:00  London Paddington                       15    On time
## 18:00  London Paddington                       10A   On time
## 18:03  Ealing Broadway                         14    On time
## 18:04  Plymouth                                7     On time
## 18:08  Ealing Broadway                         15    On time
## 18:08  Newbury                                 1     On time
## 18:12  London Waterloo                         6     On time
## 18:13  Carmarthen                              9     On time
## 18:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 18:22  Ealing Broadway                         14    On time
## 18:25  Redhill                                 5     On time
## 18:26  London Paddington                       11    On time
## 18:28  Bristol Temple Meads                    8     On time
## 18:32  Didcot Parkway                          12    On time
## 18:33  Ealing Broadway                         13    On time
## 18:34  London Paddington                       11A   On time
## 18:42  London Waterloo                         4     On time
## 18:43  London Paddington                       10    On time
## 18:43  Swansea                                 9     On time
## 18:50  London Paddington                       10    On time
## 18:52  Ealing Broadway                         13    On time
## 18:52  Staines                                 6     On time
## 18:57  Didcot Parkway                          12B   On time
## 18:59  Weston-super-Mare                       9     On time
## 19:00  Basingstoke                             2     On time
## 19:00  London Paddington                       10A   On time
## 19:03  Ealing Broadway                         14    On time
```
