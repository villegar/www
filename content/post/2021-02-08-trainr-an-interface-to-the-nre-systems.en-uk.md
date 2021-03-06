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

## Example (Last rendered on 2021-03-06 10:09)

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
## Reading (RDG) Station Board on 2021-03-06 10:09:50
## Time   From                                    Plat  Expected
## 10:01  Didcot Parkway                          -     On time
## 10:02  Exeter St Davids                        -     10:08
## 10:11  London Paddington                       -     On time
## 10:13  London Paddington                       -     10:07
## 10:13  Worcester Foregate Street               -     10:06
## 10:16  London Paddington                       -     10:19
## 10:22  Bedwyn                                  -     10:24
## 10:32  London Paddington                       -     On time
## 10:33  Redhill                                 -     On time
## 10:40  Bristol Temple Meads                    -     On time
## 10:40  Manchester Piccadilly                   -     On time
## 10:42  Newbury                                 -     On time
## 10:43  London Paddington                       -     On time
## 10:44  London Paddington                       -     On time
## 10:46  Port Talbot Parkway                     -     On time
## 10:53  London Paddington                       -     On time
## 10:54  Great Malvern                           -     On time
## 10:56  London Paddington                       -     On time
## 11:01  Didcot Parkway                          -     On time
## 11:01  Plymouth                                -     On time
## 11:06  Basingstoke                             -     On time
## 11:10  Bournemouth                             -     On time
## 11:11  London Paddington                       -     On time
## 11:13  London Paddington                       -     On time
## 11:16  London Paddington                       -     On time
## 11:21  Bedwyn                                  -     On time
## 11:32  London Paddington                       -     On time
## 11:33  Redhill                                 -     Delayed
## 11:34  Cheltenham Spa                          -     On time
## 11:38  Newbury                                 -     On time
## 11:39  Manchester Piccadilly                   -     On time
## 11:40  Bristol Temple Meads                    -     On time
## 11:43  London Paddington                       -     On time
## 11:44  London Paddington                       -     On time
## 11:46  Port Talbot Parkway                     -     Delayed
## 11:53  London Paddington                       -     On time
## 11:54  Great Malvern                           -     On time
## 11:56  London Paddington                       -     On time
## 11:57  Basingstoke                             -     On time
## 10:12  Ascot                                   -     On time
## 10:27  Ascot                                   -     On time
## 10:42  Ascot                                   -     On time
## 10:57  Ascot                                   -     On time
## 11:12  Ascot                                   -     On time
## 11:27  Ascot                                   -     On time
## 11:42  Ascot                                   -     On time
## 11:57  Ascot                                   -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-06 10:09:53
## Time   To                                      Plat  Expected
## 10:05  London Paddington                       -     10:09
## 10:09  Newbury                                 -     On time
## 10:13  Port Talbot Parkway                     -     On time
## 10:14  Ealing Broadway                         -     On time
## 10:14  London Paddington                       -     On time
## 10:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 10:19  Hereford                                -     10:20
## 10:20  Redhill                                 -     On time
## 10:22  Ealing Broadway                         -     On time
## 10:24  London Paddington                       -     10:24
## 10:29  Penzance                                -     On time
## 10:34  Bedwyn                                  -     On time
## 10:42  London Paddington                       -     On time
## 10:48  London Paddington                       -     On time
## 10:49  Bournemouth                             -     On time
## 10:52  Didcot Parkway                          -     On time
## 10:52  Ealing Broadway                         -     On time
## 10:54  Basingstoke                             -     On time
## 10:55  Bristol Temple Meads                    -     On time
## 10:56  London Paddington                       -     On time
## 10:58  Cheltenham Spa                          -     On time
## 11:05  London Paddington                       -     On time
## 11:10  Newbury                                 -     On time
## 11:13  Port Talbot Parkway                     -     On time
## 11:15  Ealing Broadway                         -     On time
## 11:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 11:19  Worcester Foregate Street               -     On time
## 11:20  Redhill                                 -     On time
## 11:22  Ealing Broadway                         -     On time
## 11:24  London Paddington                       -     On time
## 11:29  Plymouth                                -     On time
## 11:34  Bedwyn                                  -     On time
## 11:35  London Paddington                       -     On time
## 11:42  London Paddington                       -     On time
## 11:48  London Paddington                       -     Delayed
## 11:50  Basingstoke                             -     On time
## 11:52  Ealing Broadway                         -     On time
## 11:54  Didcot Parkway                          -     On time
## 11:55  Bristol Temple Meads                    -     On time
## 11:57  London Paddington                       -     On time
## 11:58  Cheltenham Spa                          -     On time
## 10:17  Ascot                                   -     On time
## 10:32  Ascot                                   -     On time
## 10:47  Ascot                                   -     On time
## 11:02  Ascot                                   -     On time
## 11:17  Ascot                                   -     On time
## 11:32  Ascot                                   -     On time
## 11:47  Ascot                                   -     On time
## 12:02  Ascot                                   -     On time
```
