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

## Example (Last rendered on 2021-03-06 12:10)

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
## Reading (RDG) Station Board on 2021-03-06 12:10:02
## Time   From                                    Plat  Expected
## 11:46  Port Talbot Parkway                     -     12:22
## 12:02  Didcot Parkway                          -     On time
## 12:11  London Paddington                       -     On time
## 12:13  London Paddington                       -     12:08
## 12:16  London Paddington                       -     12:18
## 12:17  Plymouth                                -     On time
## 12:26  London Paddington                       -     On time
## 12:27  Bedwyn                                  -     On time
## 12:32  London Paddington                       -     On time
## 12:33  Redhill                                 -     On time
## 12:39  Manchester Piccadilly                   -     On time
## 12:40  Weston-super-Mare                       -     On time
## 12:42  Newbury                                 -     On time
## 12:43  London Paddington                       -     On time
## 12:44  London Paddington                       -     On time
## 12:46  Port Talbot Parkway                     -     13:23
## 12:53  London Paddington                       -     On time
## 12:54  Great Malvern                           -     On time
## 12:57  Basingstoke                             -     On time
## 13:00  Penzance                                -     On time
## 13:02  Didcot Parkway                          -     On time
## 13:10  Bournemouth                             -     On time
## 13:11  London Paddington                       -     On time
## 13:13  London Paddington                       -     On time
## 13:16  London Paddington                       -     On time
## 13:21  Bedwyn                                  -     On time
## 13:32  London Paddington                       -     On time
## 13:33  Redhill                                 -     On time
## 13:38  Newbury                                 -     On time
## 13:39  Manchester Piccadilly                   -     On time
## 13:40  Bristol Temple Meads                    -     On time
## 13:42  Exeter St Davids                        -     On time
## 13:43  London Paddington                       -     On time
## 13:44  London Paddington                       -     On time
## 13:46  Port Talbot Parkway                     -     Delayed
## 13:53  London Paddington                       -     On time
## 13:54  Great Malvern                           -     On time
## 13:56  Basingstoke                             -     On time
## 13:56  London Paddington                       -     On time
## 13:59  Penzance                                -     On time
## 12:12  Ascot                                   -     On time
## 12:27  Ascot                                   -     On time
## 12:42  Ascot                                   -     On time
## 12:57  Ascot                                   -     On time
## 13:12  Ascot                                   -     On time
## 13:27  Ascot                                   -     On time
## 13:42  Ascot                                   -     On time
## 13:57  Ascot                                   -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-06 12:10:05
## Time   To                                      Plat  Expected
## 11:48  London Paddington                       -     12:23
## 12:10  Newbury                                 -     On time
## 12:11  Ealing Broadway                         -     On time
## 12:13  Port Talbot Parkway                     -     On time
## 12:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 12:19  Hereford                                -     On time
## 12:19  London Paddington                       -     On time
## 12:20  Redhill                                 -     On time
## 12:22  Ealing Broadway                         -     On time
## 12:29  Penzance                                -     On time
## 12:30  London Paddington                       -     On time
## 12:34  Bedwyn                                  -     On time
## 12:42  London Paddington                       -     On time
## 12:48  London Paddington                       -     13:24
## 12:49  Bournemouth                             -     On time
## 12:52  Basingstoke                             -     On time
## 12:52  Ealing Broadway                         -     On time
## 12:53  Didcot Parkway                          -     On time
## 12:55  Bristol Temple Meads                    -     On time
## 12:57  London Paddington                       -     On time
## 13:05  London Paddington                       -     On time
## 13:10  Newbury                                 -     On time
## 13:13  Port Talbot Parkway                     -     On time
## 13:15  Ealing Broadway                         -     On time
## 13:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 13:19  Worcester Foregate Street               -     On time
## 13:20  Redhill                                 -     On time
## 13:22  Ealing Broadway                         -     On time
## 13:23  London Paddington                       -     On time
## 13:29  Penzance                                -     On time
## 13:34  Bedwyn                                  -     On time
## 13:41  London Paddington                       -     On time
## 13:45  London Paddington                       -     On time
## 13:48  London Paddington                       -     Delayed
## 13:52  Basingstoke                             -     On time
## 13:52  Ealing Broadway                         -     On time
## 13:54  Didcot Parkway                          -     On time
## 13:55  Bristol Temple Meads                    -     On time
## 13:56  London Paddington                       -     On time
## 13:58  Cheltenham Spa                          -     On time
## 14:05  London Paddington                       -     On time
## 12:17  Ascot                                   -     On time
## 12:32  Ascot                                   -     On time
## 12:47  Ascot                                   -     On time
## 13:02  Ascot                                   -     On time
## 13:17  Ascot                                   -     On time
## 13:32  Ascot                                   -     On time
## 13:47  Ascot                                   -     On time
## 14:02  Ascot                                   -     On time
```
