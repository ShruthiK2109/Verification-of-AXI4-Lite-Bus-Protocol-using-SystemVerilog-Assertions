# Verification-of-AXI4-Lite-Bus-Protocol-using-SystemVerilog-Assertions
<img width="887" height="390" alt="AXI4 Lite diagram for read and write operations" src="https://github.com/user-attachments/assets/ea6b0621-21ba-45f2-a74d-44c47bb2f319" />

The Advanced eXtensible Interface 4 (AXI4) belongs to the fourth generation of the ARM Advanced Microcontroller Bus Architecture (AMBA) standard. It is a family of buses designed for high-performance, synchronous, and multi-master on-chip communication. The AXI4 bus protocol includes five channels for communication: Read address, Read data, Write address, Write data, and Write response. Implemented using Finite State Machines (FSMs), the design ensures that the master initiates read/write requests to the slave, allowing the slave to read/write data to memory based on the received requests. Within the AMBA specification, there are three AXI4 protocols: AXI4, AXI4-Lite, and AXI4-Stream. AXI4-Lite is a subset of AXI4, specifically lacking burst access capability. It features a simpler interface compared to the full AXI4, utilizing a traditional Address/Data format (single address, single data) and supporting only 32- or 64-bits data width.

Methodology:

During READ operation:

● In READ Operation the Master will send a particular address location from where it would like to read the data. When an address is found on the read address channel, the ARVALID Signal goes high.

● The address from the Master remains stable until the RREADY is high. Slave gives acknowledgment to Master by asserting ARREADY indicating that it accepts the address.

● Since both ARVALID and ARREADY are asserted, on the next rising clock edge the handshake occurs. After this the master and slave deassert ARVALID and the ARREADY, respectively.

● The Slave will receive the Address and puts the data on the data bus. When valid data is present in the data bus then RVALID signal goes high.

● When RREADY signal is high, it allows the Master to accept the data.

● Since both RREADY and RVALID are asserted, the next rising clock edge completes the transaction. RREADY and RVALID can now be deasserted.

During WRITE operation:

● During WRITE Operation the Master sends a particular address to the slave. If the address is present in the write address channel then AWVALID Signal will be high.

● The Slave gives acknowledgement to the Master by asserting AWREADY indicating that it accepts the address. The address from the Master remains stable until the AWREADY is high.

● Because Valid and Ready signals are present on both the Write Address and Write Data channels, handshakes occur, and the corresponding Valid and Ready signals can be deasserted.

● The Master will send the data to the slave using a data bus. When valid data is present in the data bus then the WVALID signal goes high.

● When the Slave is ready to accept the information, it asserts WREADY and the Slave will receive that data present in the data bus.

● The Slave asserts BVALID, indicating there is a valid response on the Write response channel.
