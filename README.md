# Test Application for PWM (#16, #17) and PIC Coprocessor (#31) Tibbits

Both PWM Tibbits as well as the PIC coprocessor Tibbit are tested using the same project.

You will need:

- TPP2, TPP2(G2), TPP3, or TPP3(G2) board
- One Tibbit #16, #17, or #31
- One Tibbit #00-3
- One Tibbit #20 (9 terminal blocks)
- Optionally, one Tibbit #9 or #10 (12V->5V regulator)
- Optionally, one Tibbit #18 (power jack)

*The last two Tibbits are necessary if you are going to power your rig from a 12V power adaptor. Alternatively you can supply regulated +5V power directly to the TPP. The test with an RGB LED strip requires 12V power as well.*

All three Tibbits are based on the PIC16F1824 device. This is a generic PIC microcontroller with a typically rich set of peripherals.

Tibbits #16 and #17 take advantage of PIC's PWM channels (three out of four are utilized).

Tibbit #31 has four I/O lines that can be used in the following ways:

- Three lines have PWM capability
- All four lines can work as ADC inputs
- Two lines can act as TX and RX of the PIC's UART
- Each line can also function as a a regular input/output

All three Tibbits ship with the GRA (general register access) firmware, which allows you to access internal PIC registers and memory through the I2C interface. The firmware implements a very simple communications protocol that essentially implement two important commands — address read and address write. These two commands are used to write to and read from the internal PIC RAM and registers. This facilitates a simple and versatile access to all microcontroller resources.

Since the GRA firmware does not do anything intelligent and all the setup work is scripted in Tibbo BASIC, it's possible to modify the behavior of PIC micro without making any changes to its firmware.

The GRA firmware of PIC-based Tibbits can be updated using the "update_pic_firmware" project, which is also included in the .zip file.

This Tibbo BASIC project has several test modes. The desired mode is selected in the following line of code in main.tbs:

**test_item=TEST_IO '<<==================== SELECT DESIRED TEST CASE HERE**

Tibbit #31 (PIC coprocessor) supports all test modes. PWM Tibbits #16 and #17 should only be tested using PWM tests.

## TEST_IO (Tibbit #31 only)

For this test we recommend using four small LEDs. Insert Tibbits as shown on the right photo. Tibbit #0-3 is there to supply 5V power to the LEDs. Connect the LEDs as shown on the diagram: