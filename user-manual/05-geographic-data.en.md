# Geographic Data Management

The geographic data management features in Gobify help you maintain accurate street and neighborhood (colonia) information, which is essential for citizen addresses and program beneficiary tracking.

## Why Geographic Data Matters

Accurate geographic data ensures:
- **Precise citizen addresses** for program delivery and field visits
- **Correct mapping** of beneficiaries on program maps
- **Standardized location data** across the system
- **Easy search and filtering** by neighborhood
- **Consistent postal codes** and administrative divisions

## Accessing Geographic Data

Geographic data management is split into two sections:

1. **Calles (Streets)** - Click the **Calles** tab in main navigation
2. **Colonias (Neighborhoods)** - Click the **Colonias** tab in main navigation

---

## Managing Streets (Calles)

The Calles section allows you to view, search, add, and edit street information.

### Streets List View

[Screenshot: Streets table showing street names, types, and edit buttons]

When you open the Calles section, you'll see a paginated list of all streets in the system.

**Table Columns:**

| Column | Description | Example |
|--------|-------------|---------|
| **Nombre** | Street name | Juárez |
| **Tipo** | Street type label | Calle |
| **Nombre Completo** | Full street designation | Calle Juárez |
| **Acciones** | Action buttons | Edit, Delete |

**Street Type Labels:**

Streets are categorized by type, each with a distinct visual label:

- **Calle** (Street) - Most common, standard streets
- **Avenida** (Avenue) - Major thoroughfares
- **Boulevard** (Boulevard) - Wide, important roads
- **Privada** (Private street) - Gated or restricted access
- **Cerrada** (Closed street) - Dead-end streets
- **Callejón** (Alley) - Narrow passages
- **Camino** (Road) - Less urban routes
- **Andador** (Walkway) - Pedestrian paths

[Screenshot: Street type labels with different colors]

Each type has a colored badge for quick visual identification.

### Searching Streets

Use the search functionality to quickly find specific streets.

[Screenshot: Search bar with example "Juarez"]

**Search Methods:**

#### By Name
```
Search: Juarez
Results: All streets containing "Juarez"
- Calle Juárez
- Avenida Benito Juárez
- Privada Juárez Norte
```

#### By Type
```
Search: Avenida
Results: All streets typed as "Avenida"
- Avenida Revolución
- Avenida Hidalgo
- Avenida del Mar
```

#### Partial Search
```
Search: Hid
Results: Streets matching partial name
- Calle Hidalgo
- Boulevard Miguel Hidalgo
```

**Search Features:**
- Real-time results as you type
- Case-insensitive
- Searches both name and type
- Highlights matching terms

### Pagination

Streets are displayed 25 per page for easy navigation.

[Screenshot: Pagination controls showing page 1 of 48]

**Pagination Controls:**

- **Page Info**: "Showing 1-25 of 1,200 streets"
- **First Page**: |◄ button
- **Previous**: ◄ button
- **Page Numbers**: 1, 2, 3... (click to jump)
- **Next**: ► button
- **Last Page**: ►| button

**Rows Per Page:**
1. Click "Rows per page" dropdown
2. Select: 10, 25, 50, or 100
3. Table reloads with new page size

**Navigation Tips:**
- Use search to reduce results instead of paging through thousands
- Jump to specific page number for known ranges
- Increase rows per page for bulk editing sessions

### Adding a New Street

When a street doesn't exist in the system, you can add it.

[Screenshot: "Add New Street" button and form]

**How to Add a Street:**

```
1. Click "Add New Street" button (top-right)
2. Add Street form appears
3. Fill in required fields:
   - Street name (required)
   - Street type (required)
4. Fill optional fields:
   - Alternate names
   - Notes
5. Click "Save"
6. New street appears in list immediately
7. Available for use in citizen addresses
```

**Add Street Form Fields:**

**Street Name** (required)
- Enter the base name without type designation
- Example: Enter "Juárez" not "Calle Juárez"
- Use proper capitalization
- Avoid abbreviations

**Street Type** (required)
- Select from dropdown:
  - Calle
  - Avenida
  - Boulevard
  - Privada
  - Cerrada
  - Callejón
  - Camino
  - Andador
  - Otro (Other)

**Alternate Names** (optional)
- Common variations of the street name
- Former names
- Local nicknames
- Example: "Benito Juárez" for "Juárez"

**Notes** (optional)
- Additional information
- Landmarks on the street
- Special characteristics
- Example: "Main commercial street in Centro"

**Validation Rules:**
- Street name cannot be empty
- Must select a street type
- System checks for duplicates (warns if similar name exists)
- Maximum 200 characters for name

**Example Entry:**
```
Name: Revolución
Type: Avenida
Alternate Names: Av. Revolución, Revolución Norte
Notes: Runs north-south through Centro and Zona Romántica
```

**After Adding:**
- Street immediately available in address dropdowns
- Appears in street search results
- Can be edited if needed
- Available for all users

### Editing Existing Streets

Correct errors or update street information inline.

[Screenshot: Edit button and inline editing fields]

**How to Edit:**

```
1. Locate street in list (use search if needed)
2. Click "Edit" button (pencil icon)
3. Fields become editable inline
4. Make changes:
   - Update name
   - Change type
   - Modify notes
5. Click "Save" (checkmark icon)
6. Or click "Cancel" (X icon) to discard
7. Changes save immediately
8. Updated info displays
```

**Inline Editing:**

The editing happens directly in the table row:

**Before Editing:**
```
Juárez | Calle | Calle Juárez | [Edit] [Delete]
```

**During Editing:**
```
[Juarez___] [▼Calle] [Save ✓] [Cancel ✗]
```

**After Saving:**
```
Benito Juárez | Avenida | Avenida Benito Juárez | [Edit] [Delete]
```

**What You Can Edit:**
- Street name
- Street type
- Alternate names
- Notes

**What You Cannot Edit:**
- Street ID (internal system reference)
- Creation date
- Number of addresses using this street (view-only)

**Editing Best Practices:**
1. Verify change is necessary
2. Check for typos before saving
3. Ensure type accurately describes the street
4. Update alternate names if changing main name
5. Document reason in notes if major change

**Common Edits:**
- Fixing spelling errors
- Updating official street names
- Changing type designation (e.g., Calle → Avenida)
- Adding missing alternate names
- Standardizing capitalization

### Deleting Streets

Remove streets that are duplicates or entered in error.

**How to Delete:**

```
1. Locate street to delete
2. Click "Delete" button (trash icon)
3. Confirmation dialog appears:
   "Are you sure you want to delete this street?"
   "This action cannot be undone."
4. Verify street name is correct
5. Click "Confirm Delete"
6. Street removed from list
```

**Important Warnings:**

**Cannot Delete If:**
- Street is used in citizen addresses
- Street appears in program beneficiary records
- Street referenced in reports

**Before Deleting:**
1. Search for citizens with this address
2. Verify no active records use this street
3. Consider editing instead of deleting
4. Check if it's a duplicate (merge data first)

**Error Message Example:**
```
Cannot delete street "Calle Juárez"
Currently used in 247 citizen addresses.
Please reassign addresses before deleting.
```

**Safe Deletion Workflow:**
```
1. Verify street has zero usages
2. Check it's not just a typo (edit instead)
3. Confirm it's truly a duplicate
4. Delete the duplicate only
5. Keep the primary/correct entry
```

---

## Managing Neighborhoods (Colonias)

The Colonias section manages neighborhood or district information.

### Colonias List View

[Screenshot: Colonias table showing neighborhood names and postal codes]

Similar to streets, colonias are displayed in a searchable, paginated list.

**Table Columns:**

| Column | Description | Example |
|--------|-------------|---------|
| **Nombre** | Colonia name | Centro |
| **Código Postal** | Postal code | 48300 |
| **Municipio** | Municipality | Puerto Vallarta |
| **Número de Residentes** | Resident count | 1,247 |
| **Acciones** | Action buttons | Edit, Delete |

### Searching Colonias

[Screenshot: Colonia search bar with example "Centro"]

**Search Functionality:**

#### By Name
```
Search: Centro
Results: All colonias with "Centro" in name
- Centro
- Centro Norte
- Residencial del Centro
```

#### By Postal Code
```
Search: 48300
Results: Colonias with postal code 48300
- Centro
- Zona Romántica
- Emiliano Zapata
```

#### By Municipality
```
Search: Puerto Vallarta
Results: All colonias in Puerto Vallarta
```

**Search Tips:**
- Start typing for instant results
- Search postal code for specific area
- Use partial names for broader results
- Clear search to see full list

### Adding a New Colonia

Add neighborhoods not yet in the system.

[Screenshot: Add Colonia form with required fields]

**How to Add:**

```
1. Click "Add New Colonia" button
2. Fill in the form:
   - Colonia name (required)
   - Postal code (required)
   - Municipality (required)
   - Additional info (optional)
3. Click "Save"
4. New colonia appears in list
5. Available in address forms immediately
```

**Add Colonia Form Fields:**

**Colonia Name** (required)
- Official neighborhood name
- Use proper capitalization
- Example: "Zona Romántica"

**Postal Code (CP)** (required)
- 5-digit postal code
- Example: 48380
- Validation: Must be exactly 5 digits

**Municipality** (required)
- Select from dropdown
- Example: Puerto Vallarta
- Or type to search municipalities

**State**
- Usually auto-filled based on municipality
- Example: Jalisco

**Additional Information** (optional)
- Neighborhood boundaries
- Notable landmarks
- Local characteristics
- Administrative notes

**Validation:**
- Colonia name required
- Postal code must be 5 digits
- Municipality required
- Duplicate check warns of similar names

**Example Entry:**
```
Name: 5 de Diciembre
Postal Code: 48350
Municipality: Puerto Vallarta
State: Jalisco
Info: Residential area south of Centro, near airport
```

### Editing Colonias

Update existing colonia information.

[Screenshot: Inline editing for colonia]

**How to Edit:**

```
1. Find colonia (use search if needed)
2. Click "Edit" button
3. Fields become editable inline
4. Update information:
   - Correct name spelling
   - Update postal code
   - Modify municipality
   - Add notes
5. Click "Save" to confirm
6. Or "Cancel" to discard changes
```

**Common Updates:**
- Correcting postal code errors
- Updating official colonia names
- Adding additional information
- Fixing municipality assignments
- Standardizing name formats

**Inline Editing Example:**

**Before:**
```
Centro | 48300 | Puerto Vallarta | [Edit]
```

**During Editing:**
```
[Centro_____] [48300_] [▼Puerto Vallarta] [✓] [✗]
```

**After:**
```
Centro | 48300 | Puerto Vallarta | [Edit]
```

### Deleting Colonias

Remove duplicate or incorrect colonias.

**How to Delete:**

```
1. Locate colonia in list
2. Click "Delete" button
3. Confirmation prompt appears
4. Verify it's safe to delete
5. Click "Confirm"
6. Colonia removed
```

**Important Considerations:**

**Cannot Delete If:**
- Citizens have addresses in this colonia
- Programs show beneficiaries in this colonia
- Active records reference this colonia

**Error Message:**
```
Cannot delete colonia "Centro"
Currently assigned to 3,428 citizen addresses.
Please reassign addresses before deleting.
```

**Safe to Delete:**
- Brand new entry with no usages
- Confirmed duplicate
- Entered in error
- Test data

**Before Deleting:**
1. Check resident count (should be 0)
2. Search for citizens in this colonia
3. Verify it's a duplicate
4. Merge data to correct colonia if needed

---

## Using Geographic Data in Practice

### When Creating Citizen Addresses

**Workflow:**
```
1. Start creating/editing citizen
2. Get to address section
3. Street field: Dropdown loads all streets
4. Type to search: "Jua" shows streets starting with "Jua"
5. Select: "Calle Juárez"
6. Colonia field: Dropdown loads all colonias
7. Type to search: "Cen" shows colonias starting with "Cen"
8. Select: "Centro"
9. Postal code: Auto-fills "48300" (based on Centro)
10. Complete remaining address fields
```

**If Street/Colonia Missing:**
```
1. Notice dropdown doesn't have the needed street/colonia
2. Click "Add New" link
3. Quick add form appears
4. Enter street/colonia details
5. Save
6. Return to citizen form
7. New street/colonia now available in dropdown
8. Select and continue
```

### Maintaining Data Quality

**Regular Maintenance:**

**Weekly:**
- Review newly added streets/colonias
- Check for duplicates
- Verify postal codes
- Standardize naming

**Monthly:**
- Audit for unused entries
- Clean up test data
- Update based on official sources
- Document any major changes

**Quarterly:**
- Cross-reference with official postal service data
- Update municipality assignments
- Review and merge duplicates
- Generate quality report

**Quality Checks:**

**For Streets:**
- [ ] Name spelled correctly
- [ ] Type assigned appropriately
- [ ] No duplicates
- [ ] Alternate names added
- [ ] Used in at least one address

**For Colonias:**
- [ ] Official postal code verified
- [ ] Municipality correct
- [ ] No duplicates
- [ ] Boundaries clear
- [ ] Referenced in addresses

### Common Geographic Data Tasks

#### Task: Add a New Street from Citizen Registration

```
1. Receiving citizen registration
2. Citizen lives on "Calle Nueva" (not in system)
3. Click Calles tab
4. Click "Add New Street"
5. Enter:
   Name: Nueva
   Type: Calle
6. Save
7. Return to citizen form
8. Select "Calle Nueva" from dropdown
9. Complete address
```

#### Task: Fix Street Type Error

```
1. Notice "Calle Revolución" should be "Avenida Revolución"
2. Go to Calles section
3. Search: "Revolucion"
4. Click "Edit" on the street
5. Change Type: Calle → Avenida
6. Add note: "Corrected type per official designation"
7. Save
8. System updates all references automatically
```

#### Task: Merge Duplicate Colonias

```
1. Discover duplicates:
   - "5 de Diciembre"
   - "5 De Diciembre" (different capitalization)
2. Check usage:
   - First: 234 citizens
   - Second: 12 citizens
3. Determine which to keep (first, more usage)
4. For each citizen in second colonia:
   - Edit citizen record
   - Change colonia to first version
   - Save
5. Once second colonia has 0 usage:
   - Delete the duplicate
6. Only primary version remains
```

#### Task: Update Postal Codes

```
1. Receive official postal code update
2. Go to Colonias section
3. Search affected colonia
4. Click "Edit"
5. Update postal code: Old → New
6. Add note: "Updated per SEPOMEX 2025"
7. Save
8. All addresses automatically reflect new code
```

## Integration with Other Modules

### Streets/Colonias in Citizen Management

When viewing citizen profiles:
- Full address displays street and colonia names
- Click street/colonia to see all citizens at that location
- Filter citizens by colonia
- Map shows colonia boundaries (if configured)

### Geographic Data in Social Programs

Program beneficiary maps:
- Cluster by colonia
- Color code by neighborhood density
- Filter program list by colonia
- Generate reports per neighborhood

### Reporting by Geography

Reports can be filtered by:
- Specific streets
- Particular colonias
- Postal code ranges
- Municipality-wide

## Best Practices

### Naming Conventions

**Streets:**
- Use official names from city records
- Capitalize properly: "Juárez" not "JUAREZ" or "juarez"
- Don't include type in name: "Juárez" not "Calle Juárez"
- Add accents where appropriate: "Revolución" not "Revolucion"

**Colonias:**
- Use official postal service names
- Match SEPOMEX designations
- Include cardinal directions if official: "Centro Norte"
- Avoid abbreviations: "Fraccionamiento" not "Fracc."

### Data Accuracy

**Verify Before Adding:**
1. Check official sources (city, postal service)
2. Confirm spelling
3. Validate postal code
4. Look for existing similar entries

**Sources to Consult:**
- SEPOMEX (Mexican Postal Service) official catalog
- Municipal urban development plans
- Google Maps (for reference, not sole source)
- Official city street directory

### Preventing Duplicates

**Before Adding New:**
1. Search thoroughly
2. Try variations: "5 de Diciembre", "5 Diciembre", "Cinco de Diciembre"
3. Check common misspellings
4. Review recently added entries

**When You Find Duplicates:**
1. Determine which is correct/more complete
2. Note usage count for each
3. Migrate data to primary version
4. Delete duplicate only when safe

## Troubleshooting

### Street/Colonia Not Appearing in Dropdown

**Solutions:**
1. Refresh the page
2. Clear search and try again
3. Verify it was saved (check list)
4. Check spelling in dropdown search
5. Add it if truly missing

### Cannot Delete Street/Colonia

**Reason:**
- Still in use by citizen addresses
- Referenced in program records

**Resolution:**
```
1. Search for all citizens using this street/colonia
2. Decide if entries should be updated or if deletion is wrong
3. If truly a duplicate, update all citizens to use correct version
4. Once usage count reaches 0, deletion allowed
5. Or keep entry if it's actually in use (don't delete)
```

### Postal Code Doesn't Match

**Check:**
1. Verify with official SEPOMEX catalog
2. Update colonia postal code if incorrect
3. Or reassign citizen to correct colonia
4. Document source of correct postal code

### Too Many Search Results

**Refine Search:**
1. Use more specific terms
2. Include postal code in search
3. Add municipality name
4. Use exact phrase if possible

## Quick Reference

### Common Street Types

| Spanish | English | Usage |
|---------|---------|-------|
| Calle | Street | Standard streets |
| Avenida | Avenue | Major roads |
| Boulevard | Boulevard | Wide thoroughfares |
| Privada | Private | Gated/private streets |
| Cerrada | Closed | Dead-end streets |
| Callejón | Alley | Narrow passages |
| Camino | Road | Less urban routes |
| Andador | Walkway | Pedestrian paths |

### Keyboard Shortcuts
- **Tab**: Move between form fields
- **Enter**: Submit search
- **Esc**: Cancel inline edit
- **Ctrl/Cmd + F**: Quick search page

## Next Steps

Now that you understand geographic data:

- **[QR Scanner](06-qr-scanner.md)**: Quick access to citizen information
- **[Reports](07-reports.md)**: Manage citizen reports
- **[Tips and Tricks](08-tips-and-tricks.md)**: Advanced workflows and shortcuts

---

**Pro Tip**: When citizens call asking about programs, having accurate addresses means you can quickly find them and verify their enrollment. Keep geographic data clean for smooth operations.
