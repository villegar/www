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

## Example (Last rendered on 2021-04-10 16:04)

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
## Reading (RDG) Station Board on 2021-04-10 16:04:37
## Time   From                                    Plat  Expected
## 16:59  Penzance                                11    17:05
## 17:01  Didcot Parkway                          15    On time
## 17:05  Southampton Central                     13    On time
## 17:11  London Paddington                       9     On time
## 17:11  London Waterloo                         4     On time
## 17:13  London Paddington                       14    On time
## 17:16  London Paddington                       9     On time
## 17:21  Bedwyn                                  11    On time
## 17:32  London Paddington                       7B    On time
## 17:33  Cheltenham Spa                          11    On time
## 17:38  Newbury                                 1     On time
## 17:39  Manchester Piccadilly                   7     On time
## 17:40  Bristol Temple Meads                    10    On time
## 17:41  London Waterloo                         6     On time
## 17:43  London Paddington                       14    On time
## 17:44  London Paddington                       12    On time
## 17:45  Ash                                     4     On time
## 17:48  Swansea                                 10    On time
## 17:53  London Paddington                       9     Delayed
## 17:54  Hereford                                10    On time
## 17:56  London Paddington                       8     On time
## 17:57  Basingstoke                             2     On time
## 18:01  Didcot Parkway                          14    On time
## 18:11  London Paddington                       9     On time
## 18:11  London Waterloo                         5     On time
## 18:13  London Paddington                       13    On time
## 18:17  London Paddington                       9     On time
## 18:17  Plymouth                                11    On time
## 18:26  London Paddington                       7     On time
## 18:27  Bedwyn                                  11    On time
## 18:32  London Paddington                       7B    On time
## 18:33  Cheltenham Spa                          10    On time
## 18:40  Bristol Temple Meads                    11    On time
## 18:41  London Waterloo                         6     On time
## 18:41  Manchester Piccadilly                   7     On time
## 18:42  Newbury                                 1     On time
## 18:43  London Paddington                       14    On time
## 18:44  London Paddington                       12    On time
## 18:45  Ash                                     5     On time
## 18:46  Swansea                                 10    On time
## 18:53  London Paddington                       9     On time
## 18:54  Great Malvern                           10    On time
## 18:56  London Paddington                       8     On time
## 18:57  Basingstoke                             2     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-04-10 16:04:40
## Time   To                                      Plat  Expected
## 17:05  London Paddington                       11    17:06
## 17:10  Newbury                                 1     On time
## 17:12  London Waterloo                         6     On time
## 17:13  Swansea                                 9     On time
## 17:15  Ealing Broadway                         15    On time
## 17:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 17:19  Hereford                                9     On time
## 17:22  Ealing Broadway                         14    On time
## 17:23  London Paddington                       11    On time
## 17:29  Penzance                                7     On time
## 17:34  Bedwyn                                  7B    On time
## 17:35  London Paddington                       11    On time
## 17:41  London Paddington                       10    On time
## 17:42  London Waterloo                         5     On time
## 17:50  London Paddington                       10    On time
## 17:52  Basingstoke                             2     On time
## 17:52  Ealing Broadway                         14    On time
## 17:55  Didcot Parkway                          12    On time
## 17:55  Weston-super-Mare                       9     Delayed
## 17:56  London Paddington                       10    On time
## 17:58  Cheltenham Spa                          8     On time
## 18:01  Ash                                     5     On time
## 18:10  Newbury                                 1     On time
## 18:12  London Waterloo                         6     On time
## 18:13  Ealing Broadway                         14    On time
## 18:13  Swansea                                 9     On time
## 18:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 18:19  London Paddington                       11    On time
## 18:19  Worcester Foregate Street               9     On time
## 18:22  Ealing Broadway                         13    On time
## 18:28  Penzance                                7     On time
## 18:30  London Paddington                       11    On time
## 18:34  Bedwyn                                  7B    On time
## 18:35  London Paddington                       10    On time
## 18:42  London Paddington                       11    On time
## 18:42  London Waterloo                         5     On time
## 18:49  Southampton Central                     7     On time
## 18:50  London Paddington                       10    On time
## 18:52  Basingstoke                             2     On time
## 18:52  Ealing Broadway                         14    On time
## 18:53  Didcot Parkway                          12    On time
## 18:55  Taunton                                 9     On time
## 18:56  London Paddington                       10    On time
## 18:58  Cheltenham Spa                          8     On time
```
