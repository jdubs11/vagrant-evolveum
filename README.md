# vagrant-evolveum

## Install needed tools
Download and install [Virtualbox](https://www.virtualbox.org/wiki/Downloads)

Download and install [Vagrant](https://developer.hashicorp.com/vagrant/downloads?ajs_aid=a427ad26-2662-4a25-a34a-777240015bbf&product_intent=vagrant)

Download and install [Git for Windows](https://git-scm.com/download/win)

## Windows setup
Open Git Bash on your Windows (host) machine. Just search for "Git Bash" in the search bar.

Create the directory you want to work in. I usually do this in `~/Desktop/Vagrant/`

Clone this repo to that workspace. `git clone git@github.com:jdubs11/vagrant-evolveum.git`
- Alternatively you can clone via HTTPS and use your username/password or generated code
- `git clone https://github.com/jdubs11/vagrant-evolveum.git`

Enter the newly checked out repo `cd vagrant-evolveum`

Then run Vagrant `vagrant up`

Once the process completes, you can visit the Midpoint UI on your host machine at:
- http://localhost:8080/midpoint

Default creds:
- username: administrator
- password: 5ecr3t

## Delete VM
`vagrant destroy`

## Suspend VM
`vagrant suspend`

## Resume VM
`vagrant resume`
