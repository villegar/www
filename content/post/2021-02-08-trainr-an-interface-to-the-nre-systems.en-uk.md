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

## Example (Last rendered on 2022-01-20 20:03)

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
## Reading (RDG) Station Board on 2022-01-20 20:04:00
## Time   From                                    Plat  Expected
## 19:57  Didcot Parkway                          15    On time
## 20:03  Newbury                                 2     20:05
## 20:04  Gatwick Airport                         4     On time
## 20:06  Bournemouth                             8     On time
## 20:09  London Paddington                       13    On time
## 20:10  Weston-super-Mare                       10    On time
## 20:11  London Paddington                       9     On time
## 20:14  London Paddington                       13    On time
## 20:15  London Waterloo                         6     On time
## 20:17  London Paddington                       9B    On time
## 20:18  London Paddington                       12    On time
## 20:25  London Paddington                       9     On time
## 20:28  Banbury                                 11A   On time
## 20:32  Cheltenham Spa                          10A   On time
## 20:34  Basingstoke                             2     On time
## 20:34  Didcot Parkway                          13A   On time
## 20:35  Redhill                                 14A   On time
## 20:36  London Paddington                       8     On time
## 20:43  London Paddington                       14    On time
## 20:43  Manchester Piccadilly                   7     On time
## 20:44  Newbury                                 1     On time
## 20:44  Swansea                                 10    On time
## 20:47  London Paddington                       9B    On time
## 20:48  London Waterloo                         5     On time
## 20:49  London Paddington                       12    On time
## 20:53  Gatwick Airport                         6     On time
## 20:53  Great Malvern                           11    On time
## 21:00  Penzance                                10    On time
## 21:03  Didcot Parkway                          15    On time
## 21:04  Basingstoke                             2     On time
## 21:09  Bristol Temple Meads                    10    On time
## 21:10  London Paddington                       13    On time
## 21:10  London Waterloo                         4     On time
## 21:11  London Paddington                       9     On time
## 21:13  London Paddington                       14    On time
## 21:16  London Paddington                       12    On time
## 21:16  London Paddington                       9     On time
## 21:21  Bedwyn                                  11    On time
## 21:24  Oxford                                  10    On time
## 21:25  London Paddington                       9     On time
## 21:27  London Paddington                       7     On time
## 21:28  Basingstoke                             2     On time
## 21:29  Didcot Parkway                          14    On time
## 21:29  Redhill                                 5     On time
## 21:33  Cheltenham Spa                          10    On time
## 21:38  Newbury                                 1     On time
## 21:40  London Waterloo                         6     On time
## 21:41  Manchester Piccadilly                   7     On time
## 21:43  London Paddington                       14    On time
## 21:44  Swansea                                 10    On time
## 21:46  London Paddington                       9     On time
## 21:48  London Paddington                       12    On time
## 21:51  London Paddington                       9     On time
## 21:53  Great Malvern                           10    On time
## 21:56  Gatwick Airport                         14B   On time
## 21:57  Basingstoke                             3     On time
## 20:13  Heathrow Central Bus Stn                BUS   On time
## 21:03  Heathrow Central Bus Stn                BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2022-01-20 20:04:03
## Time   To                                      Plat  Expected
## 20:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 20:10  Newbury                                 2     On time
## 20:12  London Paddington                       10    On time
## 20:12  London Waterloo                         6     On time
## 20:13  Swansea                                 9     On time
## 20:15  Birmingham New Street                   8     On time
##        via Coventry                            
## 20:15  Ealing Broadway                         15    On time
## 20:19  Worcester Shrub Hill                    9B    On time
## 20:20  Shalford                                4     On time
## 20:21  Basingstoke                             1     On time
## 20:22  Ealing Broadway                         13    On time
## 20:23  Didcot Parkway                          12    On time
## 20:27  Bristol Temple Meads                    9     On time
## 20:31  London Paddington                       11A   On time
## 20:36  London Paddington                       10A   On time
## 20:37  Newbury                                 8     On time
## 20:42  Ealing Broadway                         13A   On time
## 20:42  London Waterloo                         6     On time
## 20:47  London Paddington                       10    On time
## 20:49  Oxford                                  9B    On time
## 20:51  Didcot Parkway                          12    On time
## 20:52  Basingstoke                             2     On time
## 20:52  Ealing Broadway                         14    On time
## 20:56  London Paddington                       11    On time
## 21:01  Gatwick Airport                         6     On time
##        via Guildford                           
## 21:03  London Paddington                       10    On time
## 21:08  Ealing Broadway                         15    On time
## 21:10  Newbury                                 1     On time
## 21:11  London Paddington                       10    On time
## 21:12  London Waterloo                         5     On time
## 21:13  Birmingham New Street                   7     On time
##        via Coventry                            
## 21:13  Swansea                                 9     On time
## 21:18  Great Malvern                           9     On time
## 21:22  Basingstoke                             2     On time
## 21:22  Ealing Broadway                         14    On time
## 21:23  Didcot Parkway                          12    On time
## 21:23  London Paddington                       11    On time
## 21:26  London Paddington                       10    On time
## 21:27  Bristol Temple Meads                    9     On time
## 21:29  Plymouth                                7     On time
## 21:34  Gatwick Airport                         5     On time
##        via Guildford                           
## 21:38  Ealing Broadway                         14    On time
## 21:38  London Paddington                       10    On time
## 21:42  London Waterloo                         4     On time
## 21:46  London Paddington                       10    On time
## 21:48  Oxford                                  9     On time
## 21:49  Didcot Parkway                          12    On time
## 21:52  Bournemouth                             7     On time
## 21:52  Ealing Broadway                         14    On time
## 21:53  Cheltenham Spa                          9     On time
## 21:56  London Paddington                       10    On time
## 21:00  Heathrow Central Bus Stn                BUS   On time
## 22:00  Heathrow Central Bus Stn                BUS   On time
```
