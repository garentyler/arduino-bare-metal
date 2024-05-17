CC=avr-gcc
CFLAGS=-Os -DF_CPU=16000000UL -mmcu=atmega328p -c
ARDUINO=/dev/ttyACM0

default:
	$(CC) $(CFLAGS) -o main.o main.c
	$(CC) -o main.bin main.o
	avr-objcopy -O ihex -j .text -j .data -R .eeprom main.bin main.hex
.PHONY: flash clean
flash: default
	sudo avrdude -F -V -c arduino -p ATMEGA328P -P $(ARDUINO) -b 115200 -U flash:w:main.hex
clean:
	rm -rf *.o *.bin *.hex
