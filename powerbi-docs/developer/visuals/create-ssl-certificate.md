---
title: Opret SSL-certifikater til Power BI-visualiseringer
description: Få mere at vide om, hvordan du genererer SSL-certifikater ved hjælp af Power BI Visual Tools i Windows, Mac eller Linux eller manuelt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/08/2020
ms.openlocfilehash: 8eeca13acb1568a671618dca75d20cb7667b538b
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2020
ms.locfileid: "91747545"
---
# <a name="create-an-ssl-certificate"></a>Opret et SSL-certifikat

I denne artikel beskrives det, hvordan du opretter og installerer SSL-certifikater (Secure Sockets Layer) til Power BI-visualiseringer.

I forbindelse med Windows-, macOS X- og Linux-procedurerne skal **PBIVIZ**-pakken Power BI Visual Tools være installeret. Du kan finde flere oplysninger under [Konfigurer udviklermiljøet](./custom-visual-develop-tutorial.md#setting-up-the-developer-environment). 

## <a name="create-a-certificate-on-windows"></a>Opret et certifikat i Windows

Kør følgende kommando for at generere certifikatet ved hjælp af PowerShell cmdlet'en `New-SelfSignedCertificate` i Windows 8 eller nyere:

```powershell
pbiviz --install-cert
```

I Windows 7 kræver `pbiviz`-værktøjet, at OpenSSL-værktøjet er tilgængeligt fra kommandolinjen. Du installerer OpenSSL ved at gå til [OpenSSL](https://www.openssl.org) eller [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries).

Du kan finde flere oplysninger og instruktioner til installation af et certifikat under [Opret og installér et certifikat til Windows](./custom-visual-develop-tutorial.md#windows).

## <a name="create-a-certificate-on-macos-x"></a>Opret et certifikat i macOS X

Værktøjet OpenSSL er almindeligvis tilgængeligt i operativsystemet macOS X.

Du kan også installere OpenSSL-værktøjet ved at køre en af følgende kommandoer:

- Fra *Brew*-pakkestyring:
  
  ```cmd
  brew install openssl
  brew link openssl --force
  ```

- Ved hjælp af *MacPorts*:
  
  ```cmd
  sudo port install openssl
  ```

Når du har installeret OpenSSL-værktøjet, skal du køre følgende kommando for at oprette et nyt certifikat:

```cmd
pbiviz --install-cert
```

Du kan finde flere oplysninger og instruktioner under [Opret og installér et certifikat til OS X](./custom-visual-develop-tutorial.md#osx).

## <a name="create-a-certificate-on-linux"></a>Opret et certifikat i Linux

OpenSSL-værktøjet er almindeligvis tilgængeligt i operativsystemet Linux.

Før du starter, skal du køre følgende kommandoer for at sikre, at `openssl` og `certutil` er installeret:

```sh
which openssl
which certutil
```

Hvis `openssl` og `certutil` ikke er installeret, skal du installere værktøjerne `openssl` og `libnss3`.

### <a name="create-the-ssl-configuration-file"></a>Opret SSL-konfigurationsfilen

Opret en fil, der hedder */tmp/openssl.cnf*, som indeholder følgende tekst:

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[ alt_names ]
DNS.1=localhost
```

### <a name="generate-root-certificate-authority"></a>Generer rodcertificeringsnøglecenter

Hvis du vil generere et rodcertificeringsnøglecenter til at signere lokale certifikater, skal du køre følgende kommandoer:

```sh
touch $HOME/.rnd
openssl req -x509 -nodes -new -sha256 -days 1024 -newkey rsa:2048 -keyout /tmp/local-root-ca.key -out /tmp/local-root-ca.pem -subj "/C=US/CN=Local Root CA/O=Local Root CA"
openssl x509 -outform pem -in /tmp/local-root-ca.pem -out /tmp/local-root-ca.crt
```

### <a name="generate-a-certificate-for-localhost"></a>Generér et certifikat for localhost 

Kør følgende kommandoer for at oprette et certifikat til `localhost` ved hjælp af det genererede rodcertificeringsnøglecenter og *openssl.cnf*:

```sh
PBIVIZ=`which pbiviz`
PBIVIZ=`dirname $PBIVIZ`
PBIVIZ="$PBIVIZ/../lib/node_modules/powerbi-visuals-tools/certs"
# Make sure that $PBIVIZ contains the correct certificate directory path. ls $PBIVIZ should list 'blank' file.
openssl req -new -nodes -newkey rsa:2048 -keyout $PBIVIZ/PowerBIVisualTest_private.key -out $PBIVIZ/PowerBIVisualTest.csr -subj "/C=US/O=PowerBI Visuals/CN=localhost"
openssl x509 -req -sha256 -days 1024 -in $PBIVIZ/PowerBIVisualTest.csr -CA /tmp/local-root-ca.pem -CAkey /tmp/local-root-ca.key -CAcreateserial -extfile /tmp/openssl.cnf -out $PBIVIZ/PowerBIVisualTest_public.crt
```

### <a name="add-root-certificates"></a>Tilføj rodcertifikater

Hvis du vil føje et rodcertifikat til Chrome-browserens database, skal du køre:

```sh
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:$HOME/.pki/nssdb
```

Hvis du vil føje et rodcertifikat til Mozilla Firefox-browserens database, skal du køre:

```sh
for certDB in $(find $HOME/.mozilla* -name "cert*.db")
do
certDir=$(dirname ${certDB});
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:${certDir}
done
```

Hvis du vil tilføje et rodcertifikat i hele systemet, skal du køre:

```sh
sudo cp /tmp/local-root-ca.pem /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

### <a name="remove-root-certificates"></a>Fjern rodcertifikater

Hvis du vil fjerne et rodcertifikat, skal du køre:

```sh
sudo rm /usr/local/share/ca-certificates/local-root-ca.pem
sudo update-ca-certificates --fresh
```

## <a name="generate-a-certificate-manually"></a>Generér et certifikat manuelt

Du kan også generere et SSL-certifikat manuelt ved hjælp af OpenSSL. Du kan angive et hvilket som helst værktøj til at generere certifikaterne.

Hvis OpenSSL-værktøjet allerede er installeret, skal du generere et nyt certifikat ved at køre:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBIVisualTest_private.key -out PowerBIVisualTest_public.crt -days 365
```

Du kan som regel finde `PowerBI-visuals-tools`-webservercertifikater ved at køre en af følgende kommandoer:

- For den globale forekomst af værktøjerne:
  
  ```cmd
  %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
  ```

- For den lokale forekomst af værktøjerne:
  
  ```cmd
  <Power BI visual project root>\node_modules\PowerBI-visuals-tools\certs
  ```

### <a name="pem-format"></a>PEM-format

Hvis du bruger certifikatformatet PEM (Privacy Enhanced Mail), skal du gemme certifikatfilen som *PowerBIVisualTest_public.crt* og gemme den private nøgle som *PowerBIVisualTest_private.key*.

### <a name="pfx-format"></a>PFX-format

Hvis du bruger certifikatformatet PFX (Personal Information Exchange), skal du gemme certifikatfilen som *PowerBIVisualTest_public.pfx*.

Hvis PFX-certifikatfilen kræver et adgangsudtryk:

1. I konfigurationsfilen skal du angive:
   
   ```cmd
   \PowerBI-visuals-tools\config.json
   ```
   
1. I afsnittet `server` skal du angive adgangsudtrykket ved at erstatte pladsholderen \<YOUR PASSPHRASE>:

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBIVisualTest_private.key",
        "certificate":"certs/PowerBIVisualTest_public.crt",
        "pfx":"certs/PowerBIVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"<YOUR PASSPHRASE>"
    }
    ```

## <a name="next-steps"></a>Næste trin
- [Udvikling af en Power BI-visualisering](custom-visual-develop-tutorial.md)
- [Eksempler på Power BI-visualiseringer](samples.md)
- [Publicer Power BI-visualiseringer i AppSource](office-store.md)