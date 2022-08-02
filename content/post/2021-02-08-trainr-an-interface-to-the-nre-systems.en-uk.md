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

## Example (Last rendered on 2022-08-02 04:30)

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
## Reading (RDG) Station Board on 2022-08-02 04:30:30
## Time   From                                    Plat  Expected
## 05:35  Didcot Parkway                          15    On time
## 05:38  London Paddington                       9     On time
## 05:46  Oxford                                  11A   On time
## 05:47  London Paddington                       9     On time
## 05:58  Bristol Temple Meads                    11    On time
## 05:58  London Paddington                       9B    On time
## 05:59  Newbury                                 1     On time
## 06:05  Southampton Central                     8     On time
## 06:08  London Paddington                       9     On time
## 06:11  Staines                                 5     On time
## 06:12  Didcot Parkway                          15    On time
## 06:14  Bedwyn                                  11A   On time
## 06:16  London Paddington                       9B    On time
## 06:16  London Paddington                       13    On time
## 06:25  Cheltenham Spa                          10A   On time
## 06:28  Oxford                                  11A   On time
## 06:31  Basingstoke                             2     On time
## 06:31  Bristol Temple Meads                    10    On time
## 06:41  Bedwyn                                  11A   On time
## 06:41  London Paddington                       14    On time
## 06:41  London Waterloo                         6     On time
## 06:45  London Paddington                       12    On time
## 06:49  Swansea                                 10    On time
## 06:51  London Paddington                       8B    On time
## 06:51  Redhill                                 5     On time
## 06:52  Basingstoke                             1     On time
## 06:53  Worcester Shrub Hill                    10    On time
## 06:55  London Paddington                       9     On time
## 06:59  Bristol Temple Meads                    11    On time
## 06:59  Didcot Parkway                          15    On time
## 07:00  London Paddington                       8     On time
## 07:00  Newbury                                 1     On time
## 07:06  London Paddington                       14    On time
## 07:08  Bristol Temple Meads                    11    On time
## 07:09  Hereford                                10    On time
## 07:11  London Paddington                       12    On time
## 07:11  London Paddington                       9     On time
## 07:11  London Waterloo                         4     On time
## 07:12  Didcot Parkway                          15    On time
## 07:16  London Paddington                       12    On time
## 07:16  London Paddington                       8B    On time
## 07:18  Swansea                                 10    On time
## 07:21  Newbury                                 11    On time
## 07:25  London Paddington                       9     On time
## 07:27  London Paddington                       13    On time
## 07:29  Basingstoke                             2     On time
## 06:18  Heathrow Central Bus Stn                -     On time
## 07:24  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-08-02 04:30:33
## Time   To                                      Plat  Expected
## 05:31  Gatwick Airport                         15A   On time
##        via Guildford                           
## 05:36  Ealing Broadway                         15    On time
## 05:39  Oxford                                  9     On time
## 05:40  Basingstoke                             14B   On time
## 05:42  London Waterloo                         5     On time
## 05:48  London Paddington                       11A   On time
## 05:49  Didcot Parkway                          13    On time
## 05:49  Swansea                                 9     On time
## 05:50  Newbury                                 3     On time
## 05:54  Redhill                                 15A   On time
## 06:00  Ealing Broadway                         14    On time
## 06:00  London Paddington                       11    On time
## 06:00  Worcester Shrub Hill                    9B    On time
##        via Gloucester                          
## 06:10  Bristol Temple Meads                    9     On time
## 06:11  London Waterloo                         6     On time
## 06:13  Newbury                                 13    On time
## 06:15  London Paddington                       11A   On time
## 06:15  Manchester Piccadilly                   8     On time
##        via Coventry & Stoke-on-Trent           
## 06:18  Great Malvern                           9B    On time
## 06:19  Basingstoke                             14B   On time
## 06:19  London Paddington                       15    On time
## 06:24  Oxford                                  14B   On time
## 06:26  Gatwick Airport                         15A   On time
##        via Guildford                           
## 06:28  London Paddington                       10A   On time
## 06:30  Ealing Broadway                         13    On time
## 06:34  London Paddington                       10    On time
## 06:36  London Paddington                       11A   On time
## 06:37  Newbury                                 1     On time
## 06:40  Basingstoke                             2     On time
## 06:41  London Waterloo                         5     On time
## 06:42  London Paddington                       11A   On time
## 06:48  London Paddington                       15    On time
## 06:50  Gatwick Airport                         13A   On time
##        via Guildford                           
## 06:50  London Paddington                       10    On time
## 06:53  Cheltenham Spa                          8B    On time
## 06:55  Didcot Parkway                          12    On time
## 06:56  Ealing Broadway                         14    On time
## 06:56  London Paddington                       10    On time
## 06:57  Basingstoke                             1     On time
## 06:57  Bristol Temple Meads                    9     On time
## 07:02  London Paddington                       15    On time
## 07:02  London Paddington                       11    On time
## 07:03  Penzance                                8     On time
## 07:10  London Paddington                       11    On time
## 07:10  Newbury                                 1     On time
## 07:11  London Waterloo                         6     On time
## 07:12  London Paddington                       10    On time
## 07:13  Ealing Broadway                         14    On time
## 07:13  Swansea                                 9     On time
## 07:14  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 07:17  London Paddington                       15    On time
## 07:18  Great Malvern                           8B    On time
## 07:20  London Paddington                       10    On time
## 07:20  Redhill                                 5     On time
## 07:24  London Paddington                       11    On time
## 07:25  Didcot Parkway                          12    On time
## 07:26  Ealing Broadway                         14    On time
## 07:27  Bristol Temple Meads                    9     On time
## 06:00  Heathrow Central Bus Stn                BUS   On time
## 06:35  Heathrow Central Bus Stn                BUS   On time
## 07:10  Heathrow Central Bus Stn                BUS   On time
```
