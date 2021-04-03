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

## Example (Last rendered on 2021-04-03 08:04)

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
## Reading (RDG) Station Board on 2021-04-03 08:04:02
## Time   From                                    Plat  Expected
## 08:59  London Paddington                       7     On time
## 09:01  Didcot Parkway                          15    On time
## 09:03  Plymouth                                11    08:55
## 09:10  Southampton Central                     13    On time
## 09:11  London Paddington                       8     On time
## 09:13  London Paddington                       14    On time
## 09:13  Westbury                                11    On time
## 09:14  London Waterloo                         4     On time
## 09:16  London Paddington                       9     On time
## 09:30  Bedwyn                                  11    On time
## 09:31  London Paddington                       7B    On time
## 09:33  Cheltenham Spa                          10    On time
## 09:38  Newbury                                 1     On time
## 09:40  Bristol Temple Meads                    10    On time
## 09:40  Nottingham                              13    On time
## 09:43  London Paddington                       14    On time
## 09:44  London Paddington                       12    On time
## 09:44  London Waterloo                         6     On time
## 09:46  Swansea                                 10    On time
## 09:53  London Paddington                       9     On time
## 09:54  Hereford                                10A   On time
## 09:57  Ash                                     4     On time
## 09:57  Basingstoke                             2     On time
## 10:00  Exeter St Davids                        11    On time
## 10:01  Didcot Parkway                          15    On time
## 10:07  London Paddington                       8     On time
## 10:11  London Paddington                       9     On time
## 10:13  London Paddington                       14    On time
## 10:13  Worcester Foregate Street               11    On time
## 10:14  London Waterloo                         5     On time
## 10:16  London Paddington                       9     On time
## 10:22  Bedwyn                                  11    On time
## 10:32  London Paddington                       7B    On time
## 10:40  Bristol Temple Meads                    11    On time
## 10:40  Manchester Piccadilly                   7     On time
## 10:42  Newbury                                 1     On time
## 10:43  London Paddington                       14    On time
## 10:44  London Paddington                       12    On time
## 10:44  London Waterloo                         6     On time
## 10:46  Carmarthen                              10    On time
## 10:53  London Paddington                       9     On time
## 10:54  Great Malvern                           10    On time
## 10:56  London Paddington                       8     On time
## 10:57  Ash                                     5     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-04-03 08:04:05
## Time   To                                      Plat  Expected
## 09:05  London Paddington                       11    On time
## 09:08  Newbury                                 1     On time
## 09:12  London Waterloo                         6     On time
## 09:13  Swansea                                 8     On time
## 09:15  Ealing Broadway                         15    On time
## 09:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 09:20  Great Malvern                           9     On time
## 09:20  London Paddington                       11    On time
## 09:22  Ealing Broadway                         14    On time
## 09:32  London Paddington                       11    On time
## 09:33  Bedwyn                                  7B    On time
## 09:35  Ash                                     5     On time
## 09:35  London Paddington                       10    On time
## 09:42  London Paddington                       10    On time
## 09:42  London Waterloo                         4     On time
## 09:48  London Paddington                       10    On time
## 09:52  Basingstoke                             2     On time
## 09:52  Ealing Broadway                         14    On time
## 09:53  Didcot Parkway                          12    On time
## 09:55  Bristol Temple Meads                    9     On time
## 09:56  London Paddington                       10A   On time
## 10:05  London Paddington                       11    On time
## 10:09  Newbury                                 1     On time
## 10:09  Penzance                                8     On time
## 10:12  London Waterloo                         6     On time
## 10:13  Swansea                                 9     On time
## 10:14  Ealing Broadway                         15    On time
## 10:14  London Paddington                       11    On time
## 10:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 10:19  Hereford                                9     On time
## 10:22  Ealing Broadway                         14    On time
## 10:24  London Paddington                       11    On time
## 10:29  Westbury                                8     On time
## 10:34  Bedwyn                                  7B    On time
## 10:35  Ash                                     4     On time
## 10:42  London Paddington                       11    On time
## 10:42  London Waterloo                         5     On time
## 10:48  London Paddington                       10    On time
## 10:49  Southampton Central                     7     On time
## 10:52  Didcot Parkway                          12    On time
## 10:52  Ealing Broadway                         14    On time
## 10:54  Basingstoke                             2     On time
## 10:55  Bristol Temple Meads                    9     On time
## 10:56  London Paddington                       10    On time
## 10:58  Cheltenham Spa                          8     On time
```
