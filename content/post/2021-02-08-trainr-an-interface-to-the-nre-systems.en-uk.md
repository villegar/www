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

## Example (Last rendered on 2021-03-28 16:04)

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
## Reading (RDG) Station Board on 2021-03-28 16:04:47
## Time   From                                    Plat  Expected
## 16:57  Worcester Foregate Street               11    On time
## 16:59  London Paddington                       9     17:16
## 17:07  Southampton Central                     7B    On time
## 17:10  Weston-super-Mare                       10    On time
## 17:12  London Paddington                       9B    17:20
## 17:13  Didcot Parkway                          15    On time
## 17:14  London Paddington                       14    On time
## 17:15  Slough                                  12    On time
## 17:16  Ash                                     6     On time
## 17:17  Plymouth                                11    On time
## 17:23  London Paddington                       9     Delayed
## 17:26  London Paddington                       7B    On time
## 17:29  Bedwyn                                  8B    On time
## 17:33  Basingstoke                             2     On time
## 17:39  Manchester Piccadilly                   7B    On time
## 17:40  Bristol Temple Meads                    10    On time
## 17:44  London Paddington                       14    On time
## 17:45  Swansea                                 11    On time
## 17:54  London Paddington                       9B    On time
## 17:57  Hereford                                11A   On time
## 17:59  London Paddington                       9     On time
## 18:10  Bristol Temple Meads                    10    On time
## 18:12  London Paddington                       9B    On time
## 18:13  Didcot Parkway                          15    On time
## 18:14  London Paddington                       14    On time
## 18:14  Plymouth                                11    On time
## 18:15  Slough                                  12    On time
## 18:16  Ash                                     6     On time
## 18:23  London Paddington                       9     On time
## 18:26  London Paddington                       7     On time
## 18:32  Basingstoke                             2     On time
## 18:35  Newbury                                 1     On time
## 18:39  Manchester Piccadilly                   13B   On time
## 18:40  Bristol Temple Meads                    10    On time
## 18:44  London Paddington                       14    On time
## 18:45  Swansea                                 11    On time
## 18:54  London Paddington                       8     On time
## 17:09  Staines                                 BUS   On time
## 17:35  Staines                                 BUS   On time
## 17:50  Staines                                 BUS   On time
## 17:54  Staines                                 BUS   On time
## 18:09  Staines                                 BUS   On time
## 18:35  Staines                                 BUS   On time
## 18:50  Staines                                 BUS   On time
## 18:54  Staines                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-28 16:04:50
## Time   To                                      Plat  Expected
## 17:04  Ealing Broadway                         14    On time
## 17:07  London Paddington                       11    On time
## 17:09  Swansea                                 9     17:19
## 17:14  Worcester Foregate Street               9B    17:21
## 17:15  London Paddington                       10    On time
## 17:15  Manchester Piccadilly                   7B    On time
##        via Coventry & Stoke-on-Trent           
## 17:15  Slough                                  15    On time
## 17:20  London Paddington                       11    On time
## 17:24  Bristol Temple Meads                    9     Delayed
## 17:25  Didcot Parkway                          12    On time
## 17:27  Plymouth                                7B    On time
## 17:35  Bedwyn                                  8B    On time
## 17:36  Ealing Broadway                         14    On time
## 17:38  Basingstoke                             2     On time
## 17:41  Ash                                     5     On time
## 17:45  London Paddington                       10    On time
## 17:48  London Paddington                       11    On time
## 17:52  Southampton Central                     7B    On time
## 17:55  Weston-super-Mare                       9B    On time
## 18:06  Ealing Broadway                         14    On time
## 18:07  London Paddington                       11A   On time
## 18:09  Swansea                                 9     On time
## 18:14  Great Malvern                           9B    On time
## 18:15  Manchester Piccadilly                   13B   On time
##        via Coventry & Stoke-on-Trent           
## 18:15  Slough                                  15    On time
## 18:18  London Paddington                       10    On time
## 18:20  London Paddington                       11    On time
## 18:24  Plymouth                                9     On time
##        via Bristol                             
## 18:25  Didcot Parkway                          12    On time
## 18:27  Plymouth                                7     On time
## 18:36  Ealing Broadway                         14    On time
## 18:38  Basingstoke                             2     On time
## 18:41  Ash                                     5     On time
## 18:45  London Paddington                       10    On time
## 18:50  London Paddington                       11    On time
## 18:50  Newbury                                 1     On time
## 18:55  Weston-super-Mare                       8     On time
## 17:15  Staines                                 BUS   On time
## 17:30  Staines                                 BUS   On time
## 17:50  Staines                                 BUS   On time
## 17:55  Staines                                 BUS   On time
## 18:15  Staines                                 BUS   On time
## 18:30  Staines                                 BUS   On time
## 18:50  Staines                                 BUS   On time
## 18:55  Staines                                 BUS   On time
```
