<h1>Installing Docker on Ubuntu.</h1>

<p>FFirst of all, remove possible old versions of Docker.
</p>

    sudo apt-get remove docker docker-engine docker.io

<p>Then, update the package database.
</p>

    sudo apt-get update

<p>Now add the official Docker repository GPG key to the system.
</p>

    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

<p>Add the Docker repository to APT.
</p>

    sudo add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) \
    stable"

<p>Update the package database, to have access to Docker packages from the newly added repository.
</p>

    sudo apt-get update

<p>Finally, install the docker-ce package.
</p>

    sudo apt-get install docker-ce

<p>And to run Docker without needing sudo, add your user to the docker group
</p>

    sudo usermods -aG docker $(whoami)