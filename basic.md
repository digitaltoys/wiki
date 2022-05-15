### Teamming (Bonding) - 랜카드 2개로 대역폭 늘리기
```powershell
Get-NetAdater

new-netswitchteam -Name "Wi-Fi Team" -TeamMembers "이더넷", "Wi-Fi 3"
```

### Teamming 삭제
```powershell
Remove-NetSwitchTeam -name "Wi-Fi Team"
```
