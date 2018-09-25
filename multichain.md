Segunda VM
$ curl -OL https://www.multichain.com/download/multichain-latest.tar.gz

$ tar zxvf multichain-latest.tar.gz

$ multichain-util create chain1

$ multichain-1.0.6/multichaind chain1 -daemon
MultiChain 1.0.6 Daemon (latest protocol 10011)
Starting up node...
Looking for genesis block...
Genesis block found
Other nodes can connect to this node using: multichaind chain1@10.0.2.15:6291
This host has multiple IP addresses, so from some networks: multichaind chain1@192.168.56.101:6291
Listening for API requests on port 6290 (local only - see rpcallowip setting)
Node ready.

$ ss -nltop|grep multichain
LISTEN     0      128    127.0.0.1:6290                     *:*                   users:(("multichaind",pid=1240,fd=26))
LISTEN     0      128          *:6291                     *:*                   users:(("multichaind",pid=1240,fd=28))
LISTEN     0      128        ::1:6290                    :::*                   users:(("multichaind",pid=1240,fd=25))
LISTEN     0      128         :::6291                    :::*                   users:(("multichaind",pid=1240,fd=27))


Criar e Listar Streams

multichain-1.0.6/multichain-cli chain1
chain1: liststreams            
chain1: listpermissions
chain1: create stream strTST false  
chain1: listpermissions strTST.*
chain1: liststreams            
chain1: publish strTST key1 vacamarela                      
{"method":"publish","params":["strTST","key1","vacamarela"],"id":"98527787-1535120717","chain_name":"chain1"}

error code: -8
error message:
Item data should be hexadecimal string

Usar https://codebeautify.org/string-hex-converter com “Hello Multichain!” e “Hi Again Multichain!”

chain1: publish strTST key1 48656c6c6f204d756c7469636861696e21

chain1: publish strTST key1 48656c6c6f204d756c7469636861696e21  
{"method":"publish","params":["strTST","key1","48656c6c6f204d756c7469636861696e21"],"id":"46773369-1535121691","chain_name":"chain1"}

453233ee2d950fdabe82c7a3afa2eec540755954165fbeb9cd48b102d5fd79f7
chain1: publish tstST key1 736f6d65206f7468657220646174615fd79f7

chain1: subscribe strTST

chain1: liststreamkeyitems strTST key1

Criar e Listar Assets

multichain-1.0.6/multichain-cli chain1
chain1: assets (valores, tokens, criptomoedas)

Gere 10 cursos em posse de 1B, divisiveis em 10 cada um:   
chain1: issue 1Bz2J2jR8b2i9cAja5LjNSWRhVbFNieTAti5No cursos 10 0.1       

chain1: listassets
{"method":"listassets","params":[],"id":"12262334-1535122531","chain_name":"chain1"}

[
    {
        "name" : "cursos",
        "issuetxid" : "80556946bec20c28de647566344aaf5d6e15f84924f0eaf6afc9835d1ae35df4",
        "assetref" : "126-266-21888",
        "multiple" : 10,
        "units" : 0.10000000,
        "open" : false,
        "details" : {
        },
        "issueqty" : 10.00000000,
        "issueraw" : 100,
        "subscribed" : false
    }
]
chain1: gettotalbalances
{"method":"gettotalbalances","params":[],"id":"64945662-1535122551","chain_name":"chain1"}

[
    {
        "name" : "cursos",
        "assetref" : "126-266-21888",
        "qty" : 10.00000000
    }
]








Segundo nó: tente conectar
multichain-1.0.6/multichaind chain1@192.168.56.101:6291&

Use as sugestões para ajustar as permissões no primeiro nó:
multichain-cli chain1
chain1: grant 15dmUQS353mMqEAUJkqq5n3JtfczcpReK2pXjk connect,send,receive

No primeiro nó
chain1: sendwithdata 15dmUQS353mMqEAUJkqq5n3JtfczcpReK2pXjk '{"cursos":.5}' '{"for":"tstST","key":"transfer","data":"e9206a7573746f206d65746164696e6861"}'

Teste o segundo nó de novo:
multichain-1.0.6/multichaind chain1@192.168.56.101:6291&

Ainda  no segundo nó:
multichain-1.0.6/multichain-cli chain1
chain1: gettotalbalances
chain1: listwallettransactions
chain1: sendwithdata 1Bz2J2jR8b2i9cAja5LjNSWRhVbFNieTAti5No '{"cursos":.5}' '{"for":"tstST","key":"transfer","data":"6d65746164696e68612c206d7569746f20706f75636f"}'
…
This wallet contains no addresses with permission to write to this stream and global send permission.
No primeiro nó
chain1: grant 15dmUQS353mMqEAUJkqq5n3JtfczcpReK2pXjk send
chain1: grant 15dmUQS353mMqEAUJkqq5n3JtfczcpReK2pXjk tstST.write   

Teste o envio de novo no segundo nó e verifique o balanço   
chain1: sendwithdata 1Bz2J2jR8b2i9cAja5LjNSWRhVbFNieTAti5No '{"cursos":.5}' '{"for":"tstST","key":"transfer","data":"6d65746164696e68612c206d7569746f20706f75636f"}'
chain1: gettotalbalances
chain1: listwallettransactions

chain1: listblocks 0-100                                                                                                                                  

