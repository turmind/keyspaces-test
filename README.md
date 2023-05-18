# Keyspaces-test [中文](README_cn.md)

## Observasion

- Connection to Keyspaces disconnect after about 12900 seconds = 35.84 hours
- Keyspaces reconnect immeidately after disconnect, no impact to businiess

## Test preparation

- create two IAM user keyspaces service credential
- cpp-diver tag v2.16.0 compile and install  https://github.com/datastax/cpp-driver/tree/2.16.0
  - git clone https://github.com/datastax/cpp-driver/tree/2.16.0
  - checkout tag v2.16.0
  - cmake & make & make install, that will build and install the libcassandra.so file in dir /usr/local/lib
  - add /usr/lobal/lib config file to /etc/ld.so.conf.d and use ldconfig command to make the system can find the so file
- update the simple.c file line 20 abouth the username and password
- Compile executables in simple by cmake & make
- run the simple executable file
  - in the run time, deactive one keyspaces service credential and observe and compare

## Test cases as follows

- key-active-break, Valid credentials, without executing select
- key-active-normal , Valid credentials, execute select every 30 seconds
- key-inactive-break , Invalid credentials, without executing select
- key-inactive-normal ,Invalid credentials, execute select every 30 seconds

## Relevant test files

- netstat.txt is the observed condition of socket pairs with keyspaces
- nohup.out is the operation log, focusing on the content:
  - key-active-break  line 4302
  - key-active-normal line 8602
  - key-inactive-break line 4302
  - key-inactive-normal line 8602
