# Script: Rust_Audio.Renamer

Renames audio files in batch, organizing them based on preferred naming conventions for better readability and consistency.

<br/>

## Points:

- [Audio File Extensions](#audio-file-extensions)
- [Naming Formats](#naming-formats)
- [Processing Rules](#processing-rules)
  - [Case Handling](#case-handling)
  - [Edge Case Handling](#edge-case-handling)
- [Interactive CLI Features](#interactive-cli-features)
- [Additional Features](#additional-features)

<br/>

## Audio File Extensions:

- `mp3`
- `m4a`
- `flac`
- `alac`
- `wav`
- `aiff`

<br/>

## Naming Formats

1. For albums with multiple tracks :

   - Format: `01. Track Name`
     - Notes: Each track should have a 2-digit track number ( i.e., `01` - `99` ).

2. For single-track albums or standalone tracks :

   - Format: `Artist - Track Name`

<br/>

## Processing Rules

### Case Handling:

1. File Extension :

   - Do not overwrite or alter file extensions.

2. Track Numbers :

   - Ensure track numbers are padded to two digits (i.e., `01`, `09`, `10`).

3. String Formatting Adjustments :

   - Remove unnecessary suffixes such as `(Original Mix)`.
   - Replace underscores `_` with spaces:
     - If multiple underscores are detected, treat them as placeholders for spaces.
     - Retain single underscores, as they are typically named in the artist or track name.

4. Preserve Metadata :

   - The script should rename files without altering their metadata.

<br/>

### Edge Case Handling:

1. Files Without Track Numbers :

   - Assume the file belongs to a single-track album or standalone release and apply the `Artist - Track Name` format.

2. Files with Inconsistent Naming Conventions :

   - Attempt to parse names intelligently, falling back to a log or user review if parsing fails.

3. Files with Special Characters :

   - Retain characters, unless they conflict with file system rules.

<br/>

## Interactive CLI Features:

- Directory Selection :

  - Prompts the user to select a directory or subdirectory for processing.
  - Confirms the selected directory before proceeding.

- File Count Summary :

  - Displays the total number of directories and files to be renamed.

- Custom Options :

  - Asks whether to retain the `(Original Mix)` suffix.

- Confirmation Step :

  - Summarizes proposed changes and asks for final confirmation before execution.

<br/>

## Additional Features:

1. Logging :

   - Maintain a log of renamed files for traceability.

2. Dry Run Mode :

   - Allow the user to preview changes without executing the actual file renaming.

3. Recursive Directory Support :

   - Option to process files in subdirectories.
