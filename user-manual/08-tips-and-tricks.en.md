# Tips and Tricks

This guide shares advanced techniques, keyboard shortcuts, efficient workflows, and troubleshooting solutions to help you master Gobify and work more productively.

## Keyboard Shortcuts

Master these shortcuts to navigate Gobify faster.

### Universal Shortcuts

These work throughout the entire Gobify system:

| Shortcut | Action | Context |
|----------|--------|---------|
| **Ctrl/Cmd + F** | Quick search on current page | Any page |
| **Ctrl/Cmd + K** | Global search | Opens search modal |
| **Esc** | Close modal/dialog | Active modal |
| **Tab** | Move to next field | Forms |
| **Shift + Tab** | Move to previous field | Forms |
| **Enter** | Submit form/confirm action | Forms, dialogs |
| **Ctrl/Cmd + S** | Save current form | Edit forms |
| **Ctrl/Cmd + R** | Refresh page | Any page |

### Navigation Shortcuts

| Shortcut | Action | Goes To |
|----------|--------|---------|
| **Alt + D** | Dashboard | Home screen |
| **Alt + C** | Ciudadanos | Citizens list |
| **Alt + P** | Programas Sociales | Programs list |
| **Alt + S** | Calles | Streets list |
| **Alt + N** | Colonias | Neighborhoods list |
| **Alt + Q** | Escanear QR | QR Scanner |
| **Alt + R** | Reportes | Reports list |

### Table Shortcuts

When viewing data tables:

| Shortcut | Action |
|----------|--------|
| **Arrow keys** | Navigate between rows |
| **Enter** | Open selected row |
| **Space** | Select/deselect row |
| **Ctrl/Cmd + A** | Select all rows |
| **Page Up/Down** | Scroll page |
| **Home** | First row |
| **End** | Last row |

### Search Shortcuts

While in search boxes:

| Shortcut | Action |
|----------|--------|
| **Down arrow** | Show search suggestions |
| **Enter** | Execute search |
| **Esc** | Clear search |
| **Ctrl/Cmd + A** | Select all search text |

**Note**: Exact shortcuts may vary by browser. Mac users use Cmd (⌘) instead of Ctrl.

## Efficient Workflows

Streamline common tasks with these optimized workflows.

### Morning Startup Routine

**5-Minute Daily Check (Recommended):**

```
1. Log in to Gobify
2. Review Dashboard KPIs (30 seconds)
   - Note any unusual changes
   - Identify priorities
3. Check pending reports (1 minute)
   - Filter: Assigned to Me + Pendiente
   - Count and prioritize
4. Review urgent items (2 minutes)
   - Priority: Urgente
   - Status: All except Cerrado
   - Address immediately or delegate
5. Check program enrollments awaiting approval (1.5 minutes)
   - Your assigned programs
   - Status: Pendiente
   - Plan processing time
```

### Batch Processing Citizens

When processing multiple citizens efficiently:

**Setup Phase (2 minutes):**
```
1. Open Ciudadanos section
2. Apply relevant filters
3. Customize columns to show only what you need
4. Set rows per page to 50
5. Sort by desired criteria
```

**Processing Phase (per citizen: 1-3 minutes):**
```
1. Right-click citizen → Open in new tab
2. Review details in new tab
3. Make necessary updates
4. Save and close tab
5. Return to main list (still at same position)
6. Move to next citizen
7. Repeat
```

**Why This Works:**
- Main list stays put
- No losing your place
- Faster navigation
- Parallel browsing possible

### Fast Program Request Creation

**Optimized for speed (5 minutes per request):**

```
1. Have citizen's documents ready before starting
2. Use second monitor or split screen:
   - Left: Physical documents or scans
   - Right: Gobify form
3. Fill form top-to-bottom without stopping
4. Use Tab to move between fields (not mouse)
5. Type-ahead search for streets/colonias
6. Keep common notes as text snippets (copy-paste)
7. Upload all documents at once (multi-select)
8. Review in one pass
9. Submit
```

**Time Savers:**
- Pre-scan all documents before starting form
- Verify CURP format before typing (avoid re-entry)
- Use text expansion for common phrases
- Keep frequently-used folios/references handy

### Multi-Report Processing

**Handle high volume efficiently:**

**Triage Phase (30 seconds per report):**
```
1. Filter: Status = Pendiente
2. Sort: Priority descending, then Date ascending
3. Skim each report:
   - Read title
   - Note type and category
   - Assess complexity
4. Quick assign to staff (including self)
5. Set initial priority
6. Move to next
```

**Processing Phase (variable time):**
```
1. Filter: Assigned to Me + En Revisión
2. Start with urgent
3. Handle quick-resolution items first (2-5 min each)
4. Schedule complex items for focused time
5. Update all statuses before break
6. Batch send citizen notifications
```

**End-of-Batch:**
```
1. Verify all reviewed reports have status update
2. Check no urgent items remain
3. Log count of processed reports
4. Clear filters
```

### Geographic Data Maintenance

**Weekly cleanup routine (15 minutes):**

```
1. Calles section:
   a. Sort by "Number of Uses" ascending
   b. Review streets with 0 uses
   c. Check for obvious duplicates
   d. Delete/merge as needed (2-3 minutes)

2. Colonias section:
   a. Similar review process
   b. Verify postal codes against official list
   c. Fix any discrepancies (2-3 minutes)

3. Quality check:
   a. Search for common misspellings
   b. Check inconsistent capitalization
   c. Standardize naming (5 minutes)

4. Documentation:
   a. Note changes made
   b. Update team on major corrections (2 minutes)
```

## Power User Techniques

Advanced methods for experienced users.

### Multi-Tab Workflow

**Use multiple tabs strategically:**

**Tab 1: Dashboard**
- Always open
- Quick reference for KPIs
- Return here between tasks

**Tab 2: Current Main Task**
- Citizens, Programs, Reports (whatever you're focused on)
- Keep filter/search active
- Your working tab

**Tab 3: Reference/Lookup**
- Open specific records
- Cross-reference information
- Close when done, reuse for next lookup

**Tab 4+: Background Tasks**
- Long exports generating
- PDF creation in progress
- Don't close until complete

### Search Operators

**Advanced search techniques:**

**Exact Match:**
```
Search: "Maria Garcia"
(With quotes: Exact phrase only)
```

**Wildcard:**
```
Search: Gar*
(Finds: Garcia, Garza, Garciela, etc.)
```

**Multiple Terms:**
```
Search: Garcia Centro Beca
(Finds records matching all three terms)
```

**Exclude Terms:**
```
Search: Garcia -Centro
(Finds Garcia but not in Centro)
```

**Field-Specific (if supported):**
```
Search: CURP:GAML850615
Search: Colonia:Centro
```

**Note**: Exact syntax depends on Gobify's search implementation. Test to see what works.

### Browser Features

**Leverage your browser:**

**Bookmarklets:**
Create bookmarklets for common actions:
- "My Pending Reports"
- "Urgent Items"
- "Today's Approvals"

**Bookmark Organization:**
```
Gobify/
├── Dashboard
├── My Searches/
│   ├── Pending Citizens - Centro
│   ├── My Assigned Reports
│   └── This Week's Enrollments
└── Admin/
    ├── Staff Management
    └── System Settings
```

**Browser Extensions:**
- Form autofill for common data entry
- Screenshot tools for documentation
- Password managers for security

**Developer Tools:**
- F12 → Network tab to diagnose slow loading
- Console for error messages
- Useful when reporting bugs

### Text Expansion

**Speed up repetitive typing:**

Create shortcuts that expand to full text:

**Examples:**
```
;addr → Calle Juárez #123, Col. Centro, C.P. 48300
;beca → Programa Federal de Becas para el Bienestar Benito Juárez
;recibido → Su reporte ha sido recibido y está siendo procesado.
;firma → Atentamente,\n[Your Name]\n[Your Title]\nDepartamento de Programas Sociales
```

**Tools:**
- Mac: Text Replacement (System Preferences)
- Windows: AutoHotkey, PhraseExpress
- Chrome/Firefox: Text expansion extensions

### Dual Monitor Setup

**Optimize two-screen workflow:**

**Left Monitor: Reference**
- Physical documents
- Scanned files
- Email with citizen correspondence
- Previous system (if migrating data)

**Right Monitor: Gobify**
- Main working area
- Forms and data entry
- Citizen records
- Program management

**Alternative Layout:**

**Left: Lists**
- Citizen table
- Report queue
- Program beneficiaries

**Right: Details**
- Individual records
- Forms
- Documents

### Template System

**Create templates for common scenarios:**

**Program Request Notes:**
```
Template: Standard Approval
"Documentación completa. Cumple requisitos de elegibilidad.
Aprobado para [PROGRAM_NAME]. Inicio de beneficios: [DATE].
Folio asignado: [FOLIO]."
```

**Report Responses:**
```
Template: More Info Needed
"Para continuar con su solicitud, favor de proporcionar:
1. [DOCUMENT_1]
2. [DOCUMENT_2]
3. [DOCUMENT_3]

Tiene [X] días hábiles para proporcionar la información."
```

**Citizen Communication:**
```
Template: Appointment Confirmation
"Estimado/a [NAME],
Su cita está confirmada para el [DATE] a las [TIME].
Favor de traer: [DOCUMENTS_LIST]
Ubicación: [ADDRESS]
Folio de referencia: [FOLIO]"
```

**Store templates in:**
- Separate document (copy-paste)
- Text expansion software
- Browser form filler
- Gobify notes section (if feature exists)

## Time-Saving Tips

Small improvements that add up to big time savings.

### Data Entry Optimization

**Before Starting:**
- Pre-organize all documents
- Verify all info is readable
- Check for missing data
- Have reference materials ready

**During Entry:**
- Use Tab, not mouse, to navigate fields
- Type ahead in dropdowns (don't scroll)
- Copy-paste CURP/folio numbers (avoid typos)
- Validate as you go (don't wait for form submission error)

**After Entry:**
- Quick visual scan before submitting
- Use browser back button if field error (not start over)
- Save work frequently

### Decision Trees for Common Scenarios

**When Citizen Calls About Program Status:**
```
1. Get folio number → Search in Programs
2. No folio? → Get CURP → Search in Citizens → See programs
3. Found?
   Yes → Give status update
   No → "Not in system, let's create request"
```

**When Processing Program Request:**
```
1. All docs uploaded?
   No → Change status to Pendiente + Note: "Missing [X]" + Notify citizen
   Yes → Continue

2. Meets eligibility?
   No → Change status to Negada + Note reason + Notify
   Yes → Continue

3. Budget available?
   No → Put on waitlist
   Yes → Approve + Assign folio + Notify
```

**When Handling Report:**
```
1. Urgent?
   Yes → Immediate action + Notify supervisor
   No → Continue

2. Simple resolution?
   Yes → Resolve immediately + Close
   No → Continue

3. My expertise?
   Yes → Assign to self + En Revisión
   No → Assign to appropriate staff
```

### Bulk Operations Strategy

**When to Use Bulk:**
- Exporting data for reports
- Printing mailing labels
- Sending notifications
- Updating similar records

**When to Process Individually:**
- Each case requires unique assessment
- High-value decisions
- Error risk is high
- Regulations require individual review

**Best Practice:**
- Start with small bulk test (5-10 items)
- Verify results correct
- Then proceed with larger bulk operation

## Common Mistakes to Avoid

Learn from others' errors.

### Data Entry Mistakes

**CURP Entry:**
- ❌ Don't type from memory (high error rate)
- ✓ Copy from official document
- ✓ Validate format before submitting

**Street/Colonia Selection:**
- ❌ Don't create duplicate if similar exists
- ✓ Search thoroughly first
- ✓ Check capitalization variations

**Status Changes:**
- ❌ Don't change without notes
- ✓ Always document why
- ✓ Include next steps

**Phone Numbers:**
- ❌ Don't omit area code
- ✓ Use consistent format: 322-123-4567
- ✓ Validate number before saving

### Workflow Mistakes

**Searching:**
- ❌ Don't scroll through thousands of records
- ✓ Use search and filters
- ✓ Be specific with search terms

**Multi-tasking:**
- ❌ Don't switch between 10 half-done tasks
- ✓ Finish one task before starting next
- ✓ Group similar tasks together

**Documentation:**
- ❌ Don't rely on memory ("I'll document it later")
- ✓ Add notes immediately
- ✓ Be specific and detailed

**Communication:**
- ❌ Don't leave citizens without updates
- ✓ Send acknowledgment within 24 hours
- ✓ Provide status updates regularly

### System Usage Mistakes

**Browser:**
- ❌ Don't use outdated browser
- ✓ Keep browser updated
- ✓ Use supported browsers

**Sessions:**
- ❌ Don't stay logged in overnight
- ✓ Log out when finished
- ✓ Close browser completely

**Data Security:**
- ❌ Don't email unencrypted exports with personal data
- ✓ Use secure file transfer
- ✓ Password-protect sensitive exports

**Exports:**
- ❌ Don't export entire database "just in case"
- ✓ Export only what you need
- ✓ Delete old exports regularly

## Troubleshooting Guide

Solutions to common problems.

### Performance Issues

**Slow Loading:**

**Possible Causes:**
- Large dataset (10,000+ records)
- Slow internet connection
- Browser cache full
- Too many tabs open
- Complex filters applied

**Solutions:**
```
1. Check internet speed (run speed test)
2. Close unnecessary browser tabs
3. Clear browser cache:
   - Chrome: Ctrl+Shift+Delete
   - Select "Cached images and files"
   - Clear
4. Apply filters to reduce dataset
5. Reduce rows per page
6. Try different browser
7. Restart computer if very slow
```

**Page Won't Load:**
```
1. Refresh page (F5)
2. Clear cache and hard reload (Ctrl+Shift+R)
3. Check internet connection
4. Try incognito/private mode
5. Try different browser
6. Check system status page (if available)
7. Contact IT support
```

**Export Hangs:**
```
1. Don't click export multiple times
2. Wait for progress indicator
3. If over 5 minutes with no progress:
   a. Note what you were exporting
   b. Close that tab
   c. Try smaller export (fewer records)
   d. Or try different format (CSV vs Excel)
```

### Data Issues

**Can't Find Citizen:**

**Checklist:**
```
1. Verify spelling of name
2. Try searching by CURP instead
3. Try partial search (just last name)
4. Clear all filters
5. Check if you're in right section (Ciudadanos)
6. Verify citizen actually exists in system
7. Check if citizen was archived/deleted
```

**Address Won't Save:**

**Common Causes:**
```
1. Required field missing
2. Street not in system → Add street first
3. Colonia not in system → Add colonia first
4. Postal code format wrong → Use 5 digits
5. Validation error → Read error message carefully
```

**Status Won't Change:**

**Possible Reasons:**
```
1. Missing required notes → Add explanation
2. Don't have permission → Check with supervisor
3. Invalid status transition → Some changes not allowed
4. Record locked by another user → Wait and retry
5. System rule preventing change → Review requirements
```

### Search Problems

**Search Returns Nothing:**
```
1. Check spelling
2. Try fewer letters (broader search)
3. Remove filters that might exclude results
4. Clear search and start over
5. Verify data actually exists
```

**Search Returns Too Much:**
```
1. Be more specific (add more terms)
2. Use quotes for exact phrase: "Maria Garcia"
3. Apply filters (date, status, type)
4. Search within specific field (CURP vs name)
```

**Search is Slow:**
```
1. Apply filters first to reduce dataset
2. Be more specific in search terms
3. Wait for initial load to complete before searching
4. Close other browser tabs
```

### Login and Access Issues

**Can't Log In:**
```
1. Verify username (email) is correct
2. Check password (watch for caps lock)
3. Clear browser cookies
4. Try password reset
5. Try different browser
6. Check with IT for account status
```

**Session Expires Frequently:**
```
1. Note how long you're active before expiry
2. Save work more frequently
3. Keep Dashboard open in background
4. Contact IT about session timeout settings
```

**Permission Denied:**
```
1. Verify you should have access to this feature
2. Check with supervisor about your role
3. You may need permission upgrade
4. Contact IT or system administrator
```

### Export and Print Issues

**Export File is Blank:**
```
1. Verify filter didn't exclude all records
2. Check file actually downloaded (look in Downloads)
3. Try opening with different program
4. Try exporting again
5. Try different export format
```

**PDF Won't Open:**
```
1. Ensure PDF download completed
2. Try different PDF reader
3. File may be corrupted → Export again
4. Check disk space on your device
```

**Excel File is Corrupted:**
```
1. Try CSV format instead
2. Reduce data size (fewer records)
3. Update Excel/spreadsheet software
4. Try opening in Google Sheets
```

## Best Practices Summary

### Daily Habits

**Start of Day:**
1. Check Dashboard for priorities
2. Review urgent items
3. Plan day's work
4. Clear yesterday's loose ends

**During Work:**
1. Document as you go
2. Save frequently
3. Update statuses in real-time
4. Communicate promptly

**End of Day:**
1. Update all in-progress items
2. Log out properly
3. Clear downloads folder
4. Plan tomorrow

### Quality Standards

**Data Entry:**
- Verify before submitting
- Use official sources
- Copy-paste when possible (reduces errors)
- Double-check CURP format

**Decision Making:**
- Review all relevant info
- Document reasoning
- Follow established procedures
- Escalate when unsure

**Communication:**
- Professional tone always
- Clear and concise
- Timely responses
- Document all interactions

**Security:**
- Log out when finished
- Lock screen when away
- Protect exports
- Report security concerns

## Getting More Help

### Built-in Help

**Look for:**
- Help icon (?) in interface
- Tooltips (hover over elements)
- Field descriptions
- Validation messages

### Documentation

**This Manual:**
- Bookmark for quick reference
- Use Ctrl+F to find topics
- Review relevant sections before complex tasks

**Official Resources:**
- System status page
- Release notes for new features
- Official communications from IT

### Human Support

**Colleagues:**
- Ask experienced users
- Share tips and tricks
- Collaborate on complex cases

**Supervisor:**
- Unclear processes
- Permission requests
- Policy questions
- Escalations

**IT Support:**
- Technical issues
- Login problems
- System errors
- Feature requests

### Training

**Continuing Education:**
- Attend system training sessions
- Review updated documentation
- Practice new features in test environment
- Share knowledge with team

## Productivity Metrics

Track your efficiency improvement:

### Personal Metrics

**Track Weekly:**
- Reports processed
- Citizens enrolled in programs
- Average processing time
- Error rate

**Benchmark Goals:**
```
Program Request Creation: 5-7 minutes
Report Triage: 30 seconds
Report Resolution:
  - Simple: 5-10 minutes
  - Medium: 30-60 minutes
  - Complex: 2-4 hours
```

**Improvement Over Time:**
```
Month 1: Baseline (learning)
Month 2: 20% faster
Month 3: 40% faster + fewer errors
Month 4+: Expert efficiency
```

## Quick Reference Card

**Print and keep handy:**

### Most-Used Shortcuts
```
Ctrl+K - Global Search
Alt+D - Dashboard
Alt+C - Citizens
Alt+P - Programs
Alt+R - Reports
Tab - Next field
Ctrl+S - Save
```

### Common Tasks Time Estimates
```
Citizen lookup: 30 sec
Program request: 5 min
Report triage: 30 sec
Report resolution: 5-60 min
Export generation: 10 sec - 2 min
```

### Emergency Contacts
```
IT Support: [Number]
Supervisor: [Number]
System Status: [URL]
```

### Pre-Flight Checklist
```
□ Browser updated?
□ Internet stable?
□ Documents organized?
□ Previous work saved?
□ Filters cleared?
□ Ready to focus?
```

---

**Remember**: Efficiency comes with practice. Don't try to implement all these tips at once. Pick 2-3 that seem most useful for your work, master those, then gradually add more techniques to your workflow.

**Final Tip**: Share your own discoveries! When you find a trick that saves time, tell your colleagues. The best tips often come from daily users solving real problems.
