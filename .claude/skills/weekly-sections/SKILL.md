---
name: 這週生命讀經分段
description: Read text file (.txt or .md) from ./text directory, divide content into 7 daily portions, and overwrite the original file
---

# 這週生命讀經分段

This skill reads a text file from the `./text` directory, divides the content evenly into 7 daily portions for weekly reading, and **overwrites the original file** with the formatted result.

## How It Works

1. **Validation**: Check that `./text` directory contains exactly ONE text file (.txt or .md)
2. **Read**: Load the content from the text file
3. **Parse**: Split content into paragraphs (separated by empty lines)
4. **Distribute**: Evenly distribute paragraphs across 7 days by **character count** without breaking any paragraph
5. **Write**: Overwrite the original file with the formatted content

## Validation Rules

- The `./text` directory must exist
- There must be exactly ONE file in the directory
- The file must have a `.txt` or `.md` extension
- If any condition fails, terminate and return the reason

## Output Format

```
[週一]
段落內容...

[週二]
段落內容...

[週三]
段落內容...

[週四]
段落內容...

[週五]
段落內容...

[週六]
段落內容...

[主日]
段落內容...
```

## Important Rules

- **CRITICAL: Never modify original content**: Do NOT change any punctuation marks, characters, whitespace, or empty lines from the original file. Only insert day headers ([週一] to [主日]) before content sections.
- **CRITICAL: Preserve ALL original punctuation**: Keep all Chinese full-width punctuation marks (，。；：「」『』（）) exactly as they are in the original file. Do NOT convert them to half-width punctuation (,.;:"'()).
- **Never split a paragraph**: Each paragraph must remain complete and assigned to a single day
- **Strictly maintain original order**: Paragraphs must be distributed sequentially, preserving the exact order from the source file
- **Distribute by character count**: Aim for approximately equal character count per day (not paragraph count)
- **Preserve empty lines between paragraphs**: Keep one empty line between each paragraph in the output; do NOT remove empty lines
- Paragraphs are defined as text blocks separated by one or more empty lines
- Distribution should be as even as possible while respecting paragraph boundaries and original order

## Usage

Run this skill to automatically divide your weekly reading material.

## Steps to Execute

1. List files in `./text` directory
2. Validate: exactly 1 file and must be `.txt` or `.md`
3. Read the file content
4. Split into paragraphs (by empty lines)
5. Calculate target character count per day (total_chars / 7)
6. Sequentially assign paragraphs to each day:
   - Maintain strict original order
   - Aim for ~equal character count per day
   - Keep paragraphs whole and intact
7. Format result with day headers ([週一] to [主日])
8. **Overwrite the original file** with the formatted content

## Error Messages

- "錯誤：./text 目錄不存在" - Directory does not exist
- "錯誤：./text 目錄中沒有檔案" - No files found
- "錯誤：./text 目錄中有多個檔案，只能有一個" - Multiple files found
- "錯誤：檔案必須是 .txt 或 .md 格式" - File is not a .txt or .md file
