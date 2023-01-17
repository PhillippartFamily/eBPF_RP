## To run port_based_trigger:

- in **vulnerable machine**:
```
sudo bpftrace --unsafe port_based_trigger.bt [IP in big endian] [magic port]
```

- in **attacker**:
```
nc -vv [IP of destination (vulnerable machine)] 22 -p [magic port] 
```

## To run message_based_trigger:

Still figuring out