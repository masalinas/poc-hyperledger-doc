- Download Hyperledger Sample Code from git

```shell
curl -sSL https://bit.ly/2ysbOFE | bash
```

- Go to test network folder

```shell
cd fabric-samples/test-network
```

- Deploy the test blockchain network with a sample channel and ca servers for it:

```shell
$ ./network.sh up createChannel -c mychannel -ca
Using docker and docker compose
Creating channel 'mychannel'.
If network is not up, starting nodes with CLI timeout of '5' tries and CLI delay of '3' seconds and using database 'leveldb with crypto from 'Certificate Authorities'
Bringing up network
LOCAL_VERSION=v2.5.9
DOCKER_IMAGE_VERSION=v2.5.9
CA_LOCAL_VERSION=v1.5.12
CA_DOCKER_IMAGE_VERSION=v1.5.12
Generating certificates using Fabric CA
WARN[0000] /home/miguel-salinas/git/fabric-samples/test-network/compose/compose-ca.yaml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion 
WARN[0000] /home/miguel-salinas/git/fabric-samples/test-network/compose/docker/docker-compose-ca.yaml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion 
[+] Running 4/4
 ✔ Network fabric_test   Created                                                                                                                           0.1s 
 ✔ Container ca_org1     Started                                                                                                                           0.4s 
 ✔ Container ca_orderer  Started                                                                                                                           0.4s 
 ✔ Container ca_org2     Started                                                                                                                           0.4s 
Creating Org1 Identities
Enrolling the CA admin
+ fabric-ca-client enroll -u https://admin:adminpw@localhost:7054 --caname ca-org1 --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2024/11/20 22:34:47 [INFO] Created a default configuration file at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/fabric-ca-client-config.yaml
2024/11/20 22:34:47 [INFO] TLS Enabled
2024/11/20 22:34:47 [INFO] generating key: &{A:ecdsa S:256}
2024/11/20 22:34:47 [INFO] encoded CSR
2024/11/20 22:34:47 [INFO] Stored client certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/msp/signcerts/cert.pem
2024/11/20 22:34:47 [INFO] Stored root CA certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/msp/cacerts/localhost-7054-ca-org1.pem
2024/11/20 22:34:47 [INFO] Stored Issuer public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/msp/IssuerPublicKey
2024/11/20 22:34:47 [INFO] Stored Issuer revocation public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/msp/IssuerRevocationPublicKey
Registering peer0
+ fabric-ca-client register --caname ca-org1 --id.name peer0 --id.secret peer0pw --id.type peer --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2024/11/20 22:34:47 [INFO] Configuration file location: /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/fabric-ca-client-config.yaml
2024/11/20 22:34:47 [INFO] TLS Enabled
2024/11/20 22:34:47 [INFO] TLS Enabled
Password: peer0pw
Registering user
+ fabric-ca-client register --caname ca-org1 --id.name user1 --id.secret user1pw --id.type client --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2024/11/20 22:34:47 [INFO] Configuration file location: /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/fabric-ca-client-config.yaml
2024/11/20 22:34:47 [INFO] TLS Enabled
2024/11/20 22:34:47 [INFO] TLS Enabled
Password: user1pw
Registering the org admin
+ fabric-ca-client register --caname ca-org1 --id.name org1admin --id.secret org1adminpw --id.type admin --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2024/11/20 22:34:48 [INFO] Configuration file location: /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/fabric-ca-client-config.yaml
2024/11/20 22:34:48 [INFO] TLS Enabled
2024/11/20 22:34:48 [INFO] TLS Enabled
Password: org1adminpw
Generating the peer0 msp
+ fabric-ca-client enroll -u https://peer0:peer0pw@localhost:7054 --caname ca-org1 -M /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/msp --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2024/11/20 22:34:48 [INFO] TLS Enabled
2024/11/20 22:34:48 [INFO] generating key: &{A:ecdsa S:256}
2024/11/20 22:34:48 [INFO] encoded CSR
2024/11/20 22:34:48 [INFO] Stored client certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/msp/signcerts/cert.pem
2024/11/20 22:34:48 [INFO] Stored root CA certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/msp/cacerts/localhost-7054-ca-org1.pem
2024/11/20 22:34:48 [INFO] Stored Issuer public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/msp/IssuerPublicKey
2024/11/20 22:34:48 [INFO] Stored Issuer revocation public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/msp/IssuerRevocationPublicKey
Generating the peer0-tls certificates, use --csr.hosts to specify Subject Alternative Names
+ fabric-ca-client enroll -u https://peer0:peer0pw@localhost:7054 --caname ca-org1 -M /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls --enrollment.profile tls --csr.hosts peer0.org1.example.com --csr.hosts localhost --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2024/11/20 22:34:48 [INFO] TLS Enabled
2024/11/20 22:34:48 [INFO] generating key: &{A:ecdsa S:256}
2024/11/20 22:34:48 [INFO] encoded CSR
2024/11/20 22:34:48 [INFO] Stored client certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/signcerts/cert.pem
2024/11/20 22:34:48 [INFO] Stored TLS root CA certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/tlscacerts/tls-localhost-7054-ca-org1.pem
2024/11/20 22:34:48 [INFO] Stored Issuer public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/IssuerPublicKey
2024/11/20 22:34:48 [INFO] Stored Issuer revocation public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/IssuerRevocationPublicKey
Generating the user msp
+ fabric-ca-client enroll -u https://user1:user1pw@localhost:7054 --caname ca-org1 -M /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/User1@org1.example.com/msp --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2024/11/20 22:34:48 [INFO] TLS Enabled
2024/11/20 22:34:48 [INFO] generating key: &{A:ecdsa S:256}
2024/11/20 22:34:48 [INFO] encoded CSR
2024/11/20 22:34:48 [INFO] Stored client certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/User1@org1.example.com/msp/signcerts/cert.pem
2024/11/20 22:34:48 [INFO] Stored root CA certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/User1@org1.example.com/msp/cacerts/localhost-7054-ca-org1.pem
2024/11/20 22:34:48 [INFO] Stored Issuer public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/User1@org1.example.com/msp/IssuerPublicKey
2024/11/20 22:34:48 [INFO] Stored Issuer revocation public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/User1@org1.example.com/msp/IssuerRevocationPublicKey
Generating the org admin msp
+ fabric-ca-client enroll -u https://org1admin:org1adminpw@localhost:7054 --caname ca-org1 -M /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2024/11/20 22:34:48 [INFO] TLS Enabled
2024/11/20 22:34:48 [INFO] generating key: &{A:ecdsa S:256}
2024/11/20 22:34:48 [INFO] encoded CSR
2024/11/20 22:34:48 [INFO] Stored client certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp/signcerts/cert.pem
2024/11/20 22:34:48 [INFO] Stored root CA certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp/cacerts/localhost-7054-ca-org1.pem
2024/11/20 22:34:48 [INFO] Stored Issuer public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp/IssuerPublicKey
2024/11/20 22:34:48 [INFO] Stored Issuer revocation public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp/IssuerRevocationPublicKey
Creating Org2 Identities
Enrolling the CA admin
+ fabric-ca-client enroll -u https://admin:adminpw@localhost:8054 --caname ca-org2 --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2024/11/20 22:34:48 [INFO] Created a default configuration file at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/fabric-ca-client-config.yaml
2024/11/20 22:34:48 [INFO] TLS Enabled
2024/11/20 22:34:48 [INFO] generating key: &{A:ecdsa S:256}
2024/11/20 22:34:48 [INFO] encoded CSR
2024/11/20 22:34:48 [INFO] Stored client certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/msp/signcerts/cert.pem
2024/11/20 22:34:48 [INFO] Stored root CA certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/msp/cacerts/localhost-8054-ca-org2.pem
2024/11/20 22:34:48 [INFO] Stored Issuer public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/msp/IssuerPublicKey
2024/11/20 22:34:48 [INFO] Stored Issuer revocation public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/msp/IssuerRevocationPublicKey
Registering peer0
+ fabric-ca-client register --caname ca-org2 --id.name peer0 --id.secret peer0pw --id.type peer --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2024/11/20 22:34:48 [INFO] Configuration file location: /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/fabric-ca-client-config.yaml
2024/11/20 22:34:48 [INFO] TLS Enabled
2024/11/20 22:34:48 [INFO] TLS Enabled
Password: peer0pw
Registering user
+ fabric-ca-client register --caname ca-org2 --id.name user1 --id.secret user1pw --id.type client --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2024/11/20 22:34:49 [INFO] Configuration file location: /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/fabric-ca-client-config.yaml
2024/11/20 22:34:49 [INFO] TLS Enabled
2024/11/20 22:34:49 [INFO] TLS Enabled
Password: user1pw
Registering the org admin
+ fabric-ca-client register --caname ca-org2 --id.name org2admin --id.secret org2adminpw --id.type admin --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2024/11/20 22:34:49 [INFO] Configuration file location: /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/fabric-ca-client-config.yaml
2024/11/20 22:34:49 [INFO] TLS Enabled
2024/11/20 22:34:49 [INFO] TLS Enabled
Password: org2adminpw
Generating the peer0 msp
+ fabric-ca-client enroll -u https://peer0:peer0pw@localhost:8054 --caname ca-org2 -M /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/msp --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2024/11/20 22:34:49 [INFO] TLS Enabled
2024/11/20 22:34:49 [INFO] generating key: &{A:ecdsa S:256}
2024/11/20 22:34:49 [INFO] encoded CSR
2024/11/20 22:34:49 [INFO] Stored client certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/msp/signcerts/cert.pem
2024/11/20 22:34:49 [INFO] Stored root CA certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/msp/cacerts/localhost-8054-ca-org2.pem
2024/11/20 22:34:49 [INFO] Stored Issuer public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/msp/IssuerPublicKey
2024/11/20 22:34:49 [INFO] Stored Issuer revocation public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/msp/IssuerRevocationPublicKey
Generating the peer0-tls certificates, use --csr.hosts to specify Subject Alternative Names
+ fabric-ca-client enroll -u https://peer0:peer0pw@localhost:8054 --caname ca-org2 -M /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls --enrollment.profile tls --csr.hosts peer0.org2.example.com --csr.hosts localhost --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2024/11/20 22:34:49 [INFO] TLS Enabled
2024/11/20 22:34:49 [INFO] generating key: &{A:ecdsa S:256}
2024/11/20 22:34:49 [INFO] encoded CSR
2024/11/20 22:34:49 [INFO] Stored client certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/signcerts/cert.pem
2024/11/20 22:34:49 [INFO] Stored TLS root CA certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/tlscacerts/tls-localhost-8054-ca-org2.pem
2024/11/20 22:34:49 [INFO] Stored Issuer public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/IssuerPublicKey
2024/11/20 22:34:49 [INFO] Stored Issuer revocation public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/IssuerRevocationPublicKey
Generating the user msp
+ fabric-ca-client enroll -u https://user1:user1pw@localhost:8054 --caname ca-org2 -M /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/User1@org2.example.com/msp --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2024/11/20 22:34:49 [INFO] TLS Enabled
2024/11/20 22:34:49 [INFO] generating key: &{A:ecdsa S:256}
2024/11/20 22:34:49 [INFO] encoded CSR
2024/11/20 22:34:49 [INFO] Stored client certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/User1@org2.example.com/msp/signcerts/cert.pem
2024/11/20 22:34:49 [INFO] Stored root CA certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/User1@org2.example.com/msp/cacerts/localhost-8054-ca-org2.pem
2024/11/20 22:34:49 [INFO] Stored Issuer public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/User1@org2.example.com/msp/IssuerPublicKey
2024/11/20 22:34:49 [INFO] Stored Issuer revocation public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/User1@org2.example.com/msp/IssuerRevocationPublicKey
Generating the org admin msp
+ fabric-ca-client enroll -u https://org2admin:org2adminpw@localhost:8054 --caname ca-org2 -M /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/Admin@org2.example.com/msp --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2024/11/20 22:34:49 [INFO] TLS Enabled
2024/11/20 22:34:49 [INFO] generating key: &{A:ecdsa S:256}
2024/11/20 22:34:49 [INFO] encoded CSR
2024/11/20 22:34:49 [INFO] Stored client certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/Admin@org2.example.com/msp/signcerts/cert.pem
2024/11/20 22:34:49 [INFO] Stored root CA certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/Admin@org2.example.com/msp/cacerts/localhost-8054-ca-org2.pem
2024/11/20 22:34:49 [INFO] Stored Issuer public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/Admin@org2.example.com/msp/IssuerPublicKey
2024/11/20 22:34:49 [INFO] Stored Issuer revocation public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/Admin@org2.example.com/msp/IssuerRevocationPublicKey
Creating Orderer Org Identities
Enrolling the CA admin
+ fabric-ca-client enroll -u https://admin:adminpw@localhost:9054 --caname ca-orderer --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/ordererOrg/ca-cert.pem
2024/11/20 22:34:49 [INFO] Created a default configuration file at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/fabric-ca-client-config.yaml
2024/11/20 22:34:49 [INFO] TLS Enabled
2024/11/20 22:34:49 [INFO] generating key: &{A:ecdsa S:256}
2024/11/20 22:34:49 [INFO] encoded CSR
2024/11/20 22:34:49 [INFO] Stored client certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/msp/signcerts/cert.pem
2024/11/20 22:34:49 [INFO] Stored root CA certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/msp/cacerts/localhost-9054-ca-orderer.pem
2024/11/20 22:34:49 [INFO] Stored Issuer public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/msp/IssuerPublicKey
2024/11/20 22:34:49 [INFO] Stored Issuer revocation public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/msp/IssuerRevocationPublicKey
Registering orderer
+ fabric-ca-client register --caname ca-orderer --id.name orderer --id.secret ordererpw --id.type orderer --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/ordererOrg/ca-cert.pem
2024/11/20 22:34:50 [INFO] Configuration file location: /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/fabric-ca-client-config.yaml
2024/11/20 22:34:50 [INFO] TLS Enabled
2024/11/20 22:34:50 [INFO] TLS Enabled
Password: ordererpw
Registering the orderer admin
+ fabric-ca-client register --caname ca-orderer --id.name ordererAdmin --id.secret ordererAdminpw --id.type admin --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/ordererOrg/ca-cert.pem
2024/11/20 22:34:50 [INFO] Configuration file location: /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/fabric-ca-client-config.yaml
2024/11/20 22:34:50 [INFO] TLS Enabled
2024/11/20 22:34:50 [INFO] TLS Enabled
Password: ordererAdminpw
Generating the orderer msp
+ fabric-ca-client enroll -u https://orderer:ordererpw@localhost:9054 --caname ca-orderer -M /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/ordererOrg/ca-cert.pem
2024/11/20 22:34:50 [INFO] TLS Enabled
2024/11/20 22:34:50 [INFO] generating key: &{A:ecdsa S:256}
2024/11/20 22:34:50 [INFO] encoded CSR
2024/11/20 22:34:50 [INFO] Stored client certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/signcerts/cert.pem
2024/11/20 22:34:50 [INFO] Stored root CA certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/cacerts/localhost-9054-ca-orderer.pem
2024/11/20 22:34:50 [INFO] Stored Issuer public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/IssuerPublicKey
2024/11/20 22:34:50 [INFO] Stored Issuer revocation public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/IssuerRevocationPublicKey
Generating the orderer-tls certificates, use --csr.hosts to specify Subject Alternative Names
+ fabric-ca-client enroll -u https://orderer:ordererpw@localhost:9054 --caname ca-orderer -M /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/tls --enrollment.profile tls --csr.hosts orderer.example.com --csr.hosts localhost --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/ordererOrg/ca-cert.pem
2024/11/20 22:34:50 [INFO] TLS Enabled
2024/11/20 22:34:50 [INFO] generating key: &{A:ecdsa S:256}
2024/11/20 22:34:50 [INFO] encoded CSR
2024/11/20 22:34:50 [INFO] Stored client certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/tls/signcerts/cert.pem
2024/11/20 22:34:50 [INFO] Stored TLS root CA certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/tls/tlscacerts/tls-localhost-9054-ca-orderer.pem
2024/11/20 22:34:50 [INFO] Stored Issuer public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/tls/IssuerPublicKey
2024/11/20 22:34:50 [INFO] Stored Issuer revocation public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/tls/IssuerRevocationPublicKey
Generating the admin msp
+ fabric-ca-client enroll -u https://ordererAdmin:ordererAdminpw@localhost:9054 --caname ca-orderer -M /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/users/Admin@example.com/msp --tls.certfiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/fabric-ca/ordererOrg/ca-cert.pem
2024/11/20 22:34:50 [INFO] TLS Enabled
2024/11/20 22:34:50 [INFO] generating key: &{A:ecdsa S:256}
2024/11/20 22:34:50 [INFO] encoded CSR
2024/11/20 22:34:50 [INFO] Stored client certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/users/Admin@example.com/msp/signcerts/cert.pem
2024/11/20 22:34:50 [INFO] Stored root CA certificate at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/users/Admin@example.com/msp/cacerts/localhost-9054-ca-orderer.pem
2024/11/20 22:34:50 [INFO] Stored Issuer public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/users/Admin@example.com/msp/IssuerPublicKey
2024/11/20 22:34:50 [INFO] Stored Issuer revocation public key at /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/users/Admin@example.com/msp/IssuerRevocationPublicKey
Generating CCP files for Org1 and Org2
WARN[0000] /home/miguel-salinas/git/fabric-samples/test-network/compose/compose-test-net.yaml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion 
WARN[0000] /home/miguel-salinas/git/fabric-samples/test-network/compose/docker/docker-compose-test-net.yaml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion 
WARN[0000] Found orphan containers ([ca_org1 ca_orderer ca_org2]) for this project. If you removed or renamed this service in your compose file, you can run this command with the --remove-orphans flag to clean it up. 
[+] Running 6/6
 ✔ Volume "compose_peer0.org2.example.com"  Created                                                                                                        0.0s 
 ✔ Volume "compose_orderer.example.com"     Created                                                                                                        0.0s 
 ✔ Volume "compose_peer0.org1.example.com"  Created                                                                                                        0.0s 
 ✔ Container peer0.org2.example.com         Started                                                                                                        0.4s 
 ✔ Container orderer.example.com            Started                                                                                                        0.4s 
 ✔ Container peer0.org1.example.com         Started                                                                                                        0.4s 
CONTAINER ID   IMAGE                                 COMMAND                  CREATED         STATUS                     PORTS                                                                                                                             NAMES
635a44771b7d   hyperledger/fabric-peer:latest        "peer node start"        1 second ago    Up Less than a second      0.0.0.0:9051->9051/tcp, :::9051->9051/tcp, 7051/tcp, 0.0.0.0:9445->9445/tcp, :::9445->9445/tcp                                    peer0.org2.example.com
5fa5974b4714   hyperledger/fabric-orderer:latest     "orderer"                1 second ago    Up Less than a second      0.0.0.0:7050->7050/tcp, :::7050->7050/tcp, 0.0.0.0:7053->7053/tcp, :::7053->7053/tcp, 0.0.0.0:9443->9443/tcp, :::9443->9443/tcp   orderer.example.com
d043f3edb050   hyperledger/fabric-peer:latest        "peer node start"        1 second ago    Up Less than a second      0.0.0.0:7051->7051/tcp, :::7051->7051/tcp, 0.0.0.0:9444->9444/tcp, :::9444->9444/tcp                                              peer0.org1.example.com
6d922e3d40c8   hyperledger/fabric-ca:latest          "sh -c 'fabric-ca-se…"   5 seconds ago   Up 4 seconds               0.0.0.0:7054->7054/tcp, :::7054->7054/tcp, 0.0.0.0:17054->17054/tcp, :::17054->17054/tcp                                          ca_org1
3c7a47f21fa8   hyperledger/fabric-ca:latest          "sh -c 'fabric-ca-se…"   5 seconds ago   Up 4 seconds               0.0.0.0:9054->9054/tcp, :::9054->9054/tcp, 7054/tcp, 0.0.0.0:19054->19054/tcp, :::19054->19054/tcp                                ca_orderer
1c2f3c6fb6a6   hyperledger/fabric-ca:latest          "sh -c 'fabric-ca-se…"   5 seconds ago   Up 4 seconds               0.0.0.0:8054->8054/tcp, :::8054->8054/tcp, 7054/tcp, 0.0.0.0:18054->18054/tcp, :::18054->18054/tcp                                ca_org2
97db7a66e4ae   poc-bokeh-auth                        "python bootstrap.py"    2 weeks ago     Exited (137) 2 weeks ago                                                                                                                                     poc-bokeh-auth
ee9f766dc3a9   haproxy:3.0-alpine                    "docker-entrypoint.s…"   4 weeks ago     Exited (0) 2 weeks ago                                                                                                                                       k8s-proxy
71ee27926e01   gcr.io/k8s-minikube/kicbase:v0.0.45   "/usr/local/bin/entr…"   5 weeks ago     Exited (130) 2 weeks ago                                                                                                                                     minikube
751c259e10d2   portainer/portainer-ce:2.21.2         "/portainer"             6 weeks ago     Exited (2) 4 minutes ago                                                                                                                                     portainer
Using docker and docker compose
Generating channel genesis block 'mychannel.block'
Using organization 1
/home/miguel-salinas/git/fabric-samples/test-network/../bin/configtxgen
+ '[' 0 -eq 1 ']'
+ configtxgen -profile ChannelUsingRaft -outputBlock ./channel-artifacts/mychannel.block -channelID mychannel
2024-11-20 22:34:51.414 CET 0001 INFO [common.tools.configtxgen] main -> Loading configuration
2024-11-20 22:34:51.420 CET 0002 INFO [common.tools.configtxgen.localconfig] completeInitialization -> orderer type: etcdraft
2024-11-20 22:34:51.420 CET 0003 INFO [common.tools.configtxgen.localconfig] completeInitialization -> Orderer.EtcdRaft.Options unset, setting to tick_interval:"500ms" election_tick:10 heartbeat_tick:1 max_inflight_blocks:5 snapshot_interval_size:16777216 
2024-11-20 22:34:51.420 CET 0004 INFO [common.tools.configtxgen.localconfig] Load -> Loaded configuration: /home/miguel-salinas/git/fabric-samples/test-network/configtx/configtx.yaml
2024-11-20 22:34:51.430 CET 0005 INFO [common.tools.configtxgen] doOutputBlock -> Generating genesis block
2024-11-20 22:34:51.430 CET 0006 INFO [common.tools.configtxgen] doOutputBlock -> Creating application channel genesis block
2024-11-20 22:34:51.431 CET 0007 INFO [common.tools.configtxgen] doOutputBlock -> Writing genesis block
+ res=0
Creating channel mychannel
Adding orderers
+ . scripts/orderer.sh mychannel
+ '[' 0 -eq 1 ']'
+ res=0
Status: 201
{
	"name": "mychannel",
	"url": "/participation/v1/channels/mychannel",
	"consensusRelation": "consenter",
	"status": "active",
	"height": 1
}

Channel 'mychannel' created
Joining org1 peer to the channel...
Using organization 1
+ peer channel join -b ./channel-artifacts/mychannel.block
+ res=0
2024-11-20 22:34:57.590 CET 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2024-11-20 22:34:57.614 CET 0002 INFO [channelCmd] executeJoin -> Successfully submitted proposal to join channel
Joining org2 peer to the channel...
Using organization 2
+ peer channel join -b ./channel-artifacts/mychannel.block
+ res=0
2024-11-20 22:35:00.674 CET 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2024-11-20 22:35:00.695 CET 0002 INFO [channelCmd] executeJoin -> Successfully submitted proposal to join channel
Setting anchor peer for org1...
Using organization 1
Fetching channel config for channel mychannel
Using organization 1
Fetching the most recent configuration block for the channel
++ peer channel fetch config /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_block.pb -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com -c mychannel --tls --cafile /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem
2024-11-20 22:35:00.759 CET 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2024-11-20 22:35:00.764 CET 0002 INFO [cli.common] readBlock -> Received block: 0
2024-11-20 22:35:00.764 CET 0003 INFO [channelCmd] fetch -> Retrieving last config block: 0
2024-11-20 22:35:00.765 CET 0004 INFO [cli.common] readBlock -> Received block: 0
Decoding config block to JSON and isolating config to /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/Org1MSPconfig.json
++ configtxlator proto_decode --input /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_block.pb --type common.Block --output /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_block.json
++ jq '.data.data[0].payload.data.config' /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_block.json
++ res=0
Generating anchor peer update transaction for Org1 on channel mychannel
++ jq '.channel_group.groups.Application.groups.Org1MSP.values += {"AnchorPeers":{"mod_policy": "Admins","value":{"anchor_peers": [{"host": "peer0.org1.example.com","port": 7051}]},"version": "0"}}' /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/Org1MSPconfig.json
++ res=0
++ configtxlator proto_encode --input /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/Org1MSPconfig.json --type common.Config --output /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/original_config.pb
++ configtxlator proto_encode --input /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/Org1MSPmodified_config.json --type common.Config --output /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/modified_config.pb
++ configtxlator compute_update --channel_id mychannel --original /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/original_config.pb --updated /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/modified_config.pb --output /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_update.pb
++ configtxlator proto_decode --input /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_update.pb --type common.ConfigUpdate --output /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_update.json
++ jq .
+++ cat /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_update.json
++ echo '{"payload":{"header":{"channel_header":{"channel_id":"mychannel", "type":2}},"data":{"config_update":{' '"channel_id":' '"mychannel",' '"isolated_data":' '{},' '"read_set":' '{' '"groups":' '{' '"Application":' '{' '"groups":' '{' '"Org1MSP":' '{' '"groups":' '{},' '"mod_policy":' '"",' '"policies":' '{' '"Admins":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Endorsement":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Readers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Writers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '}' '},' '"values":' '{' '"MSP":' '{' '"mod_policy":' '"",' '"value":' null, '"version":' '"0"' '}' '},' '"version":' '"0"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '},' '"write_set":' '{' '"groups":' '{' '"Application":' '{' '"groups":' '{' '"Org1MSP":' '{' '"groups":' '{},' '"mod_policy":' '"Admins",' '"policies":' '{' '"Admins":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Endorsement":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Readers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Writers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '}' '},' '"values":' '{' '"AnchorPeers":' '{' '"mod_policy":' '"Admins",' '"value":' '{' '"anchor_peers":' '[' '{' '"host":' '"peer0.org1.example.com",' '"port":' 7051 '}' ']' '},' '"version":' '"0"' '},' '"MSP":' '{' '"mod_policy":' '"",' '"value":' null, '"version":' '"0"' '}' '},' '"version":' '"1"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '}' '}}}}'
++ configtxlator proto_encode --input /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_update_in_envelope.json --type common.Envelope --output /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/Org1MSPanchors.tx
2024-11-20 22:35:00.965 CET 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2024-11-20 22:35:00.974 CET 0002 INFO [channelCmd] update -> Successfully submitted channel update
Anchor peer set for org 'Org1MSP' on channel 'mychannel'
Setting anchor peer for org2...
Using organization 2
Fetching channel config for channel mychannel
Using organization 2
Fetching the most recent configuration block for the channel
++ peer channel fetch config /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_block.pb -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com -c mychannel --tls --cafile /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem
2024-11-20 22:35:01.034 CET 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2024-11-20 22:35:01.036 CET 0002 INFO [cli.common] readBlock -> Received block: 1
2024-11-20 22:35:01.036 CET 0003 INFO [channelCmd] fetch -> Retrieving last config block: 1
2024-11-20 22:35:01.040 CET 0004 INFO [cli.common] readBlock -> Received block: 1
Decoding config block to JSON and isolating config to /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/Org2MSPconfig.json
++ configtxlator proto_decode --input /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_block.pb --type common.Block --output /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_block.json
++ jq '.data.data[0].payload.data.config' /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_block.json
++ res=0
Generating anchor peer update transaction for Org2 on channel mychannel
++ jq '.channel_group.groups.Application.groups.Org2MSP.values += {"AnchorPeers":{"mod_policy": "Admins","value":{"anchor_peers": [{"host": "peer0.org2.example.com","port": 9051}]},"version": "0"}}' /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/Org2MSPconfig.json
++ res=0
++ configtxlator proto_encode --input /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/Org2MSPconfig.json --type common.Config --output /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/original_config.pb
++ configtxlator proto_encode --input /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/Org2MSPmodified_config.json --type common.Config --output /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/modified_config.pb
++ configtxlator compute_update --channel_id mychannel --original /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/original_config.pb --updated /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/modified_config.pb --output /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_update.pb
++ configtxlator proto_decode --input /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_update.pb --type common.ConfigUpdate --output /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_update.json
++ jq .
+++ cat /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_update.json
++ echo '{"payload":{"header":{"channel_header":{"channel_id":"mychannel", "type":2}},"data":{"config_update":{' '"channel_id":' '"mychannel",' '"isolated_data":' '{},' '"read_set":' '{' '"groups":' '{' '"Application":' '{' '"groups":' '{' '"Org2MSP":' '{' '"groups":' '{},' '"mod_policy":' '"",' '"policies":' '{' '"Admins":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Endorsement":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Readers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Writers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '}' '},' '"values":' '{' '"MSP":' '{' '"mod_policy":' '"",' '"value":' null, '"version":' '"0"' '}' '},' '"version":' '"0"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '},' '"write_set":' '{' '"groups":' '{' '"Application":' '{' '"groups":' '{' '"Org2MSP":' '{' '"groups":' '{},' '"mod_policy":' '"Admins",' '"policies":' '{' '"Admins":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Endorsement":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Readers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Writers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '}' '},' '"values":' '{' '"AnchorPeers":' '{' '"mod_policy":' '"Admins",' '"value":' '{' '"anchor_peers":' '[' '{' '"host":' '"peer0.org2.example.com",' '"port":' 9051 '}' ']' '},' '"version":' '"0"' '},' '"MSP":' '{' '"mod_policy":' '"",' '"value":' null, '"version":' '"0"' '}' '},' '"version":' '"1"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '}' '}}}}'
++ configtxlator proto_encode --input /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/config_update_in_envelope.json --type common.Envelope --output /home/miguel-salinas/git/fabric-samples/test-network/channel-artifacts/Org2MSPanchors.tx
2024-11-20 22:35:01.199 CET 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2024-11-20 22:35:01.208 CET 0002 INFO [channelCmd] update -> Successfully submitted channel update
Anchor peer set for org 'Org2MSP' on channel 'mychannel'
Channel 'mychannel' joined
```

Containers deployed:

```shell
$ docker ps
CONTAINER ID   IMAGE                               COMMAND                  CREATED         STATUS         PORTS                                                                                                                             NAMES
635a44771b7d   hyperledger/fabric-peer:latest      "peer node start"        3 minutes ago   Up 3 minutes   0.0.0.0:9051->9051/tcp, :::9051->9051/tcp, 7051/tcp, 0.0.0.0:9445->9445/tcp, :::9445->9445/tcp                                    peer0.org2.example.com
5fa5974b4714   hyperledger/fabric-orderer:latest   "orderer"                3 minutes ago   Up 3 minutes   0.0.0.0:7050->7050/tcp, :::7050->7050/tcp, 0.0.0.0:7053->7053/tcp, :::7053->7053/tcp, 0.0.0.0:9443->9443/tcp, :::9443->9443/tcp   orderer.example.com
d043f3edb050   hyperledger/fabric-peer:latest      "peer node start"        3 minutes ago   Up 3 minutes   0.0.0.0:7051->7051/tcp, :::7051->7051/tcp, 0.0.0.0:9444->9444/tcp, :::9444->9444/tcp                                              peer0.org1.example.com
6d922e3d40c8   hyperledger/fabric-ca:latest        "sh -c 'fabric-ca-se…"   3 minutes ago   Up 3 minutes   0.0.0.0:7054->7054/tcp, :::7054->7054/tcp, 0.0.0.0:17054->17054/tcp, :::17054->17054/tcp                                          ca_org1
3c7a47f21fa8   hyperledger/fabric-ca:latest        "sh -c 'fabric-ca-se…"   3 minutes ago   Up 3 minutes   0.0.0.0:9054->9054/tcp, :::9054->9054/tcp, 7054/tcp, 0.0.0.0:19054->19054/tcp, :::19054->19054/tcp                                ca_orderer
1c2f3c6fb6a6   hyperledger/fabric-ca:latest        "sh -c 'fabric-ca-se…"   3 minutes ago   Up 3 minutes   0.0.0.0:8054->8054/tcp, :::8054->8054/tcp, 7054/tcp, 0.0.0.0:18054->18054/tcp, :::18054->18054/tcp                                ca_org2
```

- Deploy chain code(smaty contract)

```shell
./network.sh deployCC -ccn trade -ccv 1.0 -ccp /home/miguel-salinas/git/poc-hyperledger-cc/ -ccl javascript
Using docker and docker compose
deploying chaincode on channel 'mychannel'
executing with the following
- CHANNEL_NAME: mychannel
- CC_NAME: trade
- CC_SRC_PATH: /home/miguel-salinas/git/poc-hyperledger-cc/
- CC_SRC_LANGUAGE: javascript
- CC_VERSION: 1.0
- CC_SEQUENCE: auto
- CC_END_POLICY: NA
- CC_COLL_CONFIG: NA
- CC_INIT_FCN: NA
- DELAY: 3
- MAX_RETRY: 5
- VERBOSE: false
executing with the following
- CC_NAME: trade
- CC_SRC_PATH: /home/miguel-salinas/git/poc-hyperledger-cc/
- CC_SRC_LANGUAGE: javascript
- CC_VERSION: 1.0
+ '[' false = true ']'
+ peer lifecycle chaincode package trade.tar.gz --path /home/miguel-salinas/git/poc-hyperledger-cc/ --lang node --label trade_1.0
+ res=0
Chaincode is packaged
Installing chaincode on peer0.org1...
Using organization 1
+ peer lifecycle chaincode queryinstalled --output json
+ grep '^trade_1.0:9288fd658c1c24e8de7bbbe51b7130781e20c142915e1c7f088f40165700f450$'
+ jq -r 'try (.installed_chaincodes[].package_id)'
+ test 1 -ne 0
+ peer lifecycle chaincode install trade.tar.gz
+ res=0
2024-11-20 22:39:26.161 CET 0001 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Installed remotely: response:<status:200 payload:"\nJtrade_1.0:9288fd658c1c24e8de7bbbe51b7130781e20c142915e1c7f088f40165700f450\022\ttrade_1.0" > 
2024-11-20 22:39:26.162 CET 0002 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Chaincode code package identifier: trade_1.0:9288fd658c1c24e8de7bbbe51b7130781e20c142915e1c7f088f40165700f450
Chaincode is installed on peer0.org1
Install chaincode on peer0.org2...
Using organization 2
+ peer lifecycle chaincode queryinstalled --output json
+ jq -r 'try (.installed_chaincodes[].package_id)'
+ grep '^trade_1.0:9288fd658c1c24e8de7bbbe51b7130781e20c142915e1c7f088f40165700f450$'
+ test 1 -ne 0
+ peer lifecycle chaincode install trade.tar.gz
+ res=0
2024-11-20 22:39:35.043 CET 0001 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Installed remotely: response:<status:200 payload:"\nJtrade_1.0:9288fd658c1c24e8de7bbbe51b7130781e20c142915e1c7f088f40165700f450\022\ttrade_1.0" > 
2024-11-20 22:39:35.043 CET 0002 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Chaincode code package identifier: trade_1.0:9288fd658c1c24e8de7bbbe51b7130781e20c142915e1c7f088f40165700f450
Chaincode is installed on peer0.org2
++ sed -n '/Version:/{s/.*Sequence: //; s/, Endorsement Plugin:.*$//; p;}'
++ peer lifecycle chaincode querycommitted --channelID mychannel --name trade
Error: query failed with status: 404 - namespace trade is not defined
+ COMMITTED_CC_SEQUENCE=
+ res=0
Using organization 1
+ peer lifecycle chaincode queryinstalled --output json
+ jq -r 'try (.installed_chaincodes[].package_id)'
+ grep '^trade_1.0:9288fd658c1c24e8de7bbbe51b7130781e20c142915e1c7f088f40165700f450$'
+ res=0
trade_1.0:9288fd658c1c24e8de7bbbe51b7130781e20c142915e1c7f088f40165700f450
Query installed successful on peer0.org1 on channel
Using organization 1
+ peer lifecycle chaincode approveformyorg -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem --channelID mychannel --name trade --version 1.0 --package-id trade_1.0:9288fd658c1c24e8de7bbbe51b7130781e20c142915e1c7f088f40165700f450 --sequence 1
+ res=0
2024-11-20 22:39:37.294 CET 0001 INFO [chaincodeCmd] ClientWait -> txid [82a09b4650ec4fa9dd32a61855f5c72a3dbb8bf0788a857628b2b2883bb6602a] committed with status (VALID) at localhost:7051
Chaincode definition approved on peer0.org1 on channel 'mychannel'
Using organization 1
Checking the commit readiness of the chaincode definition on peer0.org1 on channel 'mychannel'...
Attempting to check the commit readiness of the chaincode definition on peer0.org1, Retry after 3 seconds.
+ peer lifecycle chaincode checkcommitreadiness --channelID mychannel --name trade --version 1.0 --sequence 1 --output json
+ res=0
{
	"approvals": {
		"Org1MSP": true,
		"Org2MSP": false
	}
}
Checking the commit readiness of the chaincode definition successful on peer0.org1 on channel 'mychannel'
Using organization 2
Checking the commit readiness of the chaincode definition on peer0.org2 on channel 'mychannel'...
Attempting to check the commit readiness of the chaincode definition on peer0.org2, Retry after 3 seconds.
+ peer lifecycle chaincode checkcommitreadiness --channelID mychannel --name trade --version 1.0 --sequence 1 --output json
+ res=0
{
	"approvals": {
		"Org1MSP": true,
		"Org2MSP": false
	}
}
Checking the commit readiness of the chaincode definition successful on peer0.org2 on channel 'mychannel'
Using organization 2
+ peer lifecycle chaincode approveformyorg -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem --channelID mychannel --name trade --version 1.0 --package-id trade_1.0:9288fd658c1c24e8de7bbbe51b7130781e20c142915e1c7f088f40165700f450 --sequence 1
+ res=0
2024-11-20 22:39:45.550 CET 0001 INFO [chaincodeCmd] ClientWait -> txid [ceb77166235bc7c8004db3d5e6192e29631319ef78916b6e2e387e59088aaf2a] committed with status (VALID) at localhost:9051
Chaincode definition approved on peer0.org2 on channel 'mychannel'
Using organization 1
Checking the commit readiness of the chaincode definition on peer0.org1 on channel 'mychannel'...
Attempting to check the commit readiness of the chaincode definition on peer0.org1, Retry after 3 seconds.
+ peer lifecycle chaincode checkcommitreadiness --channelID mychannel --name trade --version 1.0 --sequence 1 --output json
+ res=0
{
	"approvals": {
		"Org1MSP": true,
		"Org2MSP": true
	}
}
Checking the commit readiness of the chaincode definition successful on peer0.org1 on channel 'mychannel'
Using organization 2
Checking the commit readiness of the chaincode definition on peer0.org2 on channel 'mychannel'...
Attempting to check the commit readiness of the chaincode definition on peer0.org2, Retry after 3 seconds.
+ peer lifecycle chaincode checkcommitreadiness --channelID mychannel --name trade --version 1.0 --sequence 1 --output json
+ res=0
{
	"approvals": {
		"Org1MSP": true,
		"Org2MSP": true
	}
}
Checking the commit readiness of the chaincode definition successful on peer0.org2 on channel 'mychannel'
Using organization 1
Using organization 2
+ peer lifecycle chaincode commit -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile /home/miguel-salinas/git/fabric-samples/test-network/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem --channelID mychannel --name trade --peerAddresses localhost:7051 --tlsRootCertFiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/tlsca/tlsca.org1.example.com-cert.pem --peerAddresses localhost:9051 --tlsRootCertFiles /home/miguel-salinas/git/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/tlsca/tlsca.org2.example.com-cert.pem --version 1.0 --sequence 1
+ res=0
2024-11-20 22:39:53.821 CET 0001 INFO [chaincodeCmd] ClientWait -> txid [dd59b3b8e66a9f4fdf6195c32aa0adfff82437ab3a560443abaa28c17e6e1551] committed with status (VALID) at localhost:9051
2024-11-20 22:39:53.824 CET 0002 INFO [chaincodeCmd] ClientWait -> txid [dd59b3b8e66a9f4fdf6195c32aa0adfff82437ab3a560443abaa28c17e6e1551] committed with status (VALID) at localhost:7051
Chaincode definition committed on channel 'mychannel'
Using organization 1
Querying chaincode definition on peer0.org1 on channel 'mychannel'...
Attempting to Query committed status on peer0.org1, Retry after 3 seconds.
+ peer lifecycle chaincode querycommitted --channelID mychannel --name trade
+ res=0
Committed chaincode definition for chaincode 'trade' on channel 'mychannel':
Version: 1.0, Sequence: 1, Endorsement Plugin: escc, Validation Plugin: vscc, Approvals: [Org1MSP: true, Org2MSP: true]
Query chaincode definition successful on peer0.org1 on channel 'mychannel'
Using organization 2
Querying chaincode definition on peer0.org2 on channel 'mychannel'...
Attempting to Query committed status on peer0.org2, Retry after 3 seconds.
+ peer lifecycle chaincode querycommitted --channelID mychannel --name trade
+ res=0
Committed chaincode definition for chaincode 'trade' on channel 'mychannel':
Version: 1.0, Sequence: 1, Endorsement Plugin: escc, Validation Plugin: vscc, Approvals: [Org1MSP: true, Org2MSP: true]
Query chaincode definition successful on peer0.org2 on channel 'mychannel'
Chaincode initialization is not required
```

Containers deployed:

```shell
$ docker ps
CONTAINER ID   IMAGE                                                                                                                                                                    COMMAND                  CREATED          STATUS          PORTS                                                                                                                             NAMES
86f84497e846   dev-peer0.org2.example.com-trade_1.0-9288fd658c1c24e8de7bbbe51b7130781e20c142915e1c7f088f40165700f450-2c658049c608bfbdcedb24ef25e6854bdbc6cd601943f095ffffe1276f5e7349   "docker-entrypoint.s…"   18 seconds ago   Up 17 seconds                                                                                                                                     dev-peer0.org2.example.com-trade_1.0-9288fd658c1c24e8de7bbbe51b7130781e20c142915e1c7f088f40165700f450
68f11bdcc2dc   dev-peer0.org1.example.com-trade_1.0-9288fd658c1c24e8de7bbbe51b7130781e20c142915e1c7f088f40165700f450-2e5d8dd0b09b6e008c398d35f0061c43ff88c1569933839f74f8cd84a991eb3e   "docker-entrypoint.s…"   18 seconds ago   Up 17 seconds                                                                                                                                     dev-peer0.org1.example.com-trade_1.0-9288fd658c1c24e8de7bbbe51b7130781e20c142915e1c7f088f40165700f450
635a44771b7d   hyperledger/fabric-peer:latest                                                                                                                                           "peer node start"        5 minutes ago    Up 5 minutes    0.0.0.0:9051->9051/tcp, :::9051->9051/tcp, 7051/tcp, 0.0.0.0:9445->9445/tcp, :::9445->9445/tcp                                    peer0.org2.example.com
5fa5974b4714   hyperledger/fabric-orderer:latest                                                                                                                                        "orderer"                5 minutes ago    Up 5 minutes    0.0.0.0:7050->7050/tcp, :::7050->7050/tcp, 0.0.0.0:7053->7053/tcp, :::7053->7053/tcp, 0.0.0.0:9443->9443/tcp, :::9443->9443/tcp   orderer.example.com
d043f3edb050   hyperledger/fabric-peer:latest                                                                                                                                           "peer node start"        5 minutes ago    Up 5 minutes    0.0.0.0:7051->7051/tcp, :::7051->7051/tcp, 0.0.0.0:9444->9444/tcp, :::9444->9444/tcp                                              peer0.org1.example.com
6d922e3d40c8   hyperledger/fabric-ca:latest                                                                                                                                             "sh -c 'fabric-ca-se…"   5 minutes ago    Up 5 minutes    0.0.0.0:7054->7054/tcp, :::7054->7054/tcp, 0.0.0.0:17054->17054/tcp, :::17054->17054/tcp                                          ca_org1
3c7a47f21fa8   hyperledger/fabric-ca:latest                                                                                                                                             "sh -c 'fabric-ca-se…"   5 minutes ago    Up 5 minutes    0.0.0.0:9054->9054/tcp, :::9054->9054/tcp, 7054/tcp, 0.0.0.0:19054->19054/tcp, :::19054->19054/tcp                                ca_orderer
1c2f3c6fb6a6   hyperledger/fabric-ca:latest                                                                                                                                             "sh -c 'fabric-ca-se…"   5 minutes ago    Up 5 minutes    0.0.0.0:8054->8054/tcp, :::8054->8054/tcp, 7054/tcp, 0.0.0.0:18054->18054/tcp, :::18054->18054/tcp  
```

- Copy ca.org1.example.com-cert.pem generated from to api microservice:

```
../fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/ca/ca.org1.example.com-cert.pem
```

- Copy connection-org1.yaml generated from to api microservice:

```
../fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/connection-org1.yaml
```