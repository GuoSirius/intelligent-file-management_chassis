keytool -genkey -alias ifm -keyalg RSA -keysize 2048 -validity 36500 -keystore ifm.keystore
keytool -list -v -keystore ifm.keystore
keytool -exportcert -keystore ifm.keystore | openssl dgst -md5

keytool -v -importkeystore -srcstoretype PKCS12 -srckeystore ifm.keystore -deststoretype JKS -destkeystore ifm.jks

keytool -importkeystore -srckeystore ifm.keystore -srcstoretype JKS -deststoretype PKCS12 -destkeystore ifm.p12
keytool -v -importkeystore -srckeystore ifm.p12 -srcstoretype PKCS12 -destkeystore ifm.jks -deststoretype JKS