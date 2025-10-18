# Steps to clone GitHub repo from remote (github) to local (laptop)

## 1. Check if you already have an SSH key

> **ls -al ~/.ssh**

```plaintext
    Look for files like:

    id_rsa and id_rsa.pub, or

    id_ed25519 and id_ed25519.pub

    If you see .pub files, you already have an SSH key.
    If not, you’ll need to create a new one.
```

## 2. Create a new SSH key (if missing)

> **ssh-keygen -t ed25519 -C "idesta705@gmail.com"**

```plaintext
    ssh-keygen -t ed25519 -C "idesta705@gmail.com"
    Generating public/private ed25519 key pair.
    Enter file in which to save the key (/root/.ssh/id_ed25519): 
    Enter passphrase for "/root/.ssh/id_ed25519" (empty for no passphrase): 
    Enter same passphrase again: 
    Your identification has been saved in /root/.ssh/id_ed25519
    Your public key has been saved in /root/.ssh/id_ed25519.pub
    The key fingerprint is:
    SHA256:CjyNhRQZeSBBQT3FXkhynZzilGq3JuXQ7eUNiFVSFhQ idesta705@gmail.com
    The key's randomart image is:
    +--[ED25519 256]--+
    | o*+*X+=.*Eo     |
    |   o=+B Bo       |
    |    .O.* .       |
    |   .++B o o      |
    |   .==.oSo o     |
    |    .o+.. . .    |
    |     o.          |
    |                 |
    |                 |
    +----[SHA256]-----+
```

## 3. Start the SSH agent and add your key

> **eval "$(ssh-agent -s)"**

> **ssh-add ~/.ssh/id_ed25519**

```plaintext
    root@israel-vostro3520:/home/Github# eval "$(ssh-agent -s)"
    Agent pid 15379

    root@israel-vostro3520:/home/Github# ssh-add ~/.ssh/id_ed25519
    Identity added: /root/.ssh/id_ed25519 (idesta705@gmail.com)
```

## 4. Add your SSH key to GitHub

- **Copy your public key**

    > **cat ~/.ssh/id_ed25519.pub**

    ```plaintext
        ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIFf9Wi9UTlJUPr1ZM7tDHpYBh8ozqy5+pxvsaZm3YS0s idesta705@gmail.com
    ```

- **Go to your Github page**

    ```plaintext
        Go to https://github.com/settings/keys
        Click New SSH key
        Give it a name (like My Laptop Key)
        Paste the key content
        Click Add SSH key
    ```

## 5. Test your connection

> **ssh -T git@github.com**

```plaintext
Hi idesta! You've successfully authenticated, but GitHub does not provide shell access.
```

## 6. Try cloning

> **git clone git@github.com:idesta/aws-md.git**