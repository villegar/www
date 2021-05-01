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

## Example (Last rendered on 2021-05-01 14:10)

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
## Reading (RDG) Station Board on 2021-05-01 14:10:41
## Time   From                                    Plat  Expected
## 15:01  Didcot Parkway                          15A   On time
## 15:10  Bournemouth                             13    On time
## 15:11  London Paddington                       8     On time
## 15:11  London Waterloo                         4     On time
## 15:13  London Paddington                       14    15:06
## 15:16  London Paddington                       9B    On time
## 15:20  Penzance                                11    15:25
## 15:33  Redhill                                 5     On time
## 15:39  Manchester Piccadilly                   13    On time
## 15:40  Bristol Temple Meads                    10    On time
## 15:41  London Waterloo                         6     On time
## 15:43  London Paddington                       14    On time
## 15:44  London Paddington                       12B   On time
## 15:47  Swansea                                 10    On time
## 15:51  Gatwick Airport                         4     On time
## 15:53  London Paddington                       9     On time
## 15:54  Hereford                                10A   On time
## 15:57  Basingstoke                             2     On time
## 16:01  Didcot Parkway                          15A   On time
## 16:07  London Paddington                       8     On time
## 16:11  London Paddington                       9     On time
## 16:11  London Waterloo                         5     On time
## 16:13  London Paddington                       14    On time
## 16:16  London Paddington                       9B    On time
## 16:25  Plymouth                                11    On time
## 16:33  Redhill                                 6     On time
## 16:39  Manchester Piccadilly                   7     On time
## 16:40  Bristol Temple Meads                    10    On time
## 16:41  London Waterloo                         4     On time
## 16:43  London Paddington                       14    On time
## 16:44  London Paddington                       12B   On time
## 16:46  Swansea                                 10    On time
## 16:51  Gatwick Airport                         5     On time
## 16:53  London Paddington                       9     On time
## 16:54  Worcester Foregate Street               10A   On time
## 16:56  Basingstoke                             2     On time
## 15:12  Bedwyn                                  BUS   On time
## 15:19  Newbury                                 BUS   On time
## 15:55  Newbury                                 BUS   On time
## 16:12  Bedwyn                                  BUS   On time
## 16:17  Newbury                                 BUS   On time
## 16:55  Newbury                                 BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-01 14:10:44
## Time   To                                      Plat  Expected
## 15:12  London Waterloo                         6     On time
## 15:13  Swansea                                 8     On time
## 15:15  Ealing Broadway                         15A   On time
## 15:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 15:19  Great Malvern                           9B    On time
## 15:20  Redhill                                 5     On time
## 15:22  Ealing Broadway                         14    On time
## 15:26  London Paddington                       11    On time
## 15:41  London Paddington                       10    On time
## 15:42  London Waterloo                         4     On time
## 15:50  London Paddington                       10    On time
## 15:52  Basingstoke                             2     On time
## 15:52  Ealing Broadway                         14    On time
## 15:53  Didcot Parkway                          12B   On time
## 15:55  Bristol Temple Meads                    9     On time
## 15:56  London Paddington                       10A   On time
## 16:01  Gatwick Airport                         5     On time
##        via Guildford                           
## 16:08  Plymouth                                8     On time
## 16:12  London Waterloo                         6     On time
## 16:13  Swansea                                 9     On time
## 16:15  Ealing Broadway                         15A   On time
## 16:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 16:19  Great Malvern                           9B    On time
## 16:20  Redhill                                 4     On time
## 16:22  Ealing Broadway                         14    On time
## 16:26  London Paddington                       11    On time
## 16:41  London Paddington                       10    On time
## 16:42  London Waterloo                         5     On time
## 16:48  London Paddington                       10    On time
## 16:49  Bournemouth                             7     On time
## 16:52  Basingstoke                             2     On time
## 16:52  Ealing Broadway                         14    On time
## 16:53  Didcot Parkway                          12B   On time
## 16:55  Bristol Temple Meads                    9     On time
## 16:56  London Paddington                       10A   On time
## 17:01  Gatwick Airport                         6     On time
##        via Guildford                           
## 15:10  Newbury                                 BUS   On time
## 15:34  Bedwyn                                  BUS   On time
## 15:36  Newbury                                 BUS   On time
## 16:10  Newbury                                 BUS   On time
## 16:34  Bedwyn                                  BUS   On time
## 16:36  Newbury                                 BUS   On time
```
