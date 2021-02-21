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

## Example (Last rendered on 2021-02-21 16:10)

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
## Reading (RDG) Station Board on 2021-02-21 16:10:40
## Time   From                                    Plat  Expected
## 16:09  Bristol Temple Meads                    10    On time
## 16:13  Didcot Parkway                          15    On time
## 16:14  London Paddington                       9B    On time
## 16:15  Slough                                  12    On time
## 16:24  London Paddington                       8     On time
## 16:26  London Paddington                       7     On time
## 16:27  Newbury                                 3     On time
## 16:31  London Paddington                       14    On time
## 16:32  Barnes                                  4     On time
## 16:33  Basingstoke                             2     On time
## 16:39  Manchester Piccadilly                   13    On time
## 16:45  Salisbury                               1     On time
## 16:50  Port Talbot Parkway                     10A   On time
## 16:56  London Paddington                       9     On time
## 16:57  Oxford                                  10    On time
## 16:59  London Paddington                       7B    On time
## 17:01  London Paddington                       14    On time
## 17:02  Clapham Junction                        4     On time
## 17:07  Bournemouth                             7B    On time
## 17:07  Gatwick Airport                         6     On time
## 17:10  Weston-super-Mare                       11    On time
## 17:13  Didcot Parkway                          15    On time
## 17:14  London Paddington                       9     On time
## 17:15  Slough                                  12    On time
## 17:17  Penzance                                10    On time
## 17:24  London Paddington                       8     On time
## 17:26  London Paddington                       7     On time
## 17:29  Bedwyn                                  1     On time
## 17:31  London Paddington                       14    On time
## 17:32  Barnes                                  4     On time
## 17:33  Basingstoke                             2     On time
## 17:39  Manchester Piccadilly                   7B    On time
## 17:45  Port Talbot Parkway                     11    On time
## 17:56  London Paddington                       9     On time
## 17:57  Oxford                                  10    On time
## 18:01  London Paddington                       14    On time
## 18:02  Clapham Junction                        4     On time
## 18:07  Gatwick Airport                         6     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-02-21 16:10:42
## Time   To                                      Plat  Expected
## 16:10  Ealing Broadway                         14    On time
## 16:12  Salisbury                               1     On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:16  Port Talbot Parkway                     9B    On time
## 16:19  London Paddington                       10    On time
## 16:20  Slough                                  15    On time
## 16:24  Barnes                                  4     On time
## 16:25  Didcot Parkway                          12    On time
## 16:26  Oxford                                  8     On time
## 16:27  Penzance                                7     On time
## 16:35  Newbury                                 3     On time
## 16:37  Ealing Broadway                         14    On time
## 16:38  Basingstoke                             2     On time
## 16:41  Gatwick Airport                         6     On time
##        via Guildford                           
## 16:51  London Paddington                       10A   On time
## 16:54  Clapham Junction                        4     On time
## 16:57  Bristol Temple Meads                    9     On time
## 17:01  Plymouth                                7B    On time
## 17:05  London Paddington                       10    On time
## 17:10  Ealing Broadway                         14    On time
## 17:12  Salisbury                               1     On time
## 17:15  Manchester Piccadilly                   7B    On time
##        via Coventry & Stoke-on-Trent           
## 17:16  London Paddington                       11    On time
## 17:16  Port Talbot Parkway                     9     On time
## 17:19  London Paddington                       10    On time
## 17:20  Slough                                  15    On time
## 17:24  Barnes                                  4     On time
## 17:25  Didcot Parkway                          12    On time
## 17:26  Oxford                                  8     On time
## 17:27  Penzance                                7     On time
## 17:35  Bedwyn                                  1     On time
## 17:38  Basingstoke                             2     On time
## 17:40  Ealing Broadway                         14    On time
## 17:41  Gatwick Airport                         6     On time
##        via Guildford                           
## 17:49  London Paddington                       11    On time
## 17:52  Bournemouth                             7B    On time
## 17:54  Clapham Junction                        4     On time
## 17:57  Weston-super-Mare                       9     On time
## 18:05  London Paddington                       10    On time
```
