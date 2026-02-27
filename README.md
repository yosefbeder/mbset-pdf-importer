# mbset-pdf-importer

$tags = %TAGS (source + additional info, eg, "Exams, Final 2025")%
$subject = %SUBJECT (optional)%
$lecture = %LECTURE (optional)%
$year = %YEAR (optional)%

You will receive a list of questions (MCQs or written) either as a PDF file or plain text. Your task is to extract and convert these questions into a specific CSV format.

Generate a valid CSV inside a code block with the following exact header row: Cas,Text,A,B,C,D,E,F,G,H,Correct,Year,subcategoryName,Tag,Type,tagSuggere,EXP

Cas, Text, Options (A, B, ...etc), and EXP are all markdown.

For each question, map the extracted content to the columns as follows:

- Cas: The shared clinical scenario or context. If a clinical case or scenario has multiple sub-questions (e.g., A, B, C), you MUST split them into separate CSV rows. Repeat the exact shared context in the `Cas` column for every row that belongs to it. However, if a clinical case or context applies to ONLY ONE question, leave the `Cas` column completely blank.

- Text: The specific question content without extra spaces. Remove any question number/letter prefixes (like 'A.', 'B.', '1.'). For multi-part questions, place the individual sub-question here (do not include the shared context). If a clinical case or context applies to ONLY ONE question, place the entire case context along with the question text into this column.

- A through H: The answer options. Remove any prefixes such as 'a)', 'b)', '1.', etc., from the options while preserving their original order. Place the first option in A, the second in B, and so on. (A and B are required; leave C-H blank if unused).

- Correct: The correct answer letter(s) corresponding to the correct option(s) (e.g., A, B, or A,C). Determine the correct answer yourself based on your knowledge base.

- subcategoryName = $lecture

- Tag = $tags

- tagSuggere = $subject

- type = "QCS" (for MCQs) or "QROC" (for written)

- year = $year

- Exp = answer of written question (either from the file or generate it yourself). For MCQs at the explanation in the source only if present.

Ensure the CSV is properly formatted and escaped (e.g., wrap text containing commas or newlines in double quotes). Aggregate all questions into this single CSV block, preserving the original question sequence with no omissions. Don't include "[cite...]".

At the very end of your response, outside of the CSV code block, output the total number of questions processed.
