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

## Example (Last rendered on 2021-03-06 16:13)

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
## Reading (RDG) Station Board on 2021-03-06 16:13:55
## Time   From                                    Plat  Expected
## 14:46  Port Talbot Parkway                     -     Delayed
## 15:47  Port Talbot Parkway                     -     Delayed
## 16:01  Didcot Parkway                          -     On time
## 16:05  Swindon                                 -     On time
## 16:11  London Paddington                       -     On time
## 16:13  London Paddington                       -     16:07
## 16:16  London Paddington                       -     On time
## 16:17  Plymouth                                -     On time
## 16:26  London Paddington                       -     16:28
## 16:27  Bedwyn                                  -     On time
## 16:31  London Paddington                       -     On time
## 16:33  Redhill                                 -     On time
## 16:39  Manchester Piccadilly                   -     On time
## 16:40  Bristol Temple Meads                    -     Cancelled
## 16:41  Newbury                                 -     On time
## 16:43  London Paddington                       -     On time
## 16:44  London Paddington                       -     On time
## 16:46  Port Talbot Parkway                     -     17:05
## 16:53  London Paddington                       -     On time
## 16:54  Worcester Foregate Street               -     On time
## 16:56  Basingstoke                             -     On time
## 16:56  London Paddington                       -     On time
## 17:01  Didcot Parkway                          -     On time
## 17:01  Penzance                                -     On time
## 17:05  Bournemouth                             -     On time
## 17:11  London Paddington                       -     On time
## 17:13  London Paddington                       -     On time
## 17:16  London Paddington                       -     On time
## 17:21  Bedwyn                                  -     On time
## 17:32  London Paddington                       -     On time
## 17:33  Cheltenham Spa                          -     Delayed
## 17:33  Redhill                                 -     On time
## 17:38  Newbury                                 -     On time
## 17:39  Manchester Piccadilly                   -     On time
## 17:40  Bristol Temple Meads                    -     On time
## 17:43  London Paddington                       -     On time
## 17:44  London Paddington                       -     On time
## 17:48  Port Talbot Parkway                     -     18:02
## 17:53  London Paddington                       -     On time
## 17:54  Hereford                                -     On time
## 17:56  London Paddington                       -     On time
## 17:57  Basingstoke                             -     On time
## 16:12  Ascot                                   -     On time
## 16:27  Ascot                                   -     On time
## 16:42  Ascot                                   -     On time
## 16:57  Ascot                                   -     On time
## 17:12  Ascot                                   -     On time
## 17:27  Ascot                                   -     On time
## 17:42  Ascot                                   -     On time
## 17:57  Ascot                                   -     On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-03-06 16:13:57
## Time   To                                      Plat  Expected
## 14:48  London Paddington                       -     Delayed
## 15:50  London Paddington                       -     Delayed
## 16:05  London Paddington                       -     16:13
## 16:13  Port Talbot Parkway                     -     On time
## 16:15  Ealing Broadway                         -     On time
## 16:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 16:19  Great Malvern                           -     On time
## 16:19  London Paddington                       -     On time
## 16:20  Redhill                                 -     On time
## 16:22  Ealing Broadway                         -     On time
## 16:28  Plymouth                                -     16:28
## 16:30  London Paddington                       -     On time
## 16:34  Bedwyn                                  -     On time
## 16:41  London Paddington                       -     Cancelled
## 16:48  London Paddington                       -     17:06
## 16:49  Bournemouth                             -     On time
## 16:52  Basingstoke                             -     On time
## 16:52  Ealing Broadway                         -     On time
## 16:53  Didcot Parkway                          -     On time
## 16:55  Bristol Temple Meads                    -     On time
## 16:56  London Paddington                       -     On time
## 16:58  Cheltenham Spa                          -     On time
## 17:05  London Paddington                       -     On time
## 17:10  Newbury                                 -     On time
## 17:13  Port Talbot Parkway                     -     On time
## 17:15  Ealing Broadway                         -     On time
## 17:15  Manchester Piccadilly                   -     On time
##        via Coventry & Stoke-on-Trent           
## 17:19  Hereford                                -     On time
## 17:20  Redhill                                 -     On time
## 17:22  Ealing Broadway                         -     On time
## 17:23  London Paddington                       -     On time
## 17:29  Penzance                                -     On time
## 17:34  Bedwyn                                  -     On time
## 17:35  London Paddington                       -     Delayed
## 17:41  London Paddington                       -     On time
## 17:50  London Paddington                       -     18:03
## 17:52  Basingstoke                             -     On time
## 17:52  Ealing Broadway                         -     On time
## 17:55  Didcot Parkway                          -     On time
## 17:55  Weston-super-Mare                       -     On time
## 17:56  London Paddington                       -     On time
## 17:58  Cheltenham Spa                          -     On time
## 18:10  Newbury                                 -     On time
## 16:17  Ascot                                   -     On time
## 16:32  Ascot                                   -     On time
## 16:47  Ascot                                   -     On time
## 17:02  Ascot                                   -     On time
## 17:17  Ascot                                   -     On time
## 17:32  Ascot                                   -     On time
## 17:47  Ascot                                   -     On time
## 18:02  Ascot                                   -     On time
```
