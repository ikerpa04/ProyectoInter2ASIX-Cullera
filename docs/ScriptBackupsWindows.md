```
$origen = "\\truenas\cullera-NAS"

$fecha = Get-Date -Format "dd-MM-yyyy"

$backup = "CC_$fecha"

$destino = $args[0]

if ($destino -eq $null) {
    
    $destino = Read-Host "Donde quieres guardar?"
    
    Copy-Item -Path $origen -Destination "$destino\$backup" -Recurse
    pause
}

else {
    Copy-Item -Path $origen -Destination "$destino\$backup" -Recurse
}
```