# Background
This is a short coding assignment that involves setting up a simple REST service that perform basic CRUD operations on 
stock positions in hypothetical trading portfolio(s)

Clients of the REST API should be able to create new stock portfolios and add
stock investments (called positions) into these portfolios

As a bonus, provide a API endpoint that shows the total value of stock positions in a given portfolio

*note* the data model is such that a `Portfolio` contains 0, 1 or multiple `Stock` positions. A stock position have a `ticker` (the identifier),
and a `market value` (how much in US dollar does one own of the stock)

In other words - the core data model is such that:
```java
class Portfolio {
    String portfolioName;
    List<Stock> positions;
}

class Stock {
    String ticker;
    double marketValue;
}
```

# Requirements
## REST API

### Portfolio(s) 
 - `/GET /api/v1/portfolios` lists all portfolios on the system by name
 - `/PUT /api/v1/portfolios/{portfolioName}` creates a new portfolio
 - `/GET /api/v1/portfolios/{portfolioName}` list the stocks owned in a single portfolio
 - `/DELETE /api/v1/portfolios/{portfolioName}` delete a portfolio
 
### Positions(s)
 - `/PUT /api/v1/portfolios/{portfolioName}/{ticker}?marketValue={marketValue}` creates a new position
 - `/POST /api/v1/portfolios/{portfolioName}/{ticker}?marketValue={marketValue}` updates an existing
 - `/DELETE /api/v1/portfolios/{portfolioName}/{ticker}` removes a position
 
 ```javascript
// /PUT /api/v1/portfolios/my-portfolio-1
// ... 
// /GET /api/v1/portfolios/my-portfolio-1
 
[
  {
    "ticker": "AAPL",
    "marketValue": 100
  },
  {
    "ticker": "TLSA",
    "marketValue": 500
  }
]
```

## Bonus Question
Create a route that aggregates the market value of all positions in a given portfolio
 - `/GET /api/v1/portfolios/{portfolioName}/net-asset-value`
 
For example, if a portfolio contains two stock positions: $100 of AAPL and $200 of GOOG, then the net asset value is $300

## Project Setup / Runtime Requirement
The entire project should be simply runnable with a single maven or gradle command upon `git clone`

# Submission
Create a private repository with the completed assignment. Reply to earlier email communication chain with the link.

# Preferred Tools
 - Spring Boot is highly preferred, but you may also use `Dropwizard` a similar J2EE framework
 - Recommended IDE: Use Intellij IDEA
 - Database: we recommend using an in-memory database like h2

