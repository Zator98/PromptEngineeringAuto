# PromptEngineeringAuto




# ===== Windows updates first (Microsoft Update) =====
Set-ExecutionPolicy Bypass -Scope Process -Force

Install-PackageProvider -Name NuGet -Force -ErrorAction SilentlyContinue
Install-Module -Name PSWindowsUpdate -Force -AllowClobber
Import-Module PSWindowsUpdate
Install-WindowsUpdate -MicrosoftUpdate -AcceptAll -AutoReboot

# ===== Common runtimes many apps/games depend on =====
winget source update

# Visual C++ Redistributables (2015-2022)
winget install -e --id Microsoft.VCRedist.2015+.x64
winget install -e --id Microsoft.VCRedist.2015+.x86

# .NET Desktop Runtime (install if you run desktop apps built on .NET)
winget install -e --id Microsoft.DotNet.DesktopRuntime.8

# Microsoft Edge WebView2 Runtime (many modern apps embed web UI)
winget install -e --id Microsoft.EdgeWebView2Runtime

# Legacy DirectX runtime components for some older games/apps
winget install -e --id Microsoft.DirectX

# ===== Update all winget-managed apps =====
winget upgrade --all
