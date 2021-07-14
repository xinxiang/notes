# Automate CSR and Key Generation
* https://www.digicert.com/kb/ssl-support/openssl-quick-reference-guide.htm
* https://unix.stackexchange.com/questions/245778/automate-textual-input-to-a-command-from-a-bash-script

```
#!/bin/sh

HOST=$1
CN=$2
EMAIL=$3
TODAY=`date -d today '+%Y-%m-%d'`
mkdir -p $HOST/$TODAY
umask 277

CSR="$HOST/$TODAY/$HOST.csr"
KEY="$HOST/$TODAY/$HOST.key"


# https://unix.stackexchange.com/questions/245778/automate-textual-input-to-a-command-from-a-bash-script
# certificate details for herenow script (configurable)
COUNTRY="CA"                # 2 letter country-code
STATE="Ontario"            # state or province name
LOCALITY="Toronto"        # Locality Name (e.g. city)
ORGNAME="Governing Council of the University of Toronto" # Organization Name (eg, company)
ORGUNIT="Information Security & Enterprise Architecture" # Organizational Unit Name (eg. section)
CN="$CN"     # Common Name (eg, your name or your server's hostname)
EMAIL="$EMAIL"    # certificate's email address
# optional extra details
CHALLENGE=""                # challenge password
COMPANY=""                  # company name

DAYS="-days 365"

# create the certificate request
cat <<__EOF__ | openssl req -new $DAYS -nodes -newkey rsa:4096 -keyout $KEY -out $CSR 
$COUNTRY
$STATE
$LOCALITY
$ORGNAME
$ORGUNIT
$CN
$EMAIL
$CHALLENGE
$COMPANY
__EOF__

# verify csr
openssl req -text -in $CSR -noout -verify
```
