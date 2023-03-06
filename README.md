# Nolus-Protocol-Snapshot
![Описание](https://avatars.githubusercontent.com/u/103436687?s=200&v=4(jpg))



I provide a snapshot for Nolus Protocol

Guide how to start:

Start Nolus from snapshot
Now we can start our node on the new server from snapshot.

First, we stop the node:
`sudo systemctl stop nolusd`

You can copy the **addrbook.json** from the old server to a new one so your node can find peers after the restart.

We going to reset our node. This will erase your node database. If you are already running validator, be sure you backed up your **priv_validator_key.json** The command does not wipe the file. However, you should have a backup of it.

`nolusd tendermint unsafe-reset-all --home $HOME/.nolus --keep-addr-book`

Now we can download the archive.
`cd $HOME`

`wget http://144.168.47.230:8000/nolus-archive.tar.gz`

After the download is finished, we can unpack the archive directly to our database location

`cd $HOME`

`tar -zxvf nolus-archive.tar.gz --strip-components 1`

Restart your node

`sudo systemctl restart nolusd && sudo journalctl -u nolusd -f -o cat`

If everything works correctly, your node should start from the same height at which snapshot was taken.

