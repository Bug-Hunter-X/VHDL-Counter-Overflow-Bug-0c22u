# VHDL Counter Overflow Bug

This repository demonstrates a common error in VHDL code: an integer counter that lacks proper overflow handling.  The `buggy_counter.vhd` file contains the buggy code, while `fixed_counter.vhd` provides a corrected version.

## Bug Description

The original VHDL code implements a simple counter. However, it does not check for an upper bound on the `internal_count` signal. When the counter reaches its maximum value (15), the next increment will cause an overflow, leading to unpredictable behavior, such as wrapping around to 0 or causing a simulation failure.  This is a subtle but potentially serious error.

## Solution

The `fixed_counter.vhd` file demonstrates the correct implementation.  It uses a conditional statement to check if the counter has reached its maximum value before incrementing. If it has, the counter remains at its maximum value. This prevents overflow and ensures reliable operation.

## How to Reproduce

1.  Simulate `buggy_counter.vhd` with a testbench that drives the clock and reset signals. Observe the counter's behavior when it reaches and exceeds its maximum value.
2. Simulate `fixed_counter.vhd` with the same testbench. Note that the counter now correctly stops at its maximum value.
