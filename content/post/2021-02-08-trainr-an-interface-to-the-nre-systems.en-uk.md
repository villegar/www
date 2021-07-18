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

## Example (Last rendered on 2021-07-18 08:16)

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
## Reading (RDG) Station Board on 2021-07-18 08:16:24
## Time   From                                    Plat  Expected
## 09:13  London Paddington                       12    On time
## 09:16  London Paddington                       7     09:25
## 09:23  London Paddington                       9     On time
## 09:26  Newbury                                 3     On time
## 09:28  Bristol Parkway                         10    On time
## 09:33  Basingstoke                             2     On time
## 09:38  Gatwick Airport                         13    On time
## 09:38  London Paddington                       14    On time
## 09:47  Salisbury                               1     On time
## 09:58  Didcot Parkway                          15    On time
## 10:01  London Paddington                       9     On time
## 10:07  Redhill                                 6     On time
## 10:08  Southampton Central                     12B   On time
## 10:10  London Paddington                       9     On time
## 10:14  Bedwyn                                  15    On time
## 10:14  London Paddington                       14    On time
## 10:16  London Paddington                       13    On time
## 10:26  London Paddington                       7     On time
## 10:26  Swansea                                 10    On time
## 10:33  Basingstoke                             2     On time
## 10:38  Gatwick Airport                         5     On time
## 10:39  Birmingham New Street                   13    On time
## 10:41  Exeter St Davids                        11    On time
## 10:44  London Paddington                       14    On time
## 10:45  Salisbury                               1     On time
## 10:53  Bristol Parkway                         10    On time
## 10:53  London Paddington                       9     On time
## 10:57  Great Malvern                           11    On time
## 11:01  London Paddington                       9     On time
## 11:07  Redhill                                 6     On time
## 11:08  Bournemouth                             7     On time
## 11:10  Didcot Parkway                          15    On time
## 11:12  London Paddington                       8     On time
## 11:14  London Paddington                       14    On time
## 09:21  Heathrow Central Bus Stn                BUS   On time
## 09:26  Staines                                 BUS   On time
## 09:27  Staines                                 BUS   On time
## 09:56  Staines                                 BUS   On time
## 09:59  Staines                                 BUS   On time
## 10:21  Heathrow Central Bus Stn                BUS   On time
## 10:27  Staines                                 BUS   On time
## 10:28  Staines                                 BUS   On time
## 10:56  Staines                                 BUS   On time
## 10:57  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-07-18 08:16:29
## Time   To                                      Plat  Expected
## 09:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 09:17  Penzance                                7     09:26
## 09:18  Didcot Parkway                          12    On time
## 09:21  Gatwick Airport                         13A   On time
##        via Guildford                           
## 09:29  Weston-super-Mare                       9     On time
## 09:30  Ealing Broadway                         14    On time
## 09:38  Basingstoke                             2     On time
## 09:40  London Paddington                       10    On time
## 09:41  Redhill                                 5     On time
## 09:44  Bedwyn                                  3     On time
## 09:52  Bournemouth                             8     On time
## 10:00  Ealing Broadway                         14    On time
## 10:03  Carmarthen                              9     On time
## 10:06  Ealing Broadway                         15    On time
## 10:11  Hereford                                9     On time
## 10:12  Salisbury                               1     On time
## 10:15  Manchester Piccadilly                   12B   On time
##        via Coventry & Stoke-on-Trent           
## 10:21  Gatwick Airport                         5     On time
##        via Guildford                           
## 10:26  Didcot Parkway                          13    On time
## 10:27  Exeter St Davids                        7     On time
## 10:30  Ealing Broadway                         14    On time
## 10:38  Basingstoke                             2     On time
## 10:40  London Paddington                       10    On time
## 10:41  Redhill                                 6     On time
## 10:44  Newbury                                 15    On time
## 10:45  London Paddington                       11    On time
## 10:54  Weston-super-Mare                       9     On time
## 11:00  Ealing Broadway                         14    On time
## 11:00  London Paddington                       10    On time
## 11:02  London Paddington                       11    On time
## 11:09  Swansea                                 9     On time
## 11:12  Ealing Broadway                         15    On time
## 11:12  Salisbury                               1     On time
## 11:14  Great Malvern                           8     On time
## 11:15  Manchester Piccadilly                   7     On time
##        via Coventry & Stoke-on-Trent           
## 09:25  Staines                                 BUS   On time
## 09:27  Staines                                 BUS   On time
## 09:55  Staines                                 BUS   On time
## 09:57  Staines                                 BUS   On time
## 10:00  Heathrow Central Bus Stn                BUS   On time
## 10:25  Staines                                 BUS   On time
## 10:27  Staines                                 BUS   On time
## 10:55  Staines                                 BUS   On time
## 10:57  Staines                                 BUS   On time
## 11:00  Heathrow Central Bus Stn                BUS   On time
```
