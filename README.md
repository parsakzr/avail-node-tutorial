# Avail Node Tutorial

## Changing Node Wallet

1. Login to your Avail Node via SSH (PuTTY, Termius, etc.)
2. Run the following to backup the current configuration:
    * {APP_NAME} is the name you selected for your app chain

    ```bash
    cd ~/.madara/app-chains/{APP_NAME}
    cp da-config.json da-config-backup.json
    ```

3. edit the `da-config.json` file with editor of your choice (nano, vim, etc.)

    ```bash
    nano da-config.json
    ```

    * Change the `seed` and `address` values to the new wallet's values.

    ```json
    {"ws_provider":"wss://goldberg.avail.tools:443/ws", "mode":"sovereign", "seed": "DESIRED WALLET'S SEED PHRASE","app_id":0,"address":"DESIRED WALLET'S ADDRESS"}
    ```

    * Note: you can enter the mnemonic 12-word phrase as your seed as well.
    * example: "seed": "jelly fun printer ... serve"

4. Save and exit the editor. for nano: `Ctrl+X` -> `Y` -> `Enter`

## Rerun the node with the updated Config

5. Run the following command to go to the madara directory

    ```bash
    cd ~/madara-cli/target/release
    ```

6. Kill the running node process on screen session

    6.1. List the running sessions:

    ```bash
    session -ls
    ```

    * Outputs something like this

    ```bash
    # There are screens on:
    #   53432.roller    (02/10/24 14:53:50)     (Detached)
    #   ...
    ```

    6.2 Kill the process with the session id, example `53432.roller`. change based on your output.

    ```bash
    screen -XS 53432.roller quit
    ```

    * alternatively you can kill all the screen sessions instead of 6.1. and 6.2. by running `killall screen`

7. After killing the node process, Start a new screen session:

    ```bash
    screen -s ANYNAME
    ```

    * ANYNAME can be anything like roller, node, your app name, etc.

8. Run the node again:

    ```bash
    ./madara run
    ```

    * choose your app_name, then `Y` and it should continue importing the blocks where you left off.

9. To run the explorer too, switch to a new screen by pressing `Ctrl+A` then `D`
 and run:

    ```bash
    ./madara explorer --host=IPADDRESS
    ```

    * Replace IPADDRESS with your IP Address.

10. Everything should be running now. No need to change anything else!
