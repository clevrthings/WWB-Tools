# WWB Tools

## Live Website

**https://wwb.clevrthings.com**

WWB Tools is a website for wireless audio users who work with **Shure Wireless Workbench (WWB)**.
It provides two practical tools:

1. **BIPT Inclusion Lists**: download ready-to-import `.ils` files.
2. **Frequency Exclusion Builder**: upload an image and generate exclusion files (`.csv`, `.txt`, `.json`, `.fxl`).

## Tool 1: BIPT Inclusion Lists

On the homepage, you can download the latest WWB inclusion list files based on official BIPT zone documents.

### What this is for

- Quickly load valid frequency ranges into WWB.
- Reduce manual data entry.
- Keep your coordination workflow up to date.

### How to use

1. Open `https://wwb.clevrthings.com`.
2. In **BIPT Inclusion Lists**, click the `.ils` file you want.
3. Open **Frequency Coordination** in WWB.
4. Go to **Spectrum**.
5. Enable `Account for user groups when calculating frequencies`.
6. Go to **List > Manage > Custom > Import Groups**.
7. Select the downloaded `.ils` file.

## Tool 2: Frequency Exclusion Builder

Open the builder at:
`https://wwb.clevrthings.com/exclusion-builder/`

Upload a photo or screenshot (for example, of frequency notes, venue sheets, or coordination docs).  
The tool extracts frequencies and ranges, then generates files you can use in your WWB workflow.

### What this is for

- Convert visual frequency lists into usable files.
- Generate WWB exclusion data faster.
- Export in multiple formats for different workflows.

### How to use

1. Open the Exclusion Builder page.
2. Upload an image.
3. Optionally add extra instructions in the prompt box.
4. Click **Process**.
5. Download the generated files you need.

## Output Files

The Exclusion Builder can generate:

- `.csv`: easy to review in spreadsheet tools.
- `.txt`: plain text list.
- `.json`: structured model output.
- `.fxl`: exclusion format for WWB workflows.

## Notes

- The BIPT list is based on publicly available BIPT source documents.
- Always verify final coordination choices in your real-world RF context.
