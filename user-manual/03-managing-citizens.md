# Managing Citizens

The Ciudadanos (Citizens) section is your comprehensive database for managing citizen information, tracking program enrollment, and viewing citizen reports. This guide covers all citizen management features.

## Accessing Citizen Management

1. Click the **Ciudadanos** tab in the main navigation
2. The citizen list loads, displaying all registered citizens

[Screenshot: Citizens list view with search bar and data table]

**Note**: Initial load may take a few seconds when dealing with 10,000+ citizen records.

## Understanding the Citizen Table

The citizen table uses AG Grid, a powerful data grid system that handles large datasets efficiently.

### Table Columns

By default, you'll see these columns:

| Column | Description | Example |
|--------|-------------|---------|
| **Nombre** | Full name | María García López |
| **CURP** | Unique citizen ID | GAML850615MDFRRR04 |
| **Fecha de Nacimiento** | Date of birth | 15/06/1985 |
| **Género** | Gender | Femenino |
| **Teléfono** | Phone number | 322-123-4567 |
| **Email** | Email address | maria.garcia@email.com |
| **Dirección** | Complete address | Calle Juárez 123, Centro |
| **Colonia** | Neighborhood | Centro |
| **Programas** | Enrolled programs count | 3 programas |
| **Reportes** | Submitted reports count | 2 reportes |
| **Acciones** | Action buttons | View, Edit, Delete |

### Table Features

**Sortable Columns:**
- Click any column header to sort ascending
- Click again to sort descending
- Click a third time to remove sorting

**Resizable Columns:**
- Hover over the border between column headers
- Click and drag to resize

**Fixed Header:**
- As you scroll down, the header row stays visible
- Always know which column you're viewing

## Searching for Citizens

The search functionality allows you to quickly find specific citizens.

[Screenshot: Search bar with example search "Maria Garcia"]

### Search Methods

#### By Name
```
Search: Maria Garcia
Results: All citizens with "Maria" or "Garcia" in their name
```

**Tips:**
- Partial names work (e.g., "Mar" finds Maria, Mariana, Marco)
- Search is case-insensitive
- Search checks first name, middle name, and last names

#### By CURP
```
Search: GAML850615
Results: Citizens with matching CURP
```

**Tips:**
- You can enter partial CURP
- Great for exact identification
- CURP search is case-insensitive

#### Combined Search
```
Search: Garcia Centro
Results: Citizens named Garcia living in Centro neighborhood
```

**How It Works:**
- Search looks across multiple fields simultaneously
- Finds records matching any search term
- More specific searches yield fewer, more relevant results

### Search Workflow

1. **Click the search box** at the top of the citizen table
2. **Type your search term** (name, CURP, or address)
3. **Results update automatically** as you type
4. **Clear search** by clicking the X icon or deleting all text

**Performance Note**: Search across 10,000+ records is optimized and returns results quickly.

## Viewing Citizen Details

To see complete information about a citizen:

1. **Locate the citizen** using search or scrolling
2. **Click the "View" button** (eye icon) in the Acciones column
3. **Citizen detail panel opens** showing complete profile

[Screenshot: Citizen detail view with all information sections]

### Detail View Sections

#### Personal Information
- Full legal name
- CURP (Unique Citizen ID)
- Date of birth and age
- Gender
- Marital status
- Occupation

#### Contact Information
- Primary phone number
- Secondary phone (if available)
- Email address
- Preferred contact method

#### Address Details
- Street name and number
- Interior number (if applicable)
- Neighborhood (Colonia)
- Postal code
- Municipality
- State
- Complete formatted address

#### Enrolled Social Programs

[Screenshot: List of programs showing program name, type, status, enrollment date]

**Table Shows:**
- Program name (e.g., "Programa Federal de Becas")
- Program type (Federal or Local)
- Enrollment status (Active, Pending, Completed)
- Enrollment date
- Request status
- Benefit amount (if applicable)

**Actions:**
- Click any program name to view full program details
- See benefit history for that citizen
- View documents associated with the enrollment

#### Citizen Reports

[Screenshot: List of reports submitted by the citizen]

**Table Shows:**
- Report type (e.g., "Solicitud de Apoyo", "Queja")
- Submission date
- Current status (Pending, In Progress, Resolved)
- Assigned staff member (if any)
- Priority level

**Actions:**
- Click any report to view complete details
- See report history and status changes
- View attached documents or photos

#### Activity History
- Recent changes to citizen record
- Program enrollments and changes
- Report submissions
- Status updates

## Customizing Table Columns

Gobify allows you to customize which columns you see and their order.

### Showing/Hiding Columns

1. **Click the column menu icon** (three dots or grid icon near the search bar)
2. **Column list appears** with checkboxes
3. **Check/uncheck columns** to show or hide them
4. **Your preferences are saved** automatically

[Screenshot: Column customization menu with checkboxes]

**Commonly Hidden Columns:**
- Email (if not needed for your work)
- Secondary phone numbers
- Detailed address fields (if you only need neighborhood)

**Commonly Visible Columns:**
- Name, CURP (always recommended)
- Programs count
- Reports count
- Primary contact info

### Rearranging Columns

1. **Click and hold** on a column header
2. **Drag left or right** to desired position
3. **Release mouse** to drop column in new location
4. **Order is saved** for future sessions

### Resetting to Default

If your customization gets confusing:

1. Click the column menu icon
2. Select "Reset to Default" or "Restore Defaults"
3. Columns return to original layout

## Bulk Operations

When you need to work with multiple citizens at once, use bulk operations.

### Selecting Multiple Citizens

**Select Individual Citizens:**
1. Check the checkbox at the start of each citizen row
2. Selected rows highlight
3. Count of selected citizens appears at top

[Screenshot: Three citizens selected with counter showing "3 selected"]

**Select All Visible:**
1. Check the checkbox in the table header
2. All citizens on current page are selected
3. Or use "Select All" option if available

**Select Range:**
1. Click the first citizen's checkbox
2. Hold Shift key
3. Click the last citizen's checkbox
4. All citizens between are selected

### Bulk Actions Available

Once you've selected multiple citizens:

#### Export Selected
- Click "Export" button
- Choose format (Excel, CSV, PDF)
- Download contains only selected citizens

#### Print Selected
- Click "Print" button
- Print preview shows selected citizen list
- Useful for physical records

#### Assign to Program
- Click "Assign to Program" button
- Select which program
- Bulk enrollment initiated
- Review and confirm

#### Send Notification
- Click "Send Notification"
- Choose notification template
- Send email or SMS to selected citizens
- Useful for program updates

### Deselecting Citizens

- Click individual checkboxes again to deselect
- Click header checkbox to deselect all
- Click "Clear Selection" button if available

## Exporting Citizen Data

Export citizen data for reports, analysis, or records.

### Export Options

[Screenshot: Export menu showing format options]

#### Excel Export (.xlsx)
**Best For:** Data analysis, creating reports, sharing with Excel users

**Contains:**
- All visible columns in current view
- Formatted data
- Multiple sheets if exporting related data (programs, reports)

**How To:**
1. Click "Export" button
2. Select "Excel (.xlsx)"
3. File downloads automatically
4. Open in Microsoft Excel or similar software

#### CSV Export (.csv)
**Best For:** Importing to other systems, database backups, universal compatibility

**Contains:**
- All data in comma-separated format
- No formatting, just raw data
- Can open in Excel or text editors

**How To:**
1. Click "Export" button
2. Select "CSV (.csv)"
3. File downloads automatically
4. Open in Excel, Numbers, or Google Sheets

#### PDF Export (.pdf)
**Best For:** Printing, official reports, read-only distribution

**Contains:**
- Formatted table with all visible columns
- Professional layout
- Headers and footers with date/time
- Page numbers

**How To:**
1. Click "Export" button
2. Select "PDF (.pdf)"
3. File downloads automatically
4. Open in PDF reader or print

### Export Workflow

**Export Current View:**
```
1. Apply any filters or searches
2. Customize columns to show only what you need
3. Click "Export"
4. Choose format
5. Download completes
```

**Export Selected Citizens:**
```
1. Select specific citizens using checkboxes
2. Click "Export Selected"
3. Choose format
4. Download contains only selected citizens
```

**Export All Citizens:**
```
1. Clear any filters or selections
2. Click "Export All" (may require confirmation)
3. Choose format
4. Wait for generation (may take time for 10,000+ records)
5. Download completes
```

### Export Best Practices

**Before Exporting:**
- Apply necessary filters to reduce data size
- Customize columns to include only needed information
- Verify search/filter criteria are correct

**File Naming:**
- Exports typically auto-name with date/time
- Example: `ciudadanos_2025-12-08_14-30.xlsx`
- Rename downloaded files for organization

**Large Exports:**
- Exports of 10,000+ records may take 10-30 seconds
- Don't close the browser while export generates
- You'll see a progress indicator or notification

**Data Privacy:**
- Exported files contain sensitive personal information
- Store securely
- Follow your organization's data protection policies
- Delete when no longer needed

## Pagination

With thousands of citizens, data is divided into pages for performance.

### Understanding Pagination

[Screenshot: Pagination controls showing "Showing 1-25 of 12,456 citizens"]

**Display Shows:**
- Current page range (e.g., "1-25")
- Total citizen count (e.g., "of 12,456")
- Current page number
- Total page count

### Navigating Pages

**Page Controls:**
- **First Page**: Click |◄ button
- **Previous Page**: Click ◄ button
- **Next Page**: Click ► button
- **Last Page**: Click ►| button
- **Specific Page**: Enter page number or use dropdown

**Jump to Page:**
1. Click the page number field
2. Type desired page number
3. Press Enter
4. Page loads immediately

### Rows Per Page

Change how many citizens display per page:

1. Look for "Rows per page" dropdown
2. Click to see options (usually 10, 25, 50, 100)
3. Select your preference
4. Table reloads with new page size

**Choosing Page Size:**
- **10-25 rows**: Best for detailed review, slower computers
- **50 rows**: Good balance of speed and visibility
- **100 rows**: Fast scrolling, requires good internet

**Performance Note**: Larger page sizes load more data, which may take slightly longer on slower connections.

## Common Citizen Management Tasks

### Task: Find a Specific Citizen

```
1. Click Ciudadanos tab
2. Click search box
3. Type citizen's name or CURP
4. Click "View" on the correct citizen
5. Review complete profile
```

### Task: Check a Citizen's Enrolled Programs

```
1. Search for and view citizen
2. Scroll to "Programas Sociales Inscritos" section
3. Review list of programs
4. Click any program name for details
```

### Task: Export Citizens in a Neighborhood

```
1. Click search box
2. Type neighborhood name (e.g., "Centro")
3. Results show only Centro residents
4. Click "Export"
5. Select format (Excel recommended)
6. Download and open file
```

### Task: Review Recent Reports

```
1. View citizen details
2. Scroll to "Reportes" section
3. See list of submitted reports
4. Click report to view details
5. Check status and assigned staff
```

### Task: Create Contact List for a Program

```
1. Apply program filter or search
2. Customize columns: Show Name, Phone, Email
3. Hide unnecessary columns
4. Export to Excel
5. Use export for calling/emailing campaign
```

## Troubleshooting

### Table Won't Load

**Solutions:**
1. Refresh the page (F5)
2. Check internet connection
3. Clear browser cache
4. Try a different browser
5. Contact IT if problem persists

### Search Returns No Results

**Verify:**
1. Spelling is correct
2. You're not searching for information that doesn't exist
3. Try partial search (fewer letters)
4. Clear any applied filters
5. Remove search and start over

### Slow Performance

**Optimize:**
1. Reduce rows per page (use 25 instead of 100)
2. Apply filters to reduce dataset
3. Close other browser tabs
4. Check internet connection speed
5. Avoid exporting all records at once

### Export Fails

**Try:**
1. Reduce data size (apply filters first)
2. Select fewer columns
3. Export in smaller batches
4. Try different format (CSV instead of Excel)
5. Check available disk space

## Best Practices

### Daily Operations

1. **Use Search Efficiently**: Type specific terms rather than scrolling
2. **Customize Your View**: Hide columns you never use
3. **Verify Before Exporting**: Check filters and selections
4. **Regular Data Checks**: Ensure citizen information is current

### Data Quality

1. **Report Errors**: If you find incorrect information, report it
2. **Check Duplicates**: Watch for duplicate citizen records
3. **Verify CURP**: Ensure CURP matches government records
4. **Update Contact Info**: Keep phone and email current

### Security

1. **Log Out**: Always log out when finished
2. **Secure Exports**: Protect downloaded files with passwords
3. **Share Carefully**: Only export data you're authorized to share
4. **Screen Lock**: Lock your computer when stepping away

## Quick Reference

### Keyboard Shortcuts
- **Ctrl/Cmd + F**: Quick search
- **Tab**: Navigate between fields
- **Enter**: Open selected citizen
- **Esc**: Close detail view

### Common Filters
- By neighborhood: Type colonia name
- By program: Type program name
- By status: Use status dropdown if available
- By date range: Use date pickers for enrollments

## Next Steps

Now that you can manage citizens:

- **[Social Programs](04-social-programs.md)**: Learn to enroll citizens in programs
- **[Geographic Data](05-geographic-data.md)**: Understand streets and neighborhoods
- **[Reports](07-reports.md)**: Process citizen reports efficiently

---

**Pro Tip**: Create a "favorites" list by exporting a small Excel file of citizens you frequently work with. Keep it handy for quick CURP or contact lookups.
