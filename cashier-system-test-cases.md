# Cashier System Test Cases

This outlines a comprehensive set of test cases for a cashier system. These test cases are intended to ensure the system correctly calculates prices, applies appropriate discounts, and handles various scenarios including individual product purchases, combinations, and edge cases.

## 💭 Assumptions
While making these test cases, the following assumptions were made:

1. **There are three products:** Green Tea, Strawberries, and Coffee.
2. **There are three types of rules:** Free, Reduced Price, and Fraction Price. Rules are defined in the table below.

## 🚀 Test Structure
The test cases are structured to cover boundary conditions and use equivalence partitioning. This approach ensures we validate that:

1. The expected rule is applied correctly for each scenario.
2. The total price calculation is accurate.

I've organized the tests in tables because they're easier to read and compare. Each table covers a specific product or scenario, with columns for the test case ID, items added, original price, rule applied, and expected price. This format makes it simple to:

1. Quickly scan different scenarios.
2. Understand the logic behind each test case.
3. Verify that all discount rules are tested.
4. Ensure we're covering edge cases and combinations.

By structuring the tests this way, we can efficiently cover a wide range of scenarios without redundancy, giving us confidence in the system's accuracy and reliability.

## Products
| Product Code | Name         | Price  |
|--------------|--------------|--------|
| GR1          | Green Tea    | £3.11  |
| SR1          | Strawberries | £5.00  |
| CF1          | Coffee       | £11.23 |

## Discount Rules
| Rule Type        | Target Product | Minimum Quantity | Discount Details                          |
|------------------|----------------|------------------|-------------------------------------------|
| **Free**         | GR1            | 1                | Buy 1, Get 1 Free                         |
| **Free**         | CF1            | 1                | Buy 1, Get 1 Free                         |
| **Reduced Price**| GR1            | 5                | Pay £2.90 each                            |
| **Reduced Price**| GR1            | 8                | Pay £2.75 each                            |
| **Reduced Price**| SR1            | 3                | Pay £4.50 each                            |
| **Reduced Price**| CF1            | 5                | Pay £10.00 each                           |
| **Fraction Price**| GR1           | 10               | Pay 75% of the original price (£2.33 each)|
| **Fraction Price**| SR1           | 6                | Pay 85% of the original price (£4.25 each)|
| **Fraction Price**| SR1           | 10               | Pay 80% of the original price (£4.00 each)|
| **Fraction Price**| CF1           | 8                | Pay 66.6% of the original price (£7.49 each)|

## Test Cases 

### Instructions 
For each test cases:
1. Add the specified quantity of the product to the cart. 
2. Calculate the total price. 
3. Apply the relevant discount rule, if any. 
4. Verify that the final price matches the expected price. 

#### **Green Tea (GR1)**

Given that a customer added ${Items Added} of product GR1 in their cart:
- The ${Rule Applied} should be applied.
- The customer should pay ${Expected Price}.

| Test Case | Items Added | Original Price | Rule Applied                   | Expected Price |
|-----------|-------------|----------------|--------------------------------|----------------|
| GR1.1     | 1           | £3.11          | No discount                    | £3.11          |
| GR1.2     | 2           | £6.22          | Free (Buy 1, Get 1 Free)       | £3.11          |
| GR1.3     | 3           | £12.44         | Free (Buy 1, Get 1 Free) + No discount       | £6.22          |
| GR1.4     | 5           | £15.55         | Reduced Price (Pay £2.90 each) | £14.50         |
| GR1.5     | 7           | £21.77         | Reduced Price (Pay £2.90 each) | £20.30         |
| GR1.6     | 8           | £24.88         | Reduced Price (Pay £2.75 each) | £22.00         |
| GR1.7     | 10          | £31.10         | Fraction Price (75% of £3.11)  | £23.30         |
| GR1.8     | 15          | £46.65         | Fraction Price (75% of £3.11)  | £34.95         |

#### **Strawberries (SR1)**

Given that a customer added ${Items Added} of product SR1 in their cart:
- The ${Rule Applied} should be applied.
- The customer should pay ${Expected Price}.

| Test Case | Items Added | Original Price | Rule Applied                   | Expected Price |
|-----------|-------------|----------------|--------------------------------|----------------|
| SR1.1     | 1           | £5.00          | No discount                    | £5.00          |
| SR1.2     | 2           | £10.00         | No discount                    | £10.00         |
| SR1.3     | 3           | £15.00         | Reduced Price (Pay £4.50 each) | £13.50         |
| SR1.4     | 5           | £25.00         | Reduced Price (Pay £4.50 each) | £22.50         |
| SR1.5     | 6           | £30.00         | Fraction Price (85% of £5.00)  | £25.50         |
| SR1.6     | 9           | £45.00         | Fraction Price (85% of £5.00)  | £38.25         |
| SR1.7     | 10          | £50.00         | Fraction Price (80% of £5.00)  | £40.00         |
| SR1.8     | 12          | £60.00         | Fraction Price (80% of £5.00)  | £48.00         |

#### **Coffee (CF1)**

Given that a customer added ${Items Added} of product CF1 in their cart:
- The ${Rule Applied} should be applied.
- The customer should pay ${Expected Price}.

| Test Case | Items Added | Original Price | Rule Applied                    | Expected Price |
|-----------|-------------|----------------|---------------------------------|----------------|
| CF1.1     | 1           | £11.23         | No discount                     | £11.23         |
| CF1.2     | 2           | £22.46         | Free (Buy 1, Get 1 Free)        | £11.23         |
| CF1.3     | 3           | £33.69         | Free (Buy 1, Get 1 Free)        | £22.46         |
| CF1.4     | 4           | £44.92         | Free (Buy 1, Get 1 Free)        | £22.46         |
| CF1.5     | 5           | £56.15         | Reduced Price (Pay £10.00 each) | £50.00         |
| CF1.6     | 7           | £78.61         | Reduced Price (Pay £10.00 each) | £70.00         |
| CF1.7     | 8           | £89.84         | Fraction Price (66.6% of £11.23)| £59.92         |
| CF1.8     | 10          | £112.30        | Fraction Price (66.6% of £11.23)| £74.90         |

#### **Combination of Products**

Given that a customer has the following items in their cart:
- ${Items Added}

Then:
- The ${Rule Applied} should be applied.
- The customer should pay ${Expected Price}.

| Test Case | Items Added           | Original Price | Expected Price | Notes                                    |
|-----------|-----------------------|----------------|----------------|------------------------------------------|
| COMB.1    | 2 GR1, 3 SR1, 2 CF1   | 2*(3.11) + 3*(5.0) + 2*(11.23) = £43.68         | 3.11 + 3*(4.5) + 11.23 = £27.84         | GR1: Buy 1 Get 1 Free, SR1: £4.50 each, CF1: Buy 1 Get 1 Free |
| COMB.2    | 5 GR1, 6 SR1, 5 CF1   | 5*(3.11) + 6*(5.0) + 5*(11.23) = £101.7        | 5*(2.9) + 6*(4.25) + 5*(10.0) = £90.00         | GR1: £2.90 each, SR1: £4.25 each, CF1: £10.00 each |
| COMB.3    | 10 GR1, 10 SR1, 8 CF1 | 10*(3.11) + 10*(5.0) + 8*(11.23) = £170.94       | 10*(2.33) + 10*(4.0) + 8*(7.49) = £123.22        | GR1: £2.33 each, SR1: £4.00 each, CF1: £7.49 each |

#### **Edge Cases**

Given the following scenarios:
- Added {Items Added}

Then:
- The system should handle the case as described in the Notes.
- The customer should pay {Expected Price}.

| Test Case | Items Added               | Original Price | Expected Price | Notes                                    |
|-----------|---------------------------|----------------|----------------|------------------------------------------|
| EDGE.1    | 0 GR1, 0 SR1, 0 CF1       | £0.00          | £0.00          | Empty basket                             |
| EDGE.2    | 100 GR1                   | £311.00        | £233.00        | Large quantity, fraction price applies   |
| EDGE.3    | 1 GR1, 1 SR1, 1 CF1       | £19.34         | £19.34         | One of each, no discounts                |