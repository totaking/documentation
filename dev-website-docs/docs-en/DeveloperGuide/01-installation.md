
<h1 align="center">Ontology </h1>
<h4 align="center">Version 1.0 </h4>

[![GoDoc](https://godoc.org/github.com/ontio/ontology?status.svg)](https://godoc.org/github.com/ontio/ontology)




## Contents

<!-- TOC -->

- [Build development environment](#build-development-environment)
- [Get Ontology](#get-ontology)
    - [Get from release](#get-from-release)
    - [Get from source code](#get-from-source-code)
- [Run Ontology](#run-ontology)
    - [MainNet sync node](#mainnet-sync-node)
    - [Public test network Polaris sync node (TestNet)](#public-test-network-polaris-sync-node-testnet)
    - [Testmode](#testmode)
    - [Run in docker](#run-in-docker)
- [Some examples](#some-examples)
    - [ONT transfer sample](#ont-transfer-sample)
    - [Query transfer status sample](#query-transfer-status-sample)
    - [Query account balance sample](#query-account-balance-sample)

<!-- /TOC -->

## Build development environment
The requirements to build Ontology are:

- Golang version 1.9 or later
- Glide (a third party package management tool)
- Properly configured Go language environment
- Golang supported operating system

## Get Ontology

### Get from release
- You can download the latest Ontology binary file with ` curl https://dev.ont.io/ontology_install | sh `.

- You can download other versions at [release page](https://github.com/ontio/ontology/releases).

### Get from source code

Clone the Ontology repository into the appropriate $GOPATH/src/github.com/ontio directory.

```
$ git clone https://github.com/ontio/ontology.git
```
or
```
$ go get github.com/ontio/ontology
```
Fetch the dependent third party packages with glide.

```
$ cd $GOPATH/src/github.com/ontio/ontology
$ glide install
```

Build the source code with make.

```
$ make all
```

After building the source code sucessfully, you should see two executable programs:

- `ontology`: the node program/command line program for node control.
- `tools/sigsvr`: (optional) Ontology Signature Server - sigsvr is a RPC server for signing transactions for some special requirements. Detailed docs can be found [here](https://github.com/ontio/documentation/blob/master/docs/pages/doc_en/Ontology/sigsvr_en.md).

## Run Ontology

You can run Ontology in four different modes:

1) MainNet (./ontology)
2) TestNet (./ontology --networkid 2)
3) Testmode (./ontology --testmode)
4) Docker

E.g. for Windows (64-bit), use command prompt and cd to the dirctory where you installed the Ontology release, then type `start ontology-windows-amd64.exe --networkid 2`. This will sync to TestNet and you can explore further by the help command `ontology-windows-amd64.exe --networkid 2 help`.

### MainNet sync node

Run ontology directly

   ```
	./ontology
   ```
then you can connect to Ontology MainNet.

### Public test network Polaris sync node (TestNet)

Run ontology directly

   ```
	./ontology --networkid 2
   ```
   
Then you can connect to the Ontology TestNet.

### Testmode

Create a directory on the host and store the following files in the directory:
- Node program `ontology`
- Wallet file `wallet.dat` (`wallet.dat` can be generated by `./ontology account add -d`)

Run command `$ ./ontology --testmode` can start single-host testnet.

Here's a example of a single-host configuration:

- Directory structure

    ```shell
    $ tree
    └── ontology
        ├── ontology
        └── wallet.dat
    ```

### Run in docker

Please ensure there is a docker environment in your machine.

1. Make docker image

    - In the root directory of source code, run `make docker`, it will make an Ontology image in docker.

2. Run Ontology image

    - Use command `docker run ontio/ontology` to run Ontology；

    - If you need to allow interactive keyboard input while the image is running, you can use the `docker run -ti ontio/ontology` command to start the image;

    - If you need to keep the data generated by image at runtime, you can refer to the data persistence function of docker (e.g. volume);

    - If you need to add Ontology parameters, you can add them directly after `docker run ontio/ontology` such as `docker run ontio/ontology --networkid 2`.
     The parameters of ontology command line refer to [here](./docs/specifications/cli_user_guide.md).

## Some examples

### ONT transfer sample
 -- from: transfer from； -- to: transfer to； -- amount: ONT amount；
```shell
 ./ontology asset transfer  --from=ARVVxBPGySL56CvSSWfjRVVyZYpNZ7zp48 --to=AaCe8nVkMRABnp5YgEjYZ9E5KYCxks2uce --amount=10
```
If the asset transfer is successful, the result will display as follows:

```shell
Transfer ONT
  From:ARVVxBPGySL56CvSSWfjRVVyZYpNZ7zp48
  To:AaCe8nVkMRABnp5YgEjYZ9E5KYCxks2uce
  Amount:10
  TxHash:437bff5dee9a1894ad421d55b8c70a2b7f34c574de0225046531e32faa1f94ce
```
TxHash is the transfer transaction hash, and we can query a transfer result by the TxHash.
Due to block time, the transfer transaction will not be executed before the block is generated and added.

If you want to transfer ONG, just add --asset=ong flag.

Note that ONT is an integer and has no decimals, whereas ONG has 9 decimals. For detailed info please read [Everything you need to know about ONG](https://medium.com/ontologynetwork/everything-you-need-to-know-about-ong-582ed216b870).

```shell
./ontology asset transfer --from=ARVVxBPGySL56CvSSWfjRVVyZYpNZ7zp48 --to=ARVVxBPGySL56CvSSWfjRVVyZYpNZ7zp48 --amount=95.479777254 --asset=ong
```
If transfer of the asset succeeds, the result will display as follows:

```shell
Transfer ONG
  From:ARVVxBPGySL56CvSSWfjRVVyZYpNZ7zp48
  To:AaCe8nVkMRABnp5YgEjYZ9E5KYCxks2uce
  Amount:95.479777254
  TxHash:e4245d83607e6644c360b6007045017b5c5d89d9f0f5a9c3b37801018f789cc3
```

Please note, when you use the address of an account, you can use the index or label of the account instead. Index is the sequence number of a particular account in the wallet. The index starts from 1, and the label is the unique alias of an account in the wallet.

```shell
./ontology asset transfer --from=1 --to=2 --amount=10
```

### Query transfer status sample

```shell
./ontology info status <TxHash>
```

For Example:

```shell
./ontology info status 10dede8b57ce0b272b4d51ab282aaf0988a4005e980d25bd49685005cc76ba7f
```

Result:

```shell
Transaction:transfer success
From:AXkDGfr9thEqWmCKpTtQYaazJRwQzH48eC
To:AYiToLDT2yZuNs3PZieXcdTpyC5VWQmfaN
Amount:10
```

### Query account balance sample

```shell
./ontology asset balance <address|index|label>
```

For Example:

```shell
./ontology asset balance ARVVxBPGySL56CvSSWfjRVVyZYpNZ7zp48
```

or

```shell
./ontology asset balance 1
```
Result:
```shell
BalanceOf:ARVVxBPGySL56CvSSWfjRVVyZYpNZ7zp48
  ONT:989979697
  ONG:28165900
```

For further examples, please refer to the [CLI User Guide](https://ontio.github.io/documentation/cli_user_guide_en.html).


