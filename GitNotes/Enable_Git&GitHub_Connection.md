<h1>Enable Connection Between Git and GitHub</h1>
<ol>
    <li>
        Download Git, which includes Git Bash for Windows. 
    </li>
    <li>
        Create an account on GitHub. <br />
    </li>
    <li>
        Open <strong>Command Prompt (CMD)</strong>. 
    </li>
    <li>
        In CMD, enter the following command to set your Git username: 
        <code>git config --global user.name "<em>your user name</em>"</code> 
    </li>
    <li>
        In CMD, enter this command to set your Git email: 
        <code>git config --global user.email "<em>your email for GitHub</em>"</code> <br />
    </li>
    <li>
        Open <strong>Git Bash</strong>. 
    </li>
    <li>
        In Git Bash, start the SSH agent with: <code>eval "$(ssh-agent -s)"</code> 
    </li>
    <li>
        Add your private SSH key with: <code>ssh-add ~/.ssh/id_rsa</code> 
    </li>
    <li>
        Display your public SSH key by typing: <code>cat ~/.ssh/id_rsa.pub</code>. 
        <ul>
            After pressing Enter, it will show a token starting with "ssh-rsa" and ending with your email. 
        </ul>
    </li>
    <li>
        Copy this token. <br />
    </li>
    <li>
        Open <strong>GitHub</strong> in a browser. 
    </li>
    <li>
        Navigate to <strong>Settings</strong> -> <strong>SSH and GPG keys</strong> -> <strong>New SSH key</strong>
        <ul>
            Paste the token into the "Key" field, and click "Add SSH key." 
        </ul>
    </li>
    <li>
        Return to <strong>Command Prompt (CMD)</strong>. 
    </li>
    <li>
        Test the connection by entering: 
        <code>ssh -T git@github.com</code>. 
        <ul>
            If it replies: <code>Hi "<em>Your User Name</em>" You've successfully authenticated, but GitHub does not provide shell access.</code>, you’re all set! 
        </ul>
    </li>
</ol>