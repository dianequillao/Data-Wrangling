attach(refine_original)
library(tidyr)
library(dplyr)
library(dummies)
library(readr)

# clean company names
refine_original$company <- tolower(refine_original$company)
show(refine_original)

refine_original$company <- sub("phillips", "philips",refine_original$company)
refine_original$company <- sub("phllips", "philips",refine_original$company)
refine_original$company <- sub("phillps", "philips",refine_original$company)
refine_original$company <- sub("fillips", "philips",refine_original$company)
refine_original$company <- sub("phlips", "philips",refine_original$company)
refine_original$company <- sub("ak zo", "azko",refine_original$company)
refine_original$company <- sub("akz0", "azko",refine_original$company)
refine_original$company <- sub("unilver", "unilever",refine_original$company)

# separate product code and number column
refine_original <- separate(refine_original, 'Product code / number', c("product_code", "product_number"), sep ="-")

# create column for product categories
refine_original$category <- refine_original$product_code
refine_original$category <- sub("p", "Smartphone",refine_original$category)
refine_original$category <- sub("v", "TV",refine_original$category)
refine_original$category <- sub("x", "Laptop",refine_original$category)
refine_original$category <- sub("q", "Tablet",refine_original$category)

# combine address, city, and country columns
refine_original <- unite(refine_original, "full_address", c(address, city, country), sep = " , ")

# create dummy variables for company and product category
refine_original$company_philips <- ifelse(refine_original$company=='philips', 1, 0)
refine_original$company_azko <- ifelse(refine_original$company=="unilever", 0, 
                                      ifelse(refine_original$company=='philips', 0,
                                             ifelse(refine_original$company=='van houten', 0, 1)))
                                                   
                                        
refine_original$company_unilever <- ifelse(refine_original$company=='unilever', 1, 0)
refine_original$company_van_houten <- ifelse(refine_original$company=='van houten', 1, 0)

refine_original$product_smartphone <- ifelse(refine_original$product_code=='p', 1, 0)
refine_original$product_tv <- ifelse(refine_original$product_code=='v', 1, 0)
refine_original$product_laptop <- ifelse(refine_original$product_code=='x', 1, 0)
refine_original$product_tablet <- ifelse(refine_original$product_code=='q', 1, 0)

# save new data as refine_clean.csv
write.csv(refine_original, file = "refine_clean.csv")
