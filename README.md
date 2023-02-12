# Powershell-shows-all-dll-process-subprocess
Get-Process retrieves a list of all processes running on the system.

Where-Object is used to filter this list of processes, so that only processes with DLL modules are included. This is done by checking the ModuleName property of each process's Modules collection, and only including processes where at least one module's name matches the pattern "*.dll".

The filtered list of DLL processes is stored in the $processes variable.

The foreach loop iterates through each process in the $processes list.

Within the loop, the process name is written to the console using Write-Host and the string "Process: $($process.ProcessName)".

The next step is to retrieve a list of subprocesses for the current process. This is done using Get-WmiObject to query the Win32_Process WMI class, and the -Filter parameter to specify that only processes whose parent process ID matches the ID of the current process should be included. The filtered list of subprocesses is stored in the $subprocesses variable.

Another foreach loop is used to iterate through each subprocess in the $subprocesses list.

Within this inner loop, the subprocess name is written to the console using Write-Host and the string " Subprocess: $($subprocess.Name)".

The script will repeat the process of retrieving subprocesses and displaying their names for each DLL process in the $processes list, until all processes have been processed

