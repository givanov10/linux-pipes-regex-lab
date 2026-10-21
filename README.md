# linux-pipes-regex-lab

Linux Challenge Lab D: Pipes, Redirection, and REGEX


Project Overview

This project extracts, filters, and formats a clean list of unique service names recognized by the Linux system. The source data is pulled from the system configuration file located at /etc/services.
The entire operation is performed efficiently in a single line of bash code using input/output redirection and piping, without creating any temporary intermediary files.

The Solution Command

bash
egrep -v '^#' /etc/services | cut -f1 | egrep -v '^$' | sort -u > uniqueservices.txt
Use code with caution.

How It Works (Step-by-Step Breakdown)

The command forms a pipeline where the output of each tool is passed directly to the next:
• egrep -v '^#' /etc/services
Uses Extended Regular Expressions (egrep) to scan the file. The ^# pattern matches lines starting with a hash symbol (comments). The -v flag inverts the match, effectively removing all comment lines while preserving actual data.
• | cut -f1
Takes the cleaned rows and cuts out only the first column (-f1). Since fields in /etc/services are naturally separated by tabs, this isolates the service names and discards port numbers and protocols.
• | egrep -v '^$'
Filters out any remaining blank lines. The pattern ^$ represents a line where the start (^) immediately meets the end ($), meaning there is no content inside it.
• | sort -u
Sorts the extracted service names alphabetically and automatically removes all duplicate entries (-u for unique) from the list.
• > uniqueservices.txt
Redirects the final pristine stream of data out of the terminal and into a new file named uniqueservices.txt in the current working directory.

Output

The final output is a perfectly sorted, comment-free list of unique background services recognized by the Linux image.
