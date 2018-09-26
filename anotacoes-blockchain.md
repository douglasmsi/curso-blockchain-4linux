https://medium.com/coinmonks/how-to-add-site-to-ipfs-and-ipns-f121b4cfc8ee
https://medium.com/clebertech/o-guia-definitivo-do-ipfs-2e87d684e355

2007-2008-2009
	Bitcoin


Sistema de transferencia
	cobram pela transferencia (bitcoin ou moeda)
	Mineradores ganham (bitcoin ou moeda)
	Dificuldade de mineracao

ecossistema -> criptomoeda

Blockchain
	Update only
	Livro distribuido
	Interdependencia ordem/hash (proof of work)

Blockchain Permissionadas
	Alem de update only, livro distribuido, interdependencia ordem/hash.
	Em redes permissionadas e necessario o consensus.


Arvore de merkle

Procurar sobre NONCE

Blockchain
	-> Cadeia de blocos
        -> Append Only
	-> Imutavel

Rede permissionada
	Pessoas ou organizacoes nessa rede sao conhecidas, mas nao confiam entre eles. Por isso e necessario uma concordancia.


Exemplo de ordem em blockchain/bitcoin - Juquinha -> 0.001BR -> Maria -> Essa ordem entra no bitcoin e aproximadamente 3 dias ou menos existe a confirmacao

Na permissionada

Exemplo de ordem em permissionada

#######################################

Multichain -> Fazer o seu -> Bitcoin
Corda -> Financeiro(puro)
Hyperledger fabric -> Blockchain GENERICO

########################################
Necessario para aprender Hyperledger fabric

Tecnologias Linux -> Rede, comandos, troubleshooting
Tudo deve rodar em docker e as imagens sao Ubuntu
Seguro -> Certificados
	Entender HTTPS - Identificar e criptografar


No hyperledger teremos um certificado para conexao
Depois mais um certificado sera utilizado para autorizacao e autenticacao

openssl
CA Autoridade certificadora - Assina (valida) certificado (da fe)
Voce gera uma chave privada + CSR
Recebe da certificadora a chave publica assinada = certificado.

Go lang - Protobuffers - GRPC


############################################3
3 dia
Certificados - Nao usa x509
	MSP - Certificados de autenticacao e autorizacao entre organizacoes
	TLS -  Certificados de conexao entre peers
	SHA256SUM Publico (Hexa->String) - Usado para manter historico de certificados revogados.


Configuracoes - Configtx
	Peers - Peers internos, sem comunicacao com mundo externo
	Anchor - Deve ser o unico peer que expoe para outras redes / mundo externo da organizacao


