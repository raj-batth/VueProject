# Stock App

> A simple application where you could sell and buy stocks and save them, and load them back from stored DB
> - **Application Description:** 
> > Home page displays Available funds.\
> > "Portfolio" link displays all the stocks that have been bought and are available to Sell.\
> > "Stocks" link displays everything available for Buying.\
> > "Save" updates the record into the firebase.\
> > "Load" Loads the application with the current values stored in the firebase.

## Database
> For back-end, I have used google firebase which store stocks with their price and value. 

- **Note:** 
> Only one record can be stored in the firebase database for this application. A second attempt to save will replace the existing record.

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



