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

## Example (Last rendered on 2021-02-19 18:07)

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
## Reading (RDG) Station Board on 2021-02-19 18:07:55
## Time   From                                    Plat  Expected
## 17:57  Plymouth                                11    18:10
## 18:03  Didcot Parkway                          15    On time
## 18:07  Southampton Central                     13B   On time
## 18:10  London Waterloo                         4     On time
## 18:11  London Paddington                       9B    On time
## 18:13  London Paddington                       14    On time
## 18:20  Basingstoke                             2     On time
## 18:25  Bedwyn                                  11A   18:36
## 18:26  London Paddington                       8     Delayed
## 18:28  Didcot Parkway                          14    On time
## 18:28  London Paddington                       13    On time
## 18:30  Cheltenham Spa                          11A   18:33
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
## 19:03  Didcot Parkway                          15    On time
## 19:04  Basingstoke                             2     On time
## 19:05  Gatwick Airport                         5     On time
## 19:11  London Paddington                       9B    On time
## 19:13  London Paddington                       14    On time
## 19:14  London Paddington                       13    On time
## 19:15  London Waterloo                         6     On time
## 19:15  Newbury                                 1     On time
## 19:22  Bedwyn                                  11A   On time
## 19:26  London Paddington                       8     On time
## 19:28  London Paddington                       14    On time
## 19:29  London Paddington                       7     On time
## 19:30  London Paddington                       12    On time
## 19:31  Cheltenham Spa                          11    On time
## 19:33  Redhill                                 4     On time
## 19:34  London Paddington                       8     On time
## 19:39  Bristol Temple Meads                    10    On time
## 19:40  London Waterloo                         6     On time
## 19:40  Manchester Piccadilly                   7     On time
## 19:41  London Paddington                       9     On time
## 19:43  London Paddington                       13    On time
## 19:44  London Paddington                       12    On time
## 19:46  Swansea                                 10    On time
## 19:53  Worcester Foregate Street               10    On time
## 19:54  Plymouth                                11    On time
## 19:55  London Paddington                       12    On time
## 19:57  London Paddington                       9     On time
## 19:58  London Waterloo                         6     On time
## 20:00  Basingstoke                             1     On time
## 20:03  Newbury                                 2     On time
## 20:04  Gatwick Airport                         4     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-02-19 18:07:59
## Time   To                                      Plat  Expected
## 17:58  London Paddington                       11    18:11
## 18:08  Ealing Broadway                         15    On time
## 18:08  Newbury                                 1     On time
## 18:12  London Waterloo                         6     On time
## 18:13  Carmarthen                              9B    On time
## 18:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 18:22  Ealing Broadway                         14    On time
## 18:25  Redhill                                 5     On time
## 18:26  London Paddington                       11A   18:37
## 18:28  Bristol Temple Meads                    8     Delayed
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
## 19:10  Newbury                                 1     On time
## 19:12  London Waterloo                         6     On time
## 19:13  Swansea                                 9B    On time
## 19:15  Ealing Broadway                         15    On time
## 19:15  Manchester Piccadilly                   7B    On time
##        via Coventry & Stoke-on-Trent           
## 19:20  Redhill                                 5     On time
## 19:22  Ealing Broadway                         14    On time
## 19:25  London Paddington                       11A   On time
## 19:27  Weston-super-Mare                       8     On time
## 19:30  Didcot Parkway                          12    On time
## 19:31  Penzance                                7     On time
## 19:34  London Paddington                       11    On time
## 19:36  Bedwyn                                  8     On time
## 19:36  London Waterloo                         6     On time
## 19:41  London Paddington                       10    On time
## 19:42  Newbury                                 1     On time
## 19:43  Swansea                                 9     On time
## 19:49  London Paddington                       10    On time
## 19:49  Southampton Central                     7     On time
## 19:52  Ealing Broadway                         13    On time
## 19:55  London Paddington                       11    On time
## 19:57  Basingstoke                             2     On time
## 19:57  Didcot Parkway                          12    On time
## 19:58  Bristol Temple Meads                    9     On time
## 19:58  London Paddington                       10    On time
## 20:01  Gatwick Airport                         4     On time
##        via Guildford
```
