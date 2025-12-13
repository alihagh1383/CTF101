# Sort & Unique
 ### Unique
```bash
echo <Text> | awk '!x[$0]++'
```
# Regex 
### Find IP
```bash
grep -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' <File>
```
# Tools
## ssh log
### Login
```bash
grep -o '.\{1,\} Accepted password for .\{1,\}' <file- | awk '!x[$0]++'
```

## OTP
### Generate
```bash
oathtool --base32 --totp <OTPKEY> 
```