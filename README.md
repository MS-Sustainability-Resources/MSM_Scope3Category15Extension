
# Adding new categories to the Scope 3 - Category 15 (Investments)
This repo provides guidance on adding additional Investment categories to the Scope 3 - Category 15 (Investments). The Investments category is based on the Partnership for Carbon Accounting Financials (PCAF) methodology. It is an industry-led initiative enabling financial institutions to measure and disclose GHG emissions for loans and investments. For more details on Category 15: Investments, please refer to the [public documentation] https://learn.microsoft.com/en-us/industry/sustainability/calculate-scope3#category-15-investments 


# What is Scope 3- Category 15
Category 15 (Investments) includes scope 3 emissions associated with the reporting company's investments in the reporting year, not already included in scope 1 and scope 2. This category is applicable to investors (i.e. companies that make an investment with the objective of making a profit) and companies that provide financial services. This category also applies to investors that are not profit driven (e.g. multilateral development banks), and the same calculation methods should be used. Investments are categorized as downastream scope 3 category because providing capital or financing is a service provided by the reporting company.

To know more about this category, please refer to [Technical Guidance for calculating Scope 3 Emissions] (https://ghgprotocol.org/sites/default/files/standards/)Scope3_Calculation_Guidance_0.pdf 

# Why are we doing this?
Microsoft Sustainability Manager (MSM) does not provide an Out of the box configuration experiences in editing the SDDs (sustainability data definitions) as they are pretty much locked down for customizations. However, we have heard few customer asks on extensbility needs for select categories such as Investments. Hence, we are providing , via this document, a supportable way of extending the Scope 3-Category 15 (Investment) to add additional categories. Please be noted, that this guidance extends to Category 15 Only.


# Business Case
Out of the box, Sustainability Manager provides 7 pre-defined categories for Scope 3 -Category 15 as below. While these are useful, many organizations report their investiment activities beyond the pre-defined categories and hence have a need to be able to add new categories as per their business needs.

Business loans and unlisted equity
Commercial real estate
Listed equiity and corporate bonds
Mortgages
Motor vehicle loans
Project finance
Soverign bonds



# Business Scenario

Contoso corp is implementing Microsoft Sustainability Manager (MSM) to report Scope 1, Scope 2 and Scope 3 emissions. Their need for Scope 3 category 15 (Investments) require more listed categories beyond what is available Out of the box. To accurately represent the non-listed categories, Contoso corp wishes to have a 'Generic' category under Category 15 (investments) to report the non-listed cateogires.


# Solution outcome

By adding the 'Generic' category to the Category 15 (Investments), customer would now be able to categorize the Investment activities under 'Generic' to calculate the emissions.

Once the solution is setup, the 'Generic (Activities)' would look like below in the Sustainability Manager: 

![Generic Activities listing](image.png)

The calculation model would reflect the new category for 'Category 15 (Investments)' as below

![Generic Activities in Calculation Model](image-1.png)

The view for the Activities would appear like this when clicked from 'Carbon Activities'
![Investments - Generic Activities view](image-4.png)

Finally, the out of the box dashboard (Emissions Insights) show up the generic category 

![Generic Category in Emissions insights dashboard](image-3.png)

# Design Approach
To add a new category  ('Generic Activities' ) under Category 15 (Investments), we need to follow the below approach.

1. Add a new choice to PCAF asset class type global option set to represent the new activity category
2. Add two custom views under 'Investment' and 'Emissions' tables with a filter to select the new PCAF asset category created above. These views are helpful to filter the Activities and Emissions by the new PCAF category created above
3. Create two new SDD (Sustainability data definition) records in 'Sustainability Data Defintion' table to represent the Activity and Emission associated to the new PCAF category
4. Create two new records in 'Sustainability Data Definition Setting' table for Activity and Emission SDD types associated to the new PCAF category
5. Create business rule to default the 'Sustainability Data Definition' when the new PCAF category is selected from the Form
6. Migrate the above configurations to upper environments using the standard ALM practices
