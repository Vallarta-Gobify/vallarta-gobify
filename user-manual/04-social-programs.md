# Social Programs Management

The Programas Sociales (Social Programs) section is the core of Gobify, where you manage federal and local assistance programs, track beneficiaries, create requests, and generate reports.

## Accessing Social Programs

1. Click the **Programas Sociales** tab in the main navigation
2. The programs list loads, displaying all available programs based on your role

[Screenshot: Programs list showing federal and local programs]

## Understanding Program Types

Gobify manages two distinct categories of social programs:

### Federal Programs

**Characteristics:**
- Funded by federal government
- Standardized requirements nationwide
- Typically larger budgets
- Strict compliance requirements
- Labeled with "Federal" badge

**Examples:**
- Programa Federal de Becas (Federal Scholarship Program)
- Apoyo Alimentario Federal (Federal Food Assistance)
- Pensión para Adultos Mayores (Senior Citizen Pension)

### Local Programs

**Characteristics:**
- Funded by municipal/state government
- Community-specific requirements
- More flexible eligibility
- Faster approval processes
- Labeled with "Local" badge

**Examples:**
- Apoyo a Madres Solteras (Single Mother Support)
- Becas Municipales (Municipal Scholarships)
- Mejoramiento de Vivienda (Home Improvement)

### Your Access Level

Your user role determines which programs you can see:

| User Role | Federal Programs | Local Programs |
|-----------|-----------------|----------------|
| Federal-only | ✓ Yes | ✗ No |
| Local-only | ✗ No | ✓ Yes |
| Full access | ✓ Yes | ✓ Yes |

## Browsing Social Programs

### Programs List View

[Screenshot: Programs list showing cards with program names, types, and beneficiary counts]

The programs list displays cards or rows for each program:

**Card Information:**
- Program name
- Program type badge (Federal/Local)
- Number of active beneficiaries
- Number of pending requests
- Brief description
- "View Details" button

### Sorting and Filtering

**Sort Programs:**
- By name (alphabetically)
- By beneficiary count (most/least)
- By type (Federal or Local)
- By status (Active, Closed, Upcoming)

**Filter Programs:**
1. Use the filter dropdown at the top
2. Select criteria:
   - Program type (Federal/Local)
   - Status (Active/Inactive)
   - Category (Education, Health, Housing, etc.)
3. View filtered results

**Search Programs:**
1. Type in the search box
2. Search finds matches in:
   - Program name
   - Description
   - Category
3. Results update in real-time

## Viewing Program Details

To see complete information about a social program:

1. **Click the program card** or "View Details" button
2. **Program detail page opens** with comprehensive information

[Screenshot: Program detail page with tabs and map]

### Program Details Sections

#### Overview Tab

**General Information:**
- Full program name
- Program type (Federal/Local)
- Program category (Education, Health, etc.)
- Description and objectives
- Eligibility requirements
- Required documents
- Benefit amount or type
- Program duration

**Statistics:**
- Total beneficiaries: 1,247
- Active requests: 234
- Approved this month: 156
- Pending reviews: 78
- Budget utilization: 68%

**Program Status:**
- Open for new applications
- Application deadline
- Next review date

#### Beneficiaries List

[Screenshot: Table showing all beneficiaries enrolled in the program]

**Table Columns:**
- Beneficiary name
- CURP
- Folio (request number)
- Address
- Enrollment date
- Status (Active, Suspended, Completed)
- Benefit amount
- Last payment date

**Search Beneficiaries:**

Search is extremely flexible. You can search by:

1. **Name**
   ```
   Search: Maria Garcia
   Results: All beneficiaries named Maria Garcia
   ```

2. **Folio (Request Number)**
   ```
   Search: 2024-001234
   Results: Specific request by folio number
   ```

3. **Address**
   ```
   Search: Calle Juarez
   Results: All beneficiaries living on Calle Juarez
   ```

4. **Neighborhood**
   ```
   Search: Centro
   Results: All beneficiaries in Centro neighborhood
   ```

5. **Combined Search**
   ```
   Search: Garcia Centro
   Results: Garcia surname residents in Centro
   ```

**How Search Works:**
- Searches across all fields simultaneously
- Partial matches work
- Case-insensitive
- Real-time results as you type

#### Map View

The interactive map shows beneficiary locations visually.

[Screenshot: Mapbox map with cluster markers and individual pins]

**Map Features:**

**Cluster Markers:**
- Groups of nearby beneficiaries appear as numbered circles
- Number indicates how many beneficiaries in that area
- Color intensity shows density (darker = more beneficiaries)

**Zooming In:**
- Click a cluster marker to zoom in
- Clusters break apart into smaller clusters
- Eventually individual markers appear

**Individual Markers:**
- Single pin represents one beneficiary
- Click pin to see popup with:
  - Beneficiary name
  - Address
  - Folio number
  - Status
  - "View Details" link

**Map Controls:**

[Screenshot: Map controls showing zoom buttons and location]

- **+/-** buttons: Zoom in and out
- **Location button**: Recenter map
- **Full screen**: Expand map to full screen
- **Mouse wheel**: Zoom in/out
- **Click and drag**: Pan around map

**Using the Map:**

1. **Find High-Density Areas**
   ```
   1. Look for large cluster markers
   2. These show where most beneficiaries live
   3. Useful for planning outreach events
   4. Identify underserved areas
   ```

2. **Locate Specific Beneficiary**
   ```
   1. Search for beneficiary name
   2. Map automatically centers on their location
   3. Marker highlights
   4. Click for details popup
   ```

3. **Plan Field Visits**
   ```
   1. Zoom to specific neighborhood
   2. See all beneficiaries in that area
   3. Click each marker to note addresses
   4. Plan efficient visit route
   ```

4. **Analyze Geographic Distribution**
   ```
   1. Zoom out to see entire city
   2. Notice which areas have more beneficiaries
   3. Identify gaps in coverage
   4. Plan targeted enrollment campaigns
   ```

**Map Best Practices:**
- Use clusters to understand distribution patterns
- Zoom in progressively rather than jumping to max zoom
- Use search to locate specific addresses quickly
- Take screenshots for reports (use full-screen mode)

#### Documents Tab

View and manage program-related documents:
- Program guidelines (PDF)
- Application forms
- Required document checklists
- Sample filled forms
- Program announcements

## Creating New Program Requests

When a citizen applies for a program, you create a request in the system.

### Request Creation Workflow

[Screenshot: Step-by-step request creation form]

#### Step 1: Citizen Information

1. **Click "New Request" button** on the program detail page
2. **Enter or search for citizen:**

   **Option A - Existing Citizen:**
   ```
   1. Type name or CURP in search box
   2. Select citizen from dropdown
   3. Information auto-fills
   4. Click "Next"
   ```

   **Option B - New Citizen:**
   ```
   1. Click "Register New Citizen"
   2. Fill in personal information:
      - Full name (as appears on ID)
      - CURP (18 characters)
      - Date of birth
      - Gender
      - Phone number
      - Email (if available)
   3. Click "Next"
   ```

**Required Fields:**
- Full name (required)
- CURP (required, validated for format)
- Date of birth (required)
- Gender (required)
- Phone number (required, primary contact)

**Optional Fields:**
- Secondary phone
- Email address
- Occupation
- Marital status

**Validation:**
- CURP format checked automatically
- Duplicate CURP warning if already exists
- Phone format validated
- Age calculated from birth date

#### Step 2: Address Information

[Screenshot: Address form with street, colonia, postal code fields]

**Complete the address:**

1. **Street Information:**
   - Select street from dropdown (searches as you type)
   - Or click "Add New Street" if not found
   - Enter street number (exterior)
   - Enter interior number (if applicable, e.g., apartment)

2. **Neighborhood (Colonia):**
   - Select colonia from dropdown
   - Or click "Add New Colonia" if not found
   - Auto-fills postal code when available

3. **Additional Details:**
   - Postal code (CP)
   - References (e.g., "between Hidalgo and Morelos")
   - Neighborhood landmarks

**Tips:**
- Use search in street dropdown: type "Jua" finds "Calle Juárez"
- If address doesn't exist, add street/colonia first (see Geographic Data guide)
- Provide references for easier field visits
- Verify postal code matches colonia

#### Step 3: School Information

**For education-related programs only (e.g., scholarship programs)**

[Screenshot: School information form]

**Student Details:**
- School name (select from dropdown)
- School level (Primaria, Secundaria, Preparatoria, Universidad)
- Grade/semester
- Student ID number
- School address (if different from home)

**Academic Information:**
- Current grade point average
- Attendance percentage
- Special needs (if applicable)

**Skip This Step:**
- If not an education program, this step is hidden
- Click "Next" to proceed

#### Step 4: Review and Submit

[Screenshot: Review screen showing all entered information]

**Review All Information:**
- Citizen details
- Complete address
- School info (if applicable)
- Program selected
- Required documents checklist

**Before Submitting:**
1. **Verify all information is correct**
2. **Check for typos in names and CURP**
3. **Confirm address is complete**
4. **Ensure all required fields are filled**

**Submit Request:**
1. Review the summary
2. Click "Submit Request"
3. System generates folio number
4. Confirmation message appears
5. Request appears in pending list

**Folio Number:**
```
Example: 2025-FED-001234

Format: YEAR-TYPE-NUMBER
- 2025: Current year
- FED: Federal (or LOC for local)
- 001234: Sequential number
```

**Save this folio number** - it's the request's unique identifier.

### After Creating Request

**Next Steps:**
1. Request status: Pendiente (Pending)
2. Appears in program's pending requests
3. Awaits document upload and review
4. Can be edited before approval

**Notify Citizen:**
- Provide folio number
- List required documents
- Explain next steps
- Set expectation for review timeline

## Editing Existing Requests

You can modify requests that haven't been finalized.

### How to Edit a Request

1. **Go to program details**
2. **Click Beneficiaries tab**
3. **Locate the request** (search by folio or name)
4. **Click "Edit" button** (pencil icon)
5. **Edit form appears** with current information

[Screenshot: Edit request form with pre-filled data]

### What You Can Edit

**Always Editable:**
- Contact information (phone, email)
- Address details
- School information (if applicable)
- Supporting notes

**Sometimes Editable:**
- Personal information (if request is pending)
- Status (can change from pending)
- Documents (can add/remove)

**Never Editable:**
- CURP (unique identifier)
- Folio number (system generated)
- Creation date
- Approval date (once approved)

### Editing Workflow

```
1. Click "Edit Request"
2. Form loads with current data
3. Make necessary changes
4. Click "Save Changes"
5. Confirmation message appears
6. Updated information displays immediately
```

**Best Practices:**
- Document why you're editing (in notes field)
- Verify changes with citizen if possible
- Check that edits don't affect eligibility
- Save frequently if making multiple changes

## Updating Request Status

Managing the lifecycle of a request through status changes.

### Available Statuses

| Status | Meaning | Next Actions |
|--------|---------|-------------|
| **Pendiente** | Awaiting review | Upload documents, verify eligibility |
| **En Revisión** | Under review | Complete assessment |
| **Aprobada** | Approved | Activate benefits, notify citizen |
| **Negada** | Denied | Add reason, notify citizen |
| **Suspendida** | Suspended | Investigate issue |
| **Completada** | Completed | Archive, final report |

### Changing Status

[Screenshot: Status dropdown with options and reason field]

#### Approving a Request (Aprobada)

```
1. Review request details thoroughly
2. Verify all documents uploaded
3. Check eligibility criteria
4. Click "Change Status"
5. Select "Aprobada"
6. Add approval notes (optional but recommended)
7. Set benefit start date
8. Click "Confirm"
9. System sends approval notification to citizen
```

**Approval Checklist:**
- [ ] All required documents submitted
- [ ] Information verified (CURP, address, etc.)
- [ ] Meets eligibility criteria
- [ ] No duplicate enrollment
- [ ] Budget available
- [ ] Approval authority confirmed

#### Denying a Request (Negada)

```
1. Determine denial reason
2. Click "Change Status"
3. Select "Negada"
4. REQUIRED: Add reason for denial
5. Select denial category:
   - Does not meet eligibility
   - Incomplete documentation
   - Duplicate enrollment
   - Budget unavailable
   - Other (specify)
6. Click "Confirm"
7. System sends denial notification
```

**Important**: Always provide clear, specific denial reasons. Citizens have the right to understand why their request was denied.

#### Suspending a Request (Suspendida)

Use when temporary issue needs resolution:

```
1. Identify the issue (e.g., missing documents)
2. Change status to "Suspendida"
3. Add detailed suspension reason
4. Set follow-up date
5. Notify citizen of required action
6. Resume when issue resolved
```

**Common Suspension Reasons:**
- Missing or expired documents
- Address verification needed
- Pending additional information
- Temporary budget freeze
- Investigation required

### Status Change Workflow

**General Process:**
```
1. Open request details
2. Click "Update Status" button
3. Select new status from dropdown
4. Fill in required reason/notes
5. Add any supporting information
6. Review status change
7. Click "Confirm"
8. Status updates immediately
9. Automatic notification sent (if configured)
10. Status change logged in history
```

**Status History:**
- All status changes are recorded
- Shows who made the change
- Shows when change occurred
- Shows reason provided
- Creates audit trail

## Exporting Program Data

Generate reports and export beneficiary data for analysis or documentation.

### Export to PDF

PDF exports are ideal for official reports and printing.

[Screenshot: PDF export dialog with options and progress bar]

#### PDF Export Features

**What's Included:**
- Program header with logo
- Program name and details
- Export date and time
- Beneficiary list (formatted table)
- Statistics summary
- Page numbers
- Professional formatting

**How to Export PDF:**

```
1. Open program details
2. Click "Export" button
3. Select "Export to PDF"
4. PDF generation modal appears
5. Configure options:
   - Include statistics: Yes/No
   - Include map: Yes/No
   - Date range: All time / Custom
   - Status filter: All / Active only
6. Click "Generate PDF"
7. Progress bar shows generation status
8. Download starts automatically when complete
```

**Progress Tracking:**

[Screenshot: Progress bar showing "Generating PDF... 68%"]

The progress bar shows real-time status:
- "Preparing data..." (0-20%)
- "Formatting document..." (20-60%)
- "Generating pages..." (60-90%)
- "Finalizing PDF..." (90-100%)
- "Download ready!" (100%)

**Large Exports:**
- Programs with 1,000+ beneficiaries may take 30-60 seconds
- Don't close browser during generation
- You'll see progress percentage
- Can continue working in another tab

#### PDF Export Options

**Date Range:**
- All time: Complete history
- Current year: This year's enrollments
- Current month: Recent enrollments
- Custom: Specify start and end dates

**Status Filter:**
- All statuses: Complete list
- Active only: Currently enrolled
- Pending: Awaiting approval
- Approved: All approved requests
- Custom: Multiple status selection

**Include Map:**
- Yes: Adds map screenshot to PDF
- No: Text-only report (faster, smaller file)

### Export to Excel

Excel exports provide data for analysis and manipulation.

[Screenshot: Excel export button and options]

#### How to Export Excel:

```
1. Open program details
2. Click "Export" button
3. Select "Export to Excel"
4. File generates (usually fast)
5. Download starts automatically
6. Open in Excel, Numbers, or Google Sheets
```

**What's Included:**

**Sheet 1: Beneficiaries**
- All beneficiary information
- Columns: Name, CURP, Address, Status, Dates, etc.
- Formatted as table with filters

**Sheet 2: Statistics** (if available)
- Program summary
- Enrollment trends
- Status breakdown
- Budget utilization

**Sheet 3: Documents** (if available)
- Document checklist per beneficiary
- Upload status
- Missing documents report

#### Excel Data Structure

**Column Headers:**
| Column | Description |
|--------|-------------|
| Folio | Request number |
| Nombre | Full name |
| CURP | Citizen ID |
| Dirección | Complete address |
| Colonia | Neighborhood |
| Teléfono | Phone number |
| Email | Email address |
| Fecha Inscripción | Enrollment date |
| Estado | Current status |
| Monto | Benefit amount |

**Using Excel Export:**

1. **Filter Data:**
   - Click column header
   - Use Excel filter tools
   - Sort by any column

2. **Create Pivot Tables:**
   - Analyze by neighborhood
   - Count by status
   - Sum benefit amounts

3. **Generate Charts:**
   - Enrollment trends
   - Geographic distribution
   - Status breakdown

4. **Calculate Statistics:**
   - Average benefit amount
   - Approval rates
   - Processing times

### Export Best Practices

**Before Exporting:**
1. Apply necessary filters (date range, status)
2. Clean up data (ensure no pending edits)
3. Verify report parameters
4. Check available disk space

**File Management:**
- Name files descriptively: `becas_federal_dic2025.pdf`
- Store in organized folders by month/year
- Back up important reports
- Delete old exports regularly

**Data Security:**
- Exported files contain personal information
- Password-protect sensitive Excel files
- Don't email to unauthorized recipients
- Follow organizational data policies

**Large Exports:**
- Programs with 5,000+ beneficiaries: Use Excel (faster)
- Official reports: Use PDF (professional)
- Data analysis: Use Excel (manipulatable)
- Quick review: Use PDF (readable)

## Uploading Documents

Attach supporting documents to program requests.

### How to Upload Documents

[Screenshot: Document upload interface with drag-and-drop area]

```
1. Open request details
2. Click "Documents" tab
3. Click "Upload Document" button
4. Select document type from dropdown:
   - Official ID (INE/Passport)
   - Proof of address
   - Birth certificate
   - CURP certificate
   - School enrollment proof
   - Other
5. Click "Choose File" or drag file to upload area
6. Wait for upload to complete
7. Document appears in list
```

### Supported File Types

**Documents:**
- PDF (.pdf) - Preferred format
- Images: JPEG (.jpg), PNG (.png)
- Word (.doc, .docx)
- Excel (.xls, .xlsx) - For supporting data

**File Size Limits:**
- Maximum single file: 10 MB
- Recommended: Under 5 MB
- Compress large files before uploading

### Managing Uploaded Documents

**Document List Shows:**
- Document type
- File name
- Upload date
- Uploaded by (staff name)
- File size
- Actions (View, Download, Delete)

**Document Actions:**

**View Document:**
1. Click "View" icon (eye)
2. Document opens in new tab
3. PDFs display in browser
4. Images display full size

**Download Document:**
1. Click "Download" icon
2. File saves to your computer
3. Original filename preserved

**Delete Document:**
1. Click "Delete" icon (trash)
2. Confirmation dialog appears
3. Confirm deletion
4. Document removed from request

**Replace Document:**
1. Delete incorrect document
2. Upload corrected document
3. Select same document type
4. New file replaces old

### Document Verification Checklist

Before approving a request, verify:

- [ ] All required documents uploaded
- [ ] Documents are legible and complete
- [ ] Information matches request data
- [ ] Documents are current (not expired)
- [ ] Files open without errors
- [ ] No missing pages

## Common Program Management Tasks

### Task: Enroll New Beneficiary

```
1. Navigate to program details
2. Click "New Request"
3. Search/enter citizen info
4. Complete address form
5. Add school info (if applicable)
6. Review and submit
7. Note folio number
8. Upload required documents
9. Review and approve when ready
```

### Task: Process Pending Requests

```
1. Open program details
2. Filter by "Pendiente" status
3. Click first pending request
4. Review all information
5. Verify documents uploaded
6. Check eligibility
7. Change status to Aprobada/Negada
8. Add notes explaining decision
9. Move to next pending request
10. Repeat until queue cleared
```

### Task: Generate Monthly Report

```
1. Open program details
2. Apply date filter: This month
3. Apply status filter: Aprobada
4. Click "Export to PDF"
5. Include statistics: Yes
6. Generate and download
7. Review PDF
8. File in monthly reports folder
9. Share with supervisor if required
```

### Task: Find Beneficiaries in a Neighborhood

```
1. Open program details
2. Click map tab
3. Zoom to target neighborhood
4. Observe cluster markers
5. Click cluster to see individuals
6. Or use search: Type colonia name
7. List filters to show only that area
8. Export if needed for field visits
```

### Task: Update Multiple Beneficiary Statuses

```
1. Review list of beneficiaries
2. For each requiring status change:
3. Click "Edit" button
4. Update status with reason
5. Save changes
6. Move to next beneficiary
7. Verify all changes saved
8. Generate updated report
```

## Tips for Efficient Program Management

### Daily Workflow

**Morning Routine:**
1. Review pending requests count
2. Check for urgent approvals
3. Respond to citizen inquiries
4. Process documents uploaded overnight

**Processing Routine:**
1. Sort by submission date (oldest first)
2. Process in batches of 10-20
3. Take breaks between batches
4. Double-check approvals before confirming

**End of Day:**
1. Complete any started reviews
2. Update request notes
3. Generate daily activity summary
4. Plan next day's priorities

### Quality Assurance

**Before Approving:**
- Read entire request carefully
- Cross-check CURP with official ID
- Verify address exists in system
- Confirm document authenticity
- Check for duplicate enrollments

**Documentation:**
- Always add notes explaining decisions
- Document phone conversations with citizens
- Note any special circumstances
- Record follow-up requirements

### Communication

**With Citizens:**
- Provide folio number immediately
- Explain next steps clearly
- Set realistic timeline expectations
- Document all interactions

**With Team:**
- Share complex cases with supervisor
- Report system issues promptly
- Coordinate on high-volume days
- Share best practices

## Troubleshooting

### Map Not Loading

**Solutions:**
1. Refresh the page
2. Check internet connection
3. Allow location permissions if prompted
4. Try different browser
5. Clear browser cache

### PDF Export Fails

**Try:**
1. Reduce date range (fewer records)
2. Disable "Include Map" option
3. Check available disk space
4. Try Excel export instead
5. Contact IT if problem persists

### Can't Find Beneficiary in Search

**Verify:**
1. Spelling is correct
2. Try partial name search
3. Search by folio number instead
4. Check if wrong program selected
5. Verify beneficiary exists in system

### Upload Fails

**Check:**
1. File size under 10 MB
2. File type is supported
3. Internet connection stable
4. Browser not blocking pop-ups
5. Sufficient storage on server

## Next Steps

Now that you understand social programs:

- **[Geographic Data](05-geographic-data.md)**: Manage streets and neighborhoods
- **[QR Scanner](06-qr-scanner.md)**: Quick access to beneficiary info
- **[Reports](07-reports.md)**: Handle citizen reports

---

**Pro Tip**: Keep a spreadsheet of frequently used folio numbers for quick reference. Include citizen name, folio, program, and status for easy lookups during phone calls.
