# Configure SSH access to Github

## Single account with single device

1. Generate ssh-key

    ``` bash
    ssh-keygen -t rsa -C "your_email_address"
    ```

    You may need to input the filename to save the key and the passphrase, but can press enter directly. The default path for saving key pairs is `~/.ssh/`, `id_rsa` and `id_rsa.pub` is the private and public key.

2. Add public key to Github

    Open [Github](https://www.github.com), select **Account Settings - SSH Keys**, click **Add SSH Key**, and paste the complete string in `id_rsa.pub` to the editing box. You can test the ssh access using `ssh -T git@github.com`，“You've successfully authenticated, but GitHub does not provide shell access” will show if no error occurs.

3. Configure username and email

    ``` bash
    git config --global user.name "your_name"
    git config --global user.email "your_email_address"
    ```

    Remove `--global` if you do not want to set them globally.

## Multiple accounts with single device

1. Generate ssh-keys

    Execute the command for each account.

    ``` bash
    ssh-keygen -t rsa -C "your_another_email_address"
    ```

    Note that you need to input different filenames for key pairs of multiple accounts, for example `~/.ssh/id_rsa_private` and `~/.ssh/id_rsa_work`.

2. Add public key to another github account

3. Add private key to ssh agent

    For all rsa keys other than `~/.ssh/id_rsa`, you need to add them to ssh agent manually.

    ``` bash
    ssh-add ~/.ssh/id_rsa_work
    ```

4. Modify SSH configuration file

    New a configuration file `~/.ssh/config` and add the following lines.

    ```
    Host github.com # Alias
        HostName github.com # Address
        User git # Optional
        IdentityFile ~/.ssh/id_rsa # Path of private key
    Host github_work
        HostName github.com
        IdentityFile ~/.ssh/id_rsa_work
    ```

5. Access github using different accounts

    You can add an origin using a different account.

    ``` bash
    git remote add origin git@github_work:workUserName/RepoName.git
    ```

## Single account with multiple devices
Generate ssh-key for each device and add the public key to your account.