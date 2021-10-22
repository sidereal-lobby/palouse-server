# JAM

## 1. TYLER DO THIS (setup session for Ryan)
```
tmux -S /tmp/stonks_socket new -s stonks_session
sudo chgrp shrewdness /tmp/stonks_socket
```

## 2. RYAN DO THIS (setup session for Tyler)
```
tmux -S /tmp/sparkle_socket new -s sparkle_session
sudo chgrp shrewdness /tmp/sparkle_socket
```

## 3. THEN TYLER DO THIS (read only Ryan's session)
```
tmux -S /tmp/sparkle_socket attach -t sparkle_session -r
```

## 4. AND RYAN DO THIS (read only Tyler's session)
```
tmux -S /tmp/stonks_socket attach -t stonks_session -r
```

# DEVELOPMENT

```
yarn install
yarn start
```

To work with the CSS: run `sass --watch style.sass:style.css`


# SPECTATOR INSTRUCTIONS

 - ssh into the secret server.
 - Attach to Tyler's session: `tmux -S /tmp/stonks_socket attach -t stonks_session -r`
 - Open a new tab or ssh into the server again.
 - Attach to Ryan's session: `tmux -S /tmp/sparkle_socket attach -t sparkle_session -r`
 - Open the `palouse` script on your norns and setup the config file. You should see a smiley face when the connection is established.

## SERVER SETUP

```
adduser stonks
adduser sparkle
usermod -aG sudo stonks
usermod -aG sudo sparkle
groupadd -g 666 shrewdness
usermod -aG shrewdness stonks
usermod -aG shrewdness sparkle
cp -r /root/.ssh /home/stonks
cp -r /root/.ssh /home/sparkle
chown -R stonks: /home/stonks
chown -R sparkle: /home/sparkle
```