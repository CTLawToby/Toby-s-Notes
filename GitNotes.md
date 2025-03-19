<h1>Git & Github</h1>

<h2>Enable Connection Between Git and GitHub</h2>
<p>
    <strong>1.</strong> Download Git, which includes Git Bash for Windows. <br />
    <strong>2.</strong> Create an account on GitHub. <br /><br />
    <strong>3.</strong> Open <strong>Command Prompt (CMD)</strong>. <br />
    <strong>4.</strong> In CMD, enter the following command to set your Git username: 
    <code>git config --global user.name "<em>your user name</em>"</code> <br />
    <strong>5.</strong> In CMD, enter this command to set your Git email: 
    <code>git config --global user.email "<em>your email for GitHub</em>"</code> <br /><br />
    <strong>6.</strong> Open <strong>Git Bash</strong>. <br />
    <strong>7.</strong> In Git Bash, start the SSH agent with: 
    <code>eval "$(ssh-agent -s)"</code> <br />
    <strong>8.</strong> Add your private SSH key with: 
    <code>ssh-add ~/.ssh/id_rsa</code> <br />
    <strong>9.</strong> Display your public SSH key by typing: 
    <code>cat ~/.ssh/id_rsa.pub</code>. <br />
         After pressing Enter, it will show a token starting with "ssh-rsa" and ending with your email. <br />
    <strong>10.</strong> Copy this token. <br /><br />
    <strong>11.</strong> Open <strong>GitHub</strong> in a browser. <br />
    <strong>12.</strong> Navigate to <strong>Settings</strong> -> <strong>SSH and GPG keys</strong> -> <strong>New SSH key</strong><br />
      Paste the token into the "Key" field, and click "Add SSH key." <br /><br />
    <strong>13.</strong> Return to <strong>Command Prompt (CMD)</strong>. <br />
    <strong>14.</strong> Test the connection by entering: 
    <code>ssh -T git@github.com</code>. <br />
        If it replies: <code>Hi "<em>Your User Name</em>" You've successfully authenticated, but GitHub does not provide shell access.</code>, you’re all set! <br />
</p>
