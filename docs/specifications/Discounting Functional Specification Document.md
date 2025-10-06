# Functional Specification Document

## Document Information
- **Project Name:** CASE Temporary Promotion Configurations
- **Document Version:** 1.0
- **Date:** [2025-10-03]
- **Prepared By:** Sarah Richey


## Table of Contents
1. Introduction
2. Project Overview
3. Scope
4. User Stories/Use Cases
      - UseCase 1 BASE
      - UseCase 2 BIDGRID_1
      - UseCase 3 BIDGRID_2
      - UseCase 4 BIDGRID_3
      - UseCase 5 EDU
      - UseCase 6 TEMP_PROMO

### 1. Introduction
### 1.1 Purpose
This document is a configuration guide for managing the Assisted stacking with discounts

### 1.2 Document Conventions
Automatic Discounts in CASE Phase 1: 
    - BASE
    - BidGrid tier 1, tier 2, tier 3
    - EDU
    - Temp Promo

Manually  applied
     -Deal Registraiton
     -Special Pricing
     -Essential Bundle
     -Coop
     -Closed Audience

## 3. Scope 
Part 1: Documenting the current automated pricing rules that impact CASE and how to configure them.

Part 2: Defining how to configure the new temporary promotion for Deal Registration.

### 3.1 In Scope
Review existing configurations that do not change, then out line the proposed documentation that is for Deal Registration.


## 4. PRICING RULE CONFIGURATIONS FOR CASE
The BASE discount pricing rule is the "driver" for how all other discount pricing rules with the same product ID and Sku ID to calculate in Castles Best price Mprice API.

Each Price Rule is configured to follow the Business stacking rules outlined in the BRD document.

Rules of Stacking with Discounts in Assisted (CASE) 
![Rules of Stacking with Discounts](../images/stacking_rules.png) 
### 4.1 User Story/Use Case 1  - BASE
- **Title:** [Scenario 1: BASE discount]
- **Example CPM Price Rule:** [690bdfe7-c451-44bb-8ddf-c9627ea91b6e](https://yourportal.example.com/pricing-rules/690bdfe7-c451-44bb-8ddf-c9627ea91b6e)

- **Example CASE Quote in PPE** QSGL00218001 - SingaporeCust9
- **Description:** Base discount on sku.
Stacks with:
    BidGrid 1
    BidGrid 2
    EDU
    Temp Promo

- **Configuration:**
  1. Base Discount Pricing Rule Configuration in CPM.
  2. **GENERAL TAB**
     | Field             | Value                |
     |-------------------|----------------------|
     | End Date          | in the future        |
     | Name              | Base 7% Discount     |
     | Description       | [Description text]   |
     | Explanation Code  | Base_Discount        |
     | Type              | Base                 |
     
  3. **CONDITIONS TAB**
     | Field                    | Value                       |
     |--------------------------|----------------------------- |
     | Storefront Condition              | SMB and VSB                    |
     | Market Conition                   | [AT, BE, CH, DE, DK, FI, FR, ES, IE, IT, JP, LU]            |
     
  4. **TARGET**
     | Field                | Value                   |
     |----------------------|-------------------------|
     | Target Type         | Product Target    |
     | Product ID           | 8MZBMMCJZPJQ             |
     | SKU ID               | A2WQ                |
     | Display Order        | [Display Order Number]  |
     
  5. **OPERATIONS**
     | Field                | Value                   |
     |----------------------|-------------------------|
     |Calculation Type       | Percentage Off             |                      |
     
  6. **COMBINATION CLASSES**
     | Class Name | Rank       |                       | |
     |--------------|----------------------|----------------------------------|---------------|
     | BIDGRIDONE    |   999                      |     
     | BIDGRIDTWO     | 999   |
     | BIDGRIDTHREE   | 999 |
     | EDU     | 999        |
     | PROMO | 999|

### 4.2 User Story/Use Case 2 - BidGrid 1
- **Title:** Scenario 2: BidGrid Tier 1 discount

- **Description:** BidGrid Tier 1 discount stacks with Base discount.
Does NOT stack with BidGrid 2 or 3, EDU or Temp Promo.
- **Example Price Rule ** https://castleui.production.store-web.dynamics.com/authoring/PriceRule/dd737100-9209-49b6-85e8-74c61ddca9ad

- **Example CASE Quote ** In PPE QSGL00218001 - SingaporeCust9 
- **Configuration:**
  1. BidGrid Tier 1 Discount Pricing Rule Configuration
  2. **GENERAL TAB**
     | Field             | Value                   |
     |-------------------|-------------------------|
     | End Date          | in the future           |
     | Name              | BidGrid Tier 1 Discount |
     | Description       | [Description text]      |
     | Explanation Code  | BidGrid_Tier1         |
     | Type              | BidGrid1               |
     
  3. **CONDITIONS TAB**
     | Field                    | Value                       |
     |--------------------------|----------------------------- |
     | Storefront Condition     | SMB and VSB                 |
     | Market Conition          | [AT, BE, CH, DE, DK, FI, FR, ES, IE, IT, JP, LU] |
     | Quantity Condition       |  6-49
      units                  |
     
  4. **TARGET**
     | Field                | Value                   |
     |----------------------|-------------------------|
     | Target Type          | Product Target          |
     | Product ID           | 8MZBMMCJZPJQ            |
     | SKU ID               | A2WQ                    |
     | Display Order        | [Display Order Number]  |
     
  5. **OPERATIONS**
     | Field                | Value                   |
     |----------------------|-------------------------|
     |Calculation Type      | Percentage Off          |
     
  6. **COMBINATION CLASSES**
     | Class Name    | Rank  |                |                |
     |---------------|-------|----------------|----------------|
     | BIDGRIDONE    | 100   |                |                |
     | 

### 4.3 User Story/Use Case BidGrid Tier 2
- **Title:** Scenario 3: BidGrid Tier 2 discount

- **Description:** BidGrid Tier 2 discount stacks with Base
Does NOT stack with BidGrid 1 or 3, EDU or  TEMP PROMO
- **Configuration:**
  1. BidGrid Tier 2 Discount Pricing Rule Configuration
  2. **GENERAL TAB**
     | Field             | Value                   |
     |-------------------|-------------------------|
     | End Date          | in the future           |
     | Name              | BidGrid Tier 2 Discount |
     | Description       | [Description text]      |
     | Explanation Code  | BidGrid_Tier2         |
     | Type              | BidGrid2               |
     
  3. **CONDITIONS TAB**
     | Field                    | Value                       |
     |--------------------------|----------------------------- |
     | Storefront Condition     | SMB and VSB                 |
     | Market Conition          | [AT, BE, CH, DE, DK, FI, FR, ES, IE, IT, JP, LU] |
     | Quantity Condition       | 50-249 units                 |
     
  4. **TARGET**
     | Field                | Value                   |
     |----------------------|-------------------------|
     | Target Type          | Product Target          |
     | Product ID           | 8MZBMMCJZPJQ            |
     | SKU ID               | A2WQ                    |
     | Display Order        | [Display Order Number]  |
     
  5. **OPERATIONS**
     | Field                | Value                   |
     |----------------------|-------------------------|
     |Calculation Type      | Percentage Off          |
     
  6. **COMBINATION CLASSES**
     | Class Name    | Rank  |                |                |
     |---------------|-------|----------------|----------------|
     | BIDGRIDTWO| 100   |  
### 4.4 User Story/Use Case 4 - BidGrid Tier 3
- **Title:** Scenario 4: BidGrid Tier 3 discount pricing rule

- **Description:** BidGrid Tier 3 discount stacks with Base.
Does NOT stack with BidGrid1, BidGrid2, EDU or TEMP PROMO

- **Configuration:**
  1. BidGrid Tier 3 Discount Pricing Rule ConfiguratioN
  2. **GENERAL TAB**
     | Field             | Value                   |
     |-------------------|-------------------------|
     | End Date          | in the future           |
     | Name              | BidGrid Tier 3 Discount |
     | Description       | [Description text]      |
     | Explanation Code  | BidGrid_Tier3         |
     | Type              | BidGrid3               |
     
  3. **CONDITIONS TAB**
     | Field                    | Value                       |
     |--------------------------|----------------------------- |
     | Storefront Condition     | SMB and VSB                 |
     | Market Conition          | [AT, BE, CH, DE, DK, FI, FR, ES, IE, IT, JP, LU] |
     | Quantity Condition       | 250 - 999999+ units                   |
     
  4. **TARGET**
     | Field                | Value                   |
     |----------------------|-------------------------|
     | Target Type          | Product Target          |
     | Product ID           | 8MZBMMCJZPJQ            |
     | SKU ID               | A2WQ                    |
     | Display Order        | [Display Order Number]  |
     
  5. **OPERATIONS**
     | Field                | Value                   |
     |----------------------|-------------------------|
     |Calculation Type      | Percentage Off          |
     
  6. **COMBINATION CLASSES**
     | Class Name    | Rank  |                |                |
     |---------------|-------|----------------|----------------|
     | BIDGRIDTHREE  |        100     |                |
     
### 4.5 User Story/Use Case 5 - EDU
- **Title:** Scenario 5: EDU discount

- **Description:** EDU discount stacked with Base discount, doe not stack with BIDGRIDS or Temp Promo

- **Configuration:**
  1. EDU Discount Pricing Rule Configuration
  2. **GENERAL TAB**
     | Field             | Value                |
     |-------------------|----------------------|
     | End Date          | in the future        |
     | Name              | EDU 10% Discount     |
     | Description       | [Description text]   |
     | Explanation Code  | EDU_Discount         |
     | Type              | EDU                  |
     
  3. **CONDITIONS TAB**
     | Field                    | Value                       |
     |--------------------------|----------------------------- |
     | Storefront Condition     | SMB and VSB                 |
     | Market Conition          | [AT, BE, CH, DE, DK, FI, FR, ES, IE, IT, JP, LU] |
    
     
  4. **TARGET**
     | Field                | Value                   |
     |----------------------|-------------------------|
     | Target Type          | Product Target          |
     | Product ID           | 8MZBMMCJZPJQ            |
     | SKU ID               | A2WQ                    |
     | Display Order        | [Display Order Number]  |
     
  5. **OPERATIONS**
     | Field                | Value                   |
     |----------------------|-------------------------|
     |Calculation Type      | Percentage Off          |
     
  6. **COMBINATION CLASSES**
     | Class Name    | Rank  |                |                |
     |---------------|-------|----------------|----------------|
      |                |
     | EDU     | 100        |
     

### 4.6 User Story/Use Case 6 Temporary Promotion
- **Title:** Scenario 6: TEMP PROMO discount

- **Description:** TEMP PROMO discount Only stacks with Base discount in CASE Phase 1.

Does NOT stack with BidgGrids or EDU discounts.

- **Configuration:**
  1. TEMP PROMO Discount Pricing Rule Configuration
  2. **GENERAL TAB**
     | Field             | Value                |
     |-------------------|----------------------|
     | End Date          | in the future        |
     | Name              | TEMP PROMO 15% Discount     |
     | Description       | [Description text]   |
     | Explanation Code  | Temp_Promo         |
     | Type              | PROMO                  |
     
  3. **CONDITIONS TAB**
     | Field                    | Value                       |
     |--------------------------|----------------------------- |
     | Storefront Condition     | SMB and VSB                 |
     | Market Conition          | [AT, BE, CH, DE, DK, FI, FR, ES, IE, IT, JP, LU] |
    
     
  4. **TARGET**
     | Field                | Value                   |
     |----------------------|-------------------------|
     | Target Type          | Product Target          |
     | Product ID           | 8MZBMMCJZPJQ            |
     | SKU ID               | A2WQ                    |
     | Display Order        | [Display Order Number]  |
     
  5. **OPERATIONS**
     | Field                | Value                   |
     |----------------------|-------------------------|
     |Calculation Type      | Percentage Off          |
     
  6. **COMBINATION CLASSES**
     | Class Name    | Rank  |                |                |
     |---------------|-------|----------------|----------------|
     | PROMO    | 100


 Part II: TBD for Phase 2, DEAL REG Promo's that do not stack with BASE discount.

 What else is the stacking eligibility for Deal Reg Promo?
