# Track Hacker Pt1 - Official Writeup

## Challenge Overview
In this challenge, we were tasked with analyzing intercepted network packets to uncover a flag sent by a hacker to a specific server. The flag was hidden using a custom Python cipher, and our objective was to decrypt the communication and extract the flag. The packet capture file provided was named `ids_capture.pcapng`, and the server IP was `10.11.15.25`.

## Steps to Break the Cipher

### Understanding the Cipher
The cipher code provided in the challenge room revealed a critical detail: the encryption algorithm did not use the key directly for encryption. Instead, it used the length of the key to perform the encryption. This insight allowed us to focus on the key length rather than the key itself.

### Brute Force Key Length
We wrote a Python script to try all possible key lengths for decryption. By testing various key lengths, we identified that the correct key length was 128.

### Extracting ASCII Text
Using Wireshark, we opened the `ids_capture.pcapng` file and applied a display filter to isolate packets where the destination IP address was `10.11.15.25`. The filter used in Wireshark was: `ip.dst == 10.11.15.25`.

### Decrypting the Flag
After extracting the relevant packets, we converted the data into an ASCII dump. We then applied our decryption script, using the identified key length of 128, to decode the ASCII text. The decrypted text contained the flag.

### Flag Submission
The flag was found and formatted as `Vit8816{Founded_First_Access}`.

## Conclusion
By analyzing the provided cipher and understanding its reliance on key length, we successfully decrypted the communication and extracted the hidden flag. This challenge demonstrated the importance of understanding encryption methods and leveraging tools like Wireshark for packet analysis.

## Writeup Summary

1. **Cipher Analysis:**
   - Recognized that the cipher used key length rather than the key itself for encryption.

2. **Key Length Brute Force:**
   - Tested multiple key lengths, identified the correct length as 128.

3. **Packet Analysis:**
   - Used Wireshark to filter packets with destination IP `10.11.15.25`.
   - Extracted ASCII text from these packets.

4. **Decryption:**
   - Applied the decryption script using the correct key length.
   - Extracted the flag: `Vit8816{Founded_First_Access}`.

5. **Final Flag:**
   - Successfully submitted the flag as `Vit8816{Founded_First_Access}`.

This writeup concludes the steps taken to solve the "Track Hacker Pt1" challenge on TryHackMe. The key to solving this challenge was understanding the encryption mechanism and effectively using packet analysis tools to extract and decrypt the necessary information.
