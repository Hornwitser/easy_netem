# easynetem

Command line script to simplify setting up a netem qdisc to simulate various network conditions on a host.
It has the necessary pluming to easily bring it up for a single port on either UDP or TCP while leaving the rest of the network traffic untouched.

Note: this has not been tested or validated to work on loopback use at your own risk there!


## Usage

    easynetem ACTION

    actions:
        setup DEV PROT PORT    - Setup netem qdiscs on DEV for PROT PORT
        remove DEV             - Remove qdiscs on DEV
        option DEV OPTIONS DIR - Set netem options, see man tc-netem for OPTIONS

    Note: for ingress support an ifb is created on setup and deleted on remove

    Examples:
        easynetem setup eth0 tcp 25565
        easynetem option eth0 "delay 100ms loss 1%% rate 3Mbit"
        easynetem option eth0 "loss 100%" out
        easynetem remove eth0

## License

This project is licensed under the GPL Version 2 or later.
