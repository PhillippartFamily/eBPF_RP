# Instructions

Using Ubuntu 20.04 for these experiments using bpftrace. I have found that 22.04 does not build properly and there are some issues with dependencies.


## bpftrace

Make sure it's installed as described in https://github.com/iovisor/bpftrace/blob/master/INSTALL.md

## To run port_based_trigger:

- in **vulnerable machine**:
```
sudo bpftrace --unsafe port_based_trigger.bt [IP in big endian] [magic port]
```

- in **attacker**:
```
nc -vv [IP of destination (vulnerable machine)] 22 -p [magic port] 
```

### Example:

![example](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d7392e25-81a8-41ac-8a5b-ce77fe444b5f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230117%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230117T141211Z&X-Amz-Expires=86400&X-Amz-Signature=0ea297073971a40ddf00d5b8a2606d8a2e93cc825f1285e9f9fd3f22c84e6c5f&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D%22Untitled.png%22&x-id=GetObject)

First fails because of wrong port, then succeeds.

## To run message_based_trigger:

Still figuring out