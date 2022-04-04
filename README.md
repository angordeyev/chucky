# Chucky

## Clustering

    [{kernel,
      [{distributed, [{chucky, 5000, [a@manticore, {b@manticore, c@manticore}]}]},
       {sync_nodes_mandatory, [b@manticore, c@manticore]},
       {sync_nodes_timeout, 30000}
      ]}].
   
<!---->

    [{distributed, [{chucky, 5000, [a@manticore, {b@manticore, c@manticore}]}]}]  

"chucky" is, of course, the application name. 

5000 represents the timeout in millisec-onds before the node is considered down and the application is restarted in the next highest-priority node.

[a@manticore, {b@manticore, c@manticore}] lists the nodes in priority. In this case, a is first in line, followed by either b or c. Nodes defined in a tuple don’t have a priority among themselves. For example, consider the following entry.



# chucky

## Server setup

Create two VMs

Change hostname names and reboot the machines

    hostnamectl set-hostname anode
    hostnamectl set-hostname bnode

## Starting nodes

    iex --sname a -pa _build/dev/lib/chucky/ebin --app chucky --erl  "-config config/anode.config"
    iex --sname b -pa _build/dev/lib/chucky/ebin --app chucky --erl  "-config config/bnode.config"

    echo SDFERMOWERPEMZLSDFIE > ~/.erlang.cookie
