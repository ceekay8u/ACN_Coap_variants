
Instructions for usage.

net_variant1.c - for implementing variant 1.
net_variant2.c - for implementing variant 2.

Firstly, copy the variant code (either net_variant1.c or net_variant2.c) into net.c (which is located in libcoap/src/net.c).

For compiling and regenrating the binaries go to the libcoap directory and run the following commands.

make clean
./configure --disable-manpages
sudo make
sudo make install

Navigate into libcoap/examples to find client.c
Replace the existing code with the client.c in this repository.

Note : the Server program is coap-server.c and the Client program is client.c. 

The client and server programs are compiled in this manner 
Server program
coap-server.c
gcc -I /usr/local/include/ coap-server.c -o coap-server -l coap-2-openssl -DWITH_POSIX

Client Program
client.c
gcc -I /usr/local/include/ client.c -o coap-client -l coap-2-openssl -DWITH_POSIX


Running the client and server codes.

Open two terminals in the same directory and run the client and server commands 

Running the server code: ./coap-server -l 50% -v9

Running the client code: while /bin/true; do coap-client -m get coap://[::1]/time -v9 ; done

Open wiresahrk with a loopback filter and capture the coap packets. 

The libcoap repository can be found here : https://github.com/obgm/libcoap