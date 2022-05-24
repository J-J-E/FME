This project contains an FME® workspace to assist with the long-term maintenance of complex production environments with many FME Workspaces. 

***

# FME Version Requirements
- Tested and working with FME® V 2021.1+

# Instructions
1. Download WorkspaceExaminer.fmw from files
2. Open Workspace by double-clicking (or right-clicking and choosing FME® version)
3. Thoroughly read parameter descriptions outlined below!!

# Parameter Descriptions
### Parameters are grouped into multiple expandable categories as mapped below

## Section 1 - Reporting Parameters
1. Select a Workspace Folder - The root folder to begin analysis/search
2. Include workspaces in subfolders - Enable recursion into subfolders of the root folder
3. Enter directories to ignore separated by a pipe character (|) * - allows user to specify keywords of directories/files to ignore
4. Enter specific directory/workspace to target** - allows user to specify keywords of directories/files of interest
5. Select a folder to write HTML Reports - defaults to `$(FME_MF_DIR)WorkspaceReports` which creates a folder called "WorkspaceReports" inside the directory where the FME file is run from

&ast;Regex Clause - Leave blank to not filter out any directories, use | when adding multiple filters, this is case insensitive (BoUnDaRiEs = boundaries = BOUNDAIRES)  
** To read everything,leave filter blank.   
EX1: To find all workspaces containing string "GDM" replace .* with GDM  
EX2: to read a single workspace, supply the name of it such as Example1.fmw

***

## Section 2 - Workspace Statistics
1. Select Report Type(s)* - Allows the user to specify report type  
    - Overall  
    - Grouped by Directory  
    - Grouped by Directory / Workspace
2. Genericize Transformers to Reader/Writer/Transformer** - Boolean  

&ast; One of more options can be chosen and will be generated independently of each other  
** If this option is not checked, Specific FME Transformer names will be used. This could lead to a very LARGE report.


***

## Section 3 - Transformers
1. List Customer Transformers? - Boolean
2. Enter string to search - Optional; keyword or string used in regex query. Allows user to identify workspaces containing transformers LIKE _TransformerName_
3. Identify Upgradeable Transformers - Boolean  
    - This also identifies when a transformer's embedded description is saved and has upgraded transformers inside it. If you don't see the transformer in the workspace, check the transformer gallery.     
    - **This also lists whether a transformer is embedded or linked!**



***

## Section 4 - Workspace History / Description
1. Generate Workspace History* - Boolean; pulls history from Workspace Parameters history (Format can vary depending on html/markdown usage)
2. Generate Workspace Description(Overview)* - Boolean; pulls overview from Workspace Parameters Description (Format can vary depending on html/markdown usage)

&ast;  Will list workspace History/Descriptions (if they have one) and report on workspaces missing History/Descriptions

***

## Section 5 - File Path Types Reporting
1. Report Path Types - Boolean; Identifies Local Paths, UNC Paths, URLs, and FME® Parameters
2. Include Paths using FME® Parameters - Boolean
3. Check Existence of Input Datasets* - Boolean
4. Check Existence of Output Datasets* - Boolean

&ast; FME Parameters and URL's will never be checked for existence. Less useful to check output datasets as these can be moved or deleted after process run

***

## Section 6 - Regex Searching
&ast; supplying a string to search will limit the output to only matching features. Blank will pass all features through
- Multiple values can searched for together by separating with the pipe character (|)  
- do not include leading/trailing spaces unless the space is desired in the search
### Section 6.1 - Input/Outputs
1. Search for Feature Type Inputs - Boolean
2. Search for Feature Type Outputs - Boolean
3. Enter string to search - String; Optional  
  - I found this mostly useful when reading/writing to database. Allows user to search for all readers/writers/featurereaders/featurewriters that write to specific database tables

### Section 6.2 - Attribute Names
1. Search in Readers - Boolean
2. Search in Writers - Boolean
3. Search in Transformers - Boolean
4. Enter string to search - String; Optional  
  - Allows user to search for all Readers/Writers/Transformers that contain a specific Attribute (column) name

### Section 6.3 - Published Parameters
1. Search in Parameter Name - Boolean
2. Search in Parameter Default Value - Boolean
3. Enter string to search - String; Optional   
  - Mostly useful when attempting to identify where a certain parameter is used / upgrading old parameter names to new standard names
