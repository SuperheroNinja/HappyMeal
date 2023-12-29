# Happy Meal

Happy Meals are containers for Mac.

## Why

Commercial use of [Docker Desktop](https://www.docker.com/products/docker-desktop/) at a company of more than 250 employees OR more than $10 million in annual revenue requires a paid subscription (Pro, Team, or Business).
**Source:** [Docker.com, pricing and subscriptions](https://www.docker.com/pricing/)

## Thus

If you work at a company with more than 250 employees OR more than $10m in annual revenue, you ought to stop using Docker Desktop. 
This recipe allows a (worse) alternative to Docker Desktop, but the components are F/OSS.

## Create docker server

Because we are sophisticated people, we use brew to install Vagrant and QEMU.

```brew install vagrant qemu```

Because we live in a society, we will use a plugin to control QEMU.

```vagrant plugin install vagrant-qemu```

To feel like the IT engineering equivalent of ***Rico Suave***, we only use one command to create our VM.

```vagrant up```

Remove the environment.

```vagrant destroy```

## Add happymeal to ssh hosts file

```vagrant ssh-config >> ~/.ssh/config```

## Connect Docker on Mac to VM

Create context for ```happymeal```, connecting via SSH

```docker context create --docker "host=ssh://happymeal" happymeal```

Use context

```docker context use happymeal```

## Run on Mac

```docker run hello-world```

## Extra: Port forwarding

Configure forwarded_port in [Vagrantfile](Vagrantfile)

## Read me

I insist, read me

If you are in need of more information of the engineering tools which are used in this recipe, please have a look in the following snippets:

### Docker context

Each context contains all information required to manage resources on the daemon. The docker context command makes it easy to configure these contexts and switch between them.
[More information: Working with Contexts in Docker Docs](https://docs.docker.com/engine/context/working-with-contexts/)

### Brew

Homebrew is the easiest and most flexible way to install the UNIX tools Apple didn't include with macOS. It is used for installation of tools in this recipe.
[Homebrew main page: https://brew.sh/](https://brew.sh/)

### Vagrant

Vagrant enables users to create and configure lightweight, reproducible, and portable development environments. It is used for controlling a virtual machine in this recipe.
[Vagrant main page: https://www.vagrantup.com/](https://www.vagrantup.com/)
[Great docs, great search, celebrate it by using it](https://developer.hashicorp.com/vagrant/docs)

#### Why do you use these specific settings in your Vagrantfile

Because.

## Disclaimer

I am not an expert, I am a generalist. This recipe is gathered by clicking countless links, reading numerous internet threads and asking stupid questions to smart people. We owe them our thanks, instead they get a reference in the previous sentence. Information Technology is not the right career choice if you wanted to experience glorious moments. This is proof. 

Also, ***because*** is perfectly fine as an explanation for a **why** question.

### If

If you ask me a question which can be answered by the text or links in this repository AND I will send you the link to this readme I will gain the following rights:

* to name your next unborn child
* and more importantly, you owe me coffee or lunch

Note: If within 12 months of this maintained right there is no child born, I **will** rename one of your current children.

#### Names

Names on the Namey-Nominee list are:

* Jar Jar Binks
* Cyberdyne
* Sam Bankman-Fried
