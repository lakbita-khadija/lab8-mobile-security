# Résultats Yaazhini — InsecureBankv2

## Vulnérabilités
- HIGH (36)   : Insecure Communication
- MEDIUM (13) : Debuggable, Backup, Export Providers/Receivers, Random Values, SHA1withRSA, MD5, SHA-1
- LOW (3)     : Javascript in WebView
- WARNING(13) : Android External Storage
- INFO (19)   : Missing Copy/Paste Protection, Missing Screenshot Protection

## Permissions critiques
- SEND_SMS, READ_PROFILE, READ_PHONE_STATE, READ_CALL_LOG

## Activities sensibles
- LoginActivity, DoLogin, DoTransfer, ChangePassword, FilePrefActivity

## Receivers dangereux
- MyBroadCastReceiver (exported=true) 🔴

## URLs HTTP non chiffrées
- http://goo.gl/8Rd3yj
- http://goo.gl/naFqQk
- http://www.google-analytics.com
- http://plus.google.com/
- http://www.google.com
