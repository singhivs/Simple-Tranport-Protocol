High-level approach:
Since we used UDP sockets for this project, we needed to add sequence numbers of data packets. We first read the data from stdin and store the data in a list. The structure of a data packet is msg = {"type": "msg", "data": data, "sequence": SEQUENCE, 'checksum': checksum}. The sender sends a message to the receiver, and once the receiver receives the message, it adds the message to the list of messages received, and sends back an acknowldgement. If a packet is dropped, the receiver notifies the sender which packet it needs to resend. The receiver limit the number of acks to send within an adverstised window so the network is not flooded with identical acks. We also used a sliding window strategy to make the data transmission more efficient. 

Challenges you faced:
As we tested under different circumstances, we needed to modify our code to compile with the test cases. A large part of the challenge we faced was to improve the efficiency of our program while correctly handle packet drops, delays, duplications, etc. at the same time. 

Properties/features:
We used the skill of divide and conquer, by that we mean we abstracted functionalities into helper functions, which makes the structure of our code more concise and easier to debug. 

Testing:
We used logging and print statements throughout the project to easily see which messages were received and acknowldged, sequence numbers of the packets, and the time in-between. We also used test scripts provided by the starter code, which tested the performance of our program under different circumstances. 