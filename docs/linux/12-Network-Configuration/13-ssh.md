<h1>The ssh Command</h1>

Connect securely to a **remote machine** over the network to run commands.

<h3>Basic Usage</h3>


```bash
ssh hostname          # Logs in using your current username on the remote host
ssh username@hostname # Logs in with a specific username
```


<h3>Connection Steps</h3>

1. First connection may prompt to **verify the host key**:

    ```
    The authenticity of host 'test (127.0.0.1)' can't be established.
    RSA key fingerprint is ...
    Are you sure you want to continue (yes/no)? yes
    ```

2. Enter the **password** for the remote user.
3. After login, you can run commands remotely:

    ```bash
    bob@test:~$ date
    Fri Oct 4 16:14:43 CDT 2013
    ```
4. Exit Remote Session : `exit`
    * Returns you to the **local machine**.
    *  Be careful: running `exit` in nested SSH sessions may **close your terminal window**.

---

> `ssh` is essential for **remote system administration and secure connections**.
