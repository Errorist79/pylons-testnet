# pylons-testnet

- Go version: [v1.17+](https://golang.org/dl/)
- Pylonsd version: [v0.3.1](https://github.com/Pylons-tech/pylons/releases/tag/v0.3.1)

         ensure GOPATH is set properly to point to the go directory of your Go installation: GOPATH = $HOME/go
         ensure PATH is set properly to point to the bin folder of your Go installation: PATH = $GOPATH/bin
         pylonsd binary(link above or from 'make install' on repo clone/source) should be put in Go's bin folder

## Testnet Restart

1. Get the proper version (v0.3.1) and make install the pylonsd binary

 

2. Run pylonsd version to verify the version is correct.  please reach out if the version is wrong.

   ```shell
   $ pylonsd version
   ``` 

3. Run pylonsd-unsafe-reset-all

   ```shell
   $ pylonsd unsafe-reset-all
   ```

4. Download the correct genesis.json file  and copy the file to ~/.pylons/config/genesis.json

   ```shell
    link: https://github.com/Pylons-tech/pylons-testnet/blob/main/genesis.json
   ```

5. Run pylonsd validate-genesis .  Please reach out if there are issues

   ```shell
    $ pylonsd validatate-genesis

   ```
   
6. Add the seeds in `~/.pylons/config/config.toml and post your seed to the validator chat

   ```shell
    Seeds: 
    6294a76689d9c5455ab83f7070b6631f33ecdbf2@104.227.239.50:26656; 
    25e7ef64b41a636e3fb4e9bb1191b785e7d1d5cc@46.166.140.172:26656;

   ```


7. Run pylonsd validate-genesis .  Please reach out if there are issues

   ```shell
    $ pylonsd validatate-genesis

   ```


8. Run pylonsd start

   ```shell
    $ pylonsd start

   ```

9. Check the balance of your pyloxxxxx address. Please reach out to be funded from the faucet if you do not have funds (1,000,000ubedrock)

   ```shell
    $ pylonsd query bank balances <delegator-addresss>

   ```
   
10. Create your validator.

   ```shell
    $ pylonsd tx staking create-validator \
      --amount=1000000ubedrock \
      --pubkey=$(pylonsd tendermint show-validator) \
      --moniker=<moniker> \
      --chain-id=pylons-testnet \
      --commission-rate="0.10" \
      --commission-max-rate="0.20" \
      --commission-max-change-rate="0.01" \
      --min-self-delegation="1000000" \
      --gas="auto" \
      --gas-adjustment="1.5" \
      --from=<key-name>

   ```
11. Self-delegate 1000000ubedrock 

   ```shell
   $ pylonsd tx staking delegate pylovaloperxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 1000000ubedrock --from=<key-name> --broadcast-mode=async --chain-id=pylons-testnet -y
   ```
 