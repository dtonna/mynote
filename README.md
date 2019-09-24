Converting PKCS#12 certificate into PEM using OpenSSL
openssl pkcs12 -in path.p12 -out newfile.crt.pem -clcerts -nokeys
openssl pkcs12 -in path.p12 -out newfile.key.pem -nocerts -nodes
Generate RSA private key with certificate in a single command

openssl req -x509 -newkey rsa:4096 -sha256 -keyout example.key -out example.crt -subj "/CN=example.com" -days 3650 -passout pass:foobar
Generate Certificate Signing Request (CSR) from private key with passphrase

openssl x509 -x509toreq -in example.crt -out example.csr -signkey example.key -passin pass:foobar
Generate RSA private key (2048 bit)

openssl genrsa -out private.pem 2048
Generate a Certificate Signing Request (CSR)

openssl req -sha256 -new -key private.pem -out csr.pem
Generate RSA private key (2048 bit) and a Certificate Signing Request (CSR) with a single command

openssl req -new -newkey rsa:2048 -nodes -keyout server.key -out server.csr
Convert private key to PEM format

openssl rsa -in server.key -outform PEM -out server.pem
Generate a self-signed certificate that is valid for a year with sha256 hash

openssl x509 -req -sha256 -days 365 -in csr.pem -signkey private.pem -out certificate.pem
View details of a RSA private key

openssl rsa -in private.pem -text -noout
View details of a CSR

openssl req -in csr.pem -text -noout
View details of a Certificate

openssl x509 -in certificate.pem -text -noout
View details of a Certificate in DER format

openssl x509 -inform der -in certificate.cer -text -noout
Convert a DER file (.crt .cer .der) to PEM

openssl x509 -inform der -in certificate.cer -out certificate.pem
Convert a PEM file to DER

openssl x509 -outform der -in certificate.pem -out certificate.cer
