# Stock App

> A simple application where you could sell and buy stocks and save them, and load them back from stored DB


## Database
> For back-end, I have used google Firebase which store stocks with their price and value. 

- **Note:** 
> Only one record can be stored in the Firebase database for this application. A second attempt to save will replace the existing record.

## Tasks
- **Methods:** 
>Located in "components/Header.Vue", "components/stocks/Stock.vue" files etc.

- **Computed Property:** 
>Located in "components/Home.Vue", "components/stocks/Stocks.vue" files etc.

- **2 way binding:** 
>An example in "components/stocks/Stock.vue".

## Build Setup

``` bash
# Install dependencies
npm install

# Serve with hot reload at localhost:8080
npm run dev

# Build for production
npm run build


