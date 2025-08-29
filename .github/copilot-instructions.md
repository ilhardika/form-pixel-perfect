# Form Pixel Perfect - Copilot Instructions

## Project Architecture

This is a **pixel-perfect recreation** form. The project follows a **multi-page, multi-section** architecture where each page contains multiple vertical-labeled sections.

### Core Structure Pattern

```html
<div class="section-wrapper">
  <div class="vertical-label subject-label">SUBJECT</div>
  <div class="section-content">
    <table class="property-table">
      <!-- content -->
    </table>
  </div>
</div>
```

## Critical Design Constraints

### NO Column Borders Rule

- **Never** add `border-right` to `.table-cell` - this is the #1 visual requirement
- Tables use `border-collapse: collapse` with only row borders (`border-bottom`)

### Single-Row Layout Policy

- ALL elements (labels, inputs, checkboxes) must fit in ONE horizontal line per table row
- Fixed row height: `35px` with `table-layout: fixed`
- Use `white-space: nowrap` and `overflow: hidden` to prevent wrapping

### Custom Checkbox System

- Uses `appearance: none` with custom X mark (`✕`) when checked
- Size: `16px × 16px` with `transform: scale(0.8)`
- X styling: `12px font, translate(-50%, -50%)` for perfect centering

## Component Patterns

### Vertical Section Labels

- Color-coded: SUBJECT=`#bfbfbf`, ASSIGNMENT=`#c4c4c4`
- Uses `writing-mode: vertical-rl` with `text-orientation: mixed`
- Fixed width: `25px` with `border-right: 2px solid #000`

### Input Field Conventions

- Default: `100px` width, transparent background, `12px` font
- Special sizes: describe=`50px`, HOA=`40px`, full-width=`95% max 300px`
- All inputs: `border: none, background-color: transparent`

## Development Rules

### When Adding New Sections

1. Follow `section-wrapper` → `vertical-label` → `section-content` pattern
2. Each section gets unique label class with specific background color
3. Content layout may vary but maintain single-row principle

### When Modifying Layout

- Maintain `900px` fixed container width
- Keep `table-layout: fixed` for consistency
- Preserve `4px 4px` cell padding for compact spacing

### Font System (Roboto family)

- Title: `16px bold`
- Section labels: `14px bold`
- Cell labels: `14px normal`
- Input text: `12px`
- Base text: `12px`

## File Structure

- `index.html`: Main form structure
- `style.css`: Complete styling system (875 lines)
- `COPILOT_INSTRUCTIONS.md`: Project-specific documentation

## Testing Priorities

1. Verify no column borders visible
2. Confirm all content fits in single rows
3. Check X-mark checkboxes function correctly
4. Validate vertical SUBJECT label displays properly
