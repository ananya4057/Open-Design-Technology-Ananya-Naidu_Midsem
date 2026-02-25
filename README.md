from machine import Pin
import time
import random

led1 = Pin(4, Pin.OUT)
led2 = Pin(5, Pin.OUT)
led3 = Pin(15, Pin.OUT)

btn1 = Pin(18, Pin.IN, Pin.PULL_UP)
btn2 = Pin(19, Pin.IN, Pin.PULL_UP)
btn3 = Pin(21, Pin.IN, Pin.PULL_UP)

start = Pin(14, Pin.IN, Pin.PULL_UP)

print("Start!")

while True:

    if start.value() == 0:   #agar we press start
        time.sleep(0.3)

        print("HURRY!")

        #3 random generations
        s1 = random.randint(0,2)
        s2 = random.randint(0,2)
        s3 = random.randint(0,2)

        # ----- SHOW SEQUENCE -----

        # Step 1
        if s1 == 0:
            led1.on()
        elif s1 == 1:
            led2.on()
        else:
            led3.on()
        time.sleep(0.5)
        led1.off()
        led2.off()
        led3.off()
        time.sleep(0.3)

        # Step 2
        if s2 == 0:
            led1.on()
        elif s2 == 1:
            led2.on()
        else:
            led3.on()
        time.sleep(0.5)
        led1.off()
        led2.off()
        led3.off()
        time.sleep(0.3)

        # Step 3
        if s3 == 0:
            led1.on()
        elif s3 == 1:
            led2.on()
        else:
            led3.on()
        time.sleep(0.5)
        led1.off()
        led2.off()
        led3.off()

        print("Mimic the sequence to open the vault")

        # ----- USER INPUT -----

        # Input 1
        while True:
            if btn1.value() == 0:
                u1 = 0
                break
            if btn2.value() == 0:
                u1 = 1
                break
            if btn3.value() == 0:
                u1 = 2
                break

        time.sleep(0.3)

        # Input 2
        while True:
            if btn1.value() == 0:
                u2 = 0
                break
            if btn2.value() == 0:
                u2 = 1
                break
            if btn3.value() == 0:
                u2 = 2
                break

        time.sleep(0.3)

        # Input 3
        while True:
            if btn1.value() == 0:
                u3 = 0
                break
            if btn2.value() == 0:
                u3 = 1
                break
            if btn3.value() == 0:
                u3 = 2
                break

        # ----- CHECK ANSWER -----

        if u1 == s1 and u2 == s2 and u3 == s3:
            print("Vault access granted")
            led1.on()
            led2.on()
            led3.on()
            time.sleep(1)
            led1.off()
            led2.off()
            led3.off()
            
        else:
            print("Wrong! The police are here! RUN!")
            for i in range(3):
                led1.on()
                led2.on()
                led3.on()
                time.sleep(0.3)
                led1.off()
                led2.off()
                led3.off()
                time.sleep(0.3)

        print("You escaped! Go back and try again")
# Open-Design-Technology-Ananya-Naidu_Midsem
