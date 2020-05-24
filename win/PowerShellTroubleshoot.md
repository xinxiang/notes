# "...The file is not digitally signed.  The script will not be executed on the system..."

PS C:> Set-ExecutionPolicy -Scope Process Unrestricted

Or, replace unrestricted with "Restricted", "AllSigned", or "RemoteSigned"

This happens to downloaded scripts. Locally created PS script does not get this error. Therefore, create a new ps file, copy and paste the downloaded codes the into the new file. 

