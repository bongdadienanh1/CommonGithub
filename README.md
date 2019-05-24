keytool -genkey -keyalg RSA -alias wbtoken -keystore wbTcbToken.jks -storepass admin@123 -validity 365 -keysize 2048
keytool -list -v -keystore wbTcbToken.jks

keytool -importkeystore -srckeystore wbTcbToken.jks -destkeystore wbTcbToken.jks -deststoretype pkcs12


Generate a Java keystore and key pair
B1: keytool -genkey  -alias wbtoken -keyalg RSA -keystore wbTcbToken.jks -storepass admin@123 -validity 365 -keysize 2048
Generate a certificate signing reuest (CSR) for an exiting java keystore
B2: keytool -certreq -alias wbtoken -keystore wbTcbToken.jks -file wbtoken.csr
Check the keystore
B3: keytool -list -v -keystore wbTcbToken.jks
import a root or intermediate CA certificate to an exiting Java keystore
B4: keytool -import -trustcacerts -alias wbtoken -file wbtoken.crt -keystore wbTcbToken.jks
export the certificate from the trustore
keytool -exportcert -alias root -file file.cer -keystore ./keystore.jks
check the standalone certificate
keytool -printcert -v -file ca.crt
delete the certificate from the keystore
keytool -delete -alias mydomain -keystore keystore.jks
change keystore password
keytool -storepasswd -new new_storepass -keystore keystore.jks
set OPENSSL_CONF=C:\Apache24\conf\openssl.cnf
openssl req -config C:\Apache24\conf\openssl.cnf -new -out C:\Apache24\conf\wbtoken.csr -keyout C:\Apache24\conf\wbtoken.pem

openssl rsa -in C:\Apache24\conf\wbtoken.pem -out C:\Apache24\conf\wbtoken.key

openssl x509 -req -signkey C:\Apache24\conf\wbtoken.key -days 1024 -in C:\Apache24\conf\wbtoken.csr -out C:\Apache24\conf\wbtoken.crt

Url
https://www.youtube.com/watch?v=Zdl68h_N2lc
https://tutorials.webencyclop.com/blog/install-ssl-on-windows-localhost-wamp-http-ssl-https/?utm_source=youtube
https://stackoverflow.com/questions/11308077/generate-key-and-certificate-using-keytool
https://stackoverflow.com/questions/35947354/how-to-create-a-certificate-with-keytool/46960957#46960957
http://www.thinkplexx.com/learn/howto/security/tools/understanding-java-keytool-working-with-crt-files-fixing-certificate-problems
https://aboutssl.org/how-to-create-a-self-signed-certificate-using-java-keytool/
https://www.sslshopper.com/article-how-to-create-a-self-signed-certificate-using-java-keytool.html
https://www.namecheap.com/support/knowledgebase/article.aspx/9821/38/apache-redirect-to-https
https://stackoverflow.com/questions/991758/how-to-get-pem-file-from-key-and-crt-files
https://gist.github.com/stevenhaddox/1501893
