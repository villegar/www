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

## Example (Last rendered on 2021-05-01 06:16)

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
## Reading (RDG) Station Board on 2021-05-01 06:16:12
## Time   From                                    Plat  Expected
## 07:01  Didcot Parkway                          15A   On time
## 07:04  Gatwick Airport                         5     07:30
## 07:08  Southampton Central                     13    On time
## 07:16  London Paddington                       9B    On time
## 07:39  Bristol Temple Meads                    10    On time
## 07:40  Birmingham New Street                   13    On time
## 07:41  London Waterloo                         5     On time
## 07:43  London Paddington                       14    On time
## 07:44  London Paddington                       12B   On time
## 07:45  Swansea                                 11    On time
## 07:53  London Paddington                       8     On time
## 07:54  Great Malvern                           10    On time
## 07:58  Basingstoke                             2     On time
## 08:04  Didcot Parkway                          15A   On time
## 08:07  London Paddington                       8     On time
## 08:11  London Paddington                       9     On time
## 08:11  London Waterloo                         4     On time
## 08:13  London Paddington                       14    On time
## 08:16  London Paddington                       9B    On time
## 08:33  Redhill                                 5     On time
## 08:37  Manchester Piccadilly                   8     On time
## 08:41  Bristol Temple Meads                    11    On time
## 08:41  London Waterloo                         6     On time
## 08:43  London Paddington                       14    On time
## 08:44  London Paddington                       12B   On time
## 08:46  Swansea                                 10    On time
## 08:51  Gatwick Airport                         4     On time
## 08:53  London Paddington                       9     On time
## 08:54  Hereford                                10    On time
## 08:57  Basingstoke                             2     On time
## 09:01  Didcot Parkway                          15A   On time
## 09:07  London Paddington                       9     On time
## 09:10  Bournemouth                             13    On time
## 09:11  London Paddington                       8     On time
## 09:11  London Waterloo                         4     On time
## 09:13  London Paddington                       14    On time
## 07:27  Bedwyn                                  BUS   On time
## 08:07  Bedwyn                                  BUS   On time
## 09:00  Newbury                                 BUS   On time
## 09:07  Bedwyn                                  BUS   On time
```

### Departures board at Reading Station (RDG)


```r
rdg_dep <- trainR::GetDepBoardRequest("RDG")
print(rdg_dep)
```

```
## Reading (RDG) Station Board on 2021-05-01 06:16:15
## Time   To                                      Plat  Expected
## 07:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 07:20  Great Malvern                           9B    On time
## 07:20  Redhill                                 5     07:33
## 07:22  Ealing Broadway                         14    On time
## 07:41  London Paddington                       10    On time
## 07:42  London Waterloo                         4     On time
## 07:47  London Paddington                       11    On time
## 07:52  Basingstoke                             2     On time
## 07:52  Ealing Broadway                         14    On time
## 07:53  Didcot Parkway                          12B   On time
## 07:55  Bristol Temple Meads                    8     On time
## 07:56  London Paddington                       10    On time
## 08:01  Gatwick Airport                         14A   On time
##        via Guildford                           
## 08:08  Penzance                                8     On time
## 08:12  London Waterloo                         5     On time
## 08:13  Swansea                                 9     On time
## 08:15  Ealing Broadway                         15A   On time
## 08:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 08:20  Great Malvern                           9B    On time
## 08:22  Ealing Broadway                         14    On time
## 08:36  Redhill                                 14A   On time
## 08:42  London Waterloo                         4     On time
## 08:43  London Paddington                       11    On time
## 08:48  London Paddington                       10    On time
## 08:49  Bournemouth                             8     On time
## 08:52  Basingstoke                             2     On time
## 08:52  Ealing Broadway                         14    On time
## 08:53  Didcot Parkway                          12B   On time
## 08:55  Weston-super-Mare                       9     On time
## 08:57  London Paddington                       10    On time
## 09:01  Gatwick Airport                         4     On time
##        via Guildford                           
## 09:08  Plymouth                                9     On time
## 09:12  London Waterloo                         6     On time
## 09:13  Swansea                                 8     On time
## 09:15  Ealing Broadway                         15A   On time
## 09:15  Manchester Piccadilly                   13    On time
##        via Coventry & Stoke-on-Trent           
## 07:34  Bedwyn                                  BUS   On time
## 08:10  Newbury                                 BUS   On time
## 08:34  Bedwyn                                  BUS   On time
## 08:36  Newbury                                 BUS   On time
## 09:10  Newbury                                 BUS   On time
```
