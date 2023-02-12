
$processes = Get-Process | Where-Object { $_.Modules | Where-Object { $_.ModuleName -like "*.dll" } }


foreach ($process in $processes)
{
   
    Write-Host "Process: $($process.ProcessName)"

   
    $subprocesses = Get-WmiObject -Class Win32_Process -Filter "ParentProcessId = $($process.Id)"

    foreach ($subprocess in $subprocesses)
    {
        Write-Host "  Subprocess: $($subprocess.Name)"
    }
}
