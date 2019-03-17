# Working on EECS Servers

There is a list of [EECS compute severs](http://support.eecs.qmul.ac.uk/research-computing/compute-servers/) (only viewable from within the QM network).

There are several reasons why working on the servers is useful:

- you can do other work on your own computer;

- leave code running and come back later for the answers;

- make use of the cores and ram that server has.

The first step is to connect to the sever. If you are outside of the EECS network then you will need to `ssh` via frank: 
```
ssh YOUR_EECS_USERNAME@frank.eecs.qmul.ac.uk
```

After entering your password, you are connected to frank, which is virtual and used as a bridge to connect to other servers. From here, you can log onto a server from the list above by:
```
ssh YOUR_EECS_USERNAME@SERVER_NAME.eecs.qmul.ac.uk
```

You will be in your home directory. From here you will need to go to the folder where your code is and run your script!