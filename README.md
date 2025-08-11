# Seven-Segment Display Driver using Verilog HDL

## Aim  
To design and simulate a seven-segment display driver using Verilog HDL, and verify its functionality through a testbench in the Vivado 2023.1 environment. The objective is to implement the logic that converts a 4-bit binary input into the corresponding 7-segment display output for the digits 0 to 9.

## Apparatus Required  
- **Vivado 2023.1**  
- **Computer system** with a suitable operating system  

## Procedure  

### 1. Launch Vivado 2023.1  
- Open Vivado and create a new project.  

### 2. Design the Verilog Code  
- Write the Verilog code for the seven-segment display, defining the logic that maps a 4-bit binary input to the corresponding segments (a to g) of the display.  

### 3. Create the Testbench  
- Write a testbench to simulate the seven-segment display behavior. The testbench should apply various 4-bit input values and monitor the corresponding output on the seven-segment display.  

### 4. Add the Verilog Files  
- Add both the design module and the testbench in the Vivado project.  

### 5. Run Simulation  
- Run the behavioral simulation to verify the output. Ensure the seven-segment display behaves correctly for binary inputs **0000 to 1001** (decimal **0 to 9**).  

### 6. Observe the Waveforms  
- Analyze the output waveforms in the simulation window, and verify that the correct segments light up for each digit.  

### 7. Save and Document Results  
- Capture screenshots of the waveform and save the simulation logs. These will be included in the lab report.  

---
## Logic Diagram

<img width="248" height="310" alt="image" src="https://github.com/user-attachments/assets/9731885c-46bc-4183-843c-f4ea2ac5a229" />

<img width="230" height="175" alt="image" src="https://github.com/user-attachments/assets/203c78b8-4b87-4713-9cf5-82314cf72385" />


<img width="284" height="266" alt="image" src="https://github.com/user-attachments/assets/bcb52839-a8c0-40ab-8e1b-a38c2ffe41a2" />


## Verilog Code for Seven-Segment Display  

```verilog
// seven_segment_display.v
module seven_segment_display (
    input wire [3:0] binary_input,
    output reg [6:0] seg_output
);

always @(*) begin
    case (binary_input)
        4'b0000: seg_output = 7'b0111111; // 0
        4'b0001: seg_output = 7'b0000110; // 1
        4'b0010: seg_output = 7'b1011011; // 2
        4'b0011: seg_output = 7'b1001111; // 3
        4'b0100: seg_output = 7'b1100110; // 4
        4'b0101: seg_output = 7'b1101101; // 5
        4'b0110: seg_output = 7'b1111101; // 6
        4'b0111: seg_output = 7'b0000111; // 7
        4'b1000: seg_output = 7'b1111111; // 8
        4'b1001: seg_output = 7'b1101111; // 9
        default: seg_output = 7'b0000000; // blank or error
    endcase
end

endmodule
```
## Simulated Output

_____ Keep Simulated output ___________


## Testbench for Seven-Segment Display
```verilog

`timescale 1ns / 1ps
module seven_segment_display_tb;
// Inputs
reg [3:0] binary_input;
// Outputs
wire [6:0] seg_output;
// Instantiate the Unit Under Test (UUT)
seven_segment_display uut (
    .binary_input(binary_input),
    .seg_output(seg_output)
);
// Test procedure
initial begin
    // Initialize inputs
    binary_input = 4'b0000;

    // Apply test cases
    #10 binary_input = 4'b0000; // Display 0
    #10 binary_input = 4'b0001; // Display 1
    #10 binary_input = 4'b0010; // Display 2
    #10 binary_input = 4'b0011; // Display 3
    #10 binary_input = 4'b0100; // Display 4
    #10 binary_input = 4'b0101; // Display 5
    #10 binary_input = 4'b0110; // Display 6
    #10 binary_input = 4'b0111; // Display 7
    #10 binary_input = 4'b1000; // Display 8
    #10 binary_input = 4'b1001; // Display 9
    #10 $stop;
end

// Monitor outputs
initial begin
    $monitor("Time=%0t | binary_input=%b | seg_output=%b", $time, binary_input, seg_output);
end

endmodule
```
## Conclusion
In this experiment, a seven-segment display driver was successfully designed and simulated using Verilog HDL. The simulation results confirmed that the display correctly represented the digits 0 to 9 based on the 4-bit binary input. The testbench effectively verified the functionality of the seven-segment display by applying various input combinations and observing the corresponding segment outputs.

This experiment highlights how Verilog HDL can be used to control hardware components like a seven-segment display in digital systems.
