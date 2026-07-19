# Verification Checklist

After editing `index.html`, run a syntax check on the embedded script.

PowerShell:

```powershell
$htmlPath = "<absolute path to index.html>"
$html = Get-Content -Raw -LiteralPath $htmlPath
$script = [regex]::Match($html, "<script>([\s\S]*)</script>").Groups[1].Value
[System.IO.File]::WriteAllText((Join-Path $env:TEMP "wind_proto_check.js"), $script)
node --check (Join-Path $env:TEMP "wind_proto_check.js")
```

## Browser Smoke Test

1. Open `index.html` in a browser.
2. Confirm the input controls appear in the left sidebar on desktop.
3. Scroll the page and confirm the sidebar remains visible.
4. Change exposure B, C, and D.
5. Confirm `Kz at h`, `qh`, and wall pressures update.
6. Change story count to 3.
7. Confirm the wall table renders story-based rows.
8. Toggle custom floor mode and edit heights.
9. Toggle Flat and Gable roof.
10. For gable slope `<= 10 deg`, confirm `qh` uses eave height.
11. For gable slope `> 10 deg`, confirm `qh` uses mean roof height.
12. Toggle Gable Normal and Parallel orientation.
13. Confirm the SVG preview updates.
14. Confirm fixed Building length and Building width labels remain stable.
15. Confirm derived ASCE `L` and `B` update with wind direction.
16. Confirm leeward wall `Cp` changes when `L / B` crosses or interpolates between 1, 2, and 4.
17. Confirm gable roof `Cp` values change when roof slope, `h/L`, and ridge orientation change.
18. Confirm the roof table shows governing `Cp` and net pressure for each roof row.
19. Confirm the design equation block remains readable.
20. Confirm there are no console errors.
