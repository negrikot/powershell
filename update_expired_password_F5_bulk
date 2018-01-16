# update 100 users with pattern user_1, user_2 etc.
$userTemplate = "user_"
$currentPassword = "password_current"
$newPassword = "password_new"

for ($i=31; $i -le 100; $i++)
{
    $userName = "$userTemplate$i"

    # open target url in IE - F5(or TMG) window would be opened depends on your environment
    $ie = New-Object -ComObject InternetExplorer.Application
    $url = 'https://url.example.com'
    $ie.Visible = $true
    $ie.Navigate($url)
    Start-Sleep 5

    # try existing credentials
    $ie.Document.getElementById('username').value = $userName
    $ie.Document.getElementById('password').value = $currentPassword
    $submit = $ie.Document.getElementsByTagName('Input') | ? {$_.Type -eq "Submit"}
    $submit.click()
    Start-Sleep 5

    # set new credentials
    $ie.Document.getElementById('input_1').value = $newPassword
    $ie.Document.getElementById('input_2').value = $newPassword
    $submit = $ie.Document.getElementsByTagName('Input') | ? {$_.Type -eq "Submit"}
    $submit.click()
    Start-Sleep 30

    # clear IE cookies
    RunDll32.exe InetCpl.cpl,ClearMyTracksByProcess 2

    Start-Sleep 10

    # close IE
    $ie.Quit()

    Start-Sleep 5

    # log message
    Write-Host "User $userName updated" -ForegroundColor Green
}
