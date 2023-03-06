# Nolus snapshot (updated every 24 hours)


Stop the node and remove db
```
sudo systemctl stop nolusd
```
Save priv_validator_state backup and delete data
```
cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
rm -rf $HOME/.nolus/data
```
Download snapshot, and move priv_validator_state back
```
mkdir $HOME/.nolus/data
wget -O - http://65.108.9.230/nolus/nolus-rila_latest.tar | tar xf - -C $HOME/.nolus/data
mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json
```
Start node 
```
sudo systemctl start nolusd && sudo journalctl -u nolusd -f --no-hostname -o cat
```
