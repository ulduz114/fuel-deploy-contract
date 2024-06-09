# fuel-deploy-contract

### Install Dependencies 
```
sudo apt update
sudo apt upgrade -y
sudo apt-get install curl screen -y 
```
### Installing RUST

```curl --proto '=https' --tlsv1.3 https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
rustc --version
rustup install stable
rustup update stable
rustup default stable
```

### Install GIT
```
sudo apt install git -y 
```

### Install Fuel Toolchain

```
curl https://install.fuel.network | sh
source /root/.bashrc
```
### Setting FUELUP

```
fuelup toolchain install latest
fuelup self update
fuelup update && fuelup default latest
```
### Creating PROJECT

```
mkdir fuel-project && cd fuel-project
forc new counter-contract
nano counter-contract/src/main.sw
```

Clear everything and paste below code

```
contract;
 
storage {
    counter: u64 = 0,
}
 
abi Counter {
    #[storage(read, write)]
    fn increment();
 
    #[storage(read)]
    fn count() -> u64;
}
 
impl Counter for Contract {
    #[storage(read)]
    fn count() -> u64 {
        storage.counter.read()
    }
 
    #[storage(read, write)]
    fn increment() {
        let incremented = storage.counter.read() + 1;
        storage.counter.write(incremented);
    }
}

```
##Save and exit with Ctrl X + y  and click ENTER ##

### Build Contract

```
cd counter-contract
forc build
```

### create wallet

you will need your FUEL wallet here, i will be importing my seed pharse , if you dont have wallet , [install](https://wallet.fuel.network/docs/install/) and create it in your local machine and import it here

```forc wallet import ```

```forc wallet account new```

```forc wallet accounts```

### deploy contract 

```forc deploy --testnet  ```



















