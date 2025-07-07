# Validate Types Prompts

## 1. Type Consistency Check

/\*\*

-   Validate this implementation against anchor/project-anchor.md:
-
-   Check:
-   1. ✓ All interfaces are implemented correctly
-   2. ✓ Method signatures match exactly
-   3. ✓ Return types are correct
-   4. ✓ Parameter types are correct
-   5. ✓ No missing methods
-   6. ✓ No extra methods not in interface
-
-   Report any mismatches with fixes
    \*/

## 2. Find Type Drift

/\*\*

-   Compare current implementation with anchor types:
-
-   Look for:
-   1. Properties added but not in anchor
-   2. Properties in anchor but missing here
-   3. Type mismatches (string vs number)
-   4. Optional vs required mismatches
-   5. Method signature changes
-
-   Suggest anchor updates or code fixes
    \*/

## 3. Missing Types Check

/\*\*

-   Identify types that should be in anchor:
-
-   Find:
-   1. Inline types that should be extracted
-   2. Repeated type definitions
-   3. Types used but not defined
-   4. DTOs without interfaces
-   5. Error types not in anchor
-
-   Generate missing type definitions
    \*/

## 4. Import Validation

/\*\*

-   Check all imports reference anchor:
-
-   Requirements:
-   -   Types imported from anchor/project-anchor.md
-   -   No duplicate type definitions
-   -   No relative imports for types
-   -   Consistent import style
-
-   Fix any incorrect imports
    \*/
