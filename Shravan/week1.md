## Vault Door Series

### Challenge 1 : vault-door-training
Your mission is to enter Dr. Evil's laboratory and retrieve the blueprints for his Doomsday Project. The laboratory is protected by a series of locked vault doors. Each door is controlled by a computer and requires a password to open. Unfortunately, our undercover agents have not been able to obtain the secret passwords for the vault doors, but one of our junior agents obtained the source code for each vault's computer! You will need to read the source code for each level to figure out what the password is for that vault door. As a warmup, we have created a replica vault in our training facility. The source code for the training vault is here: VaultDoorTraining.java
```
import java.util.*;

class VaultDoorTraining {
    public static void main(String args[]) {
        VaultDoorTraining vaultDoor = new VaultDoorTraining();
        Scanner scanner = new Scanner(System.in); 
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
	}
   }

    // The password is below. Is it safe to put the password in the source code?
    // What if somebody stole our source code? Then they would know what our
    // password is. Hmm... I will think of some ways to improve the security
    // on the other doors.
    //
    // -Minion #9567
    public boolean checkPassword(String password) {
        return password.equals("w4rm1ng_Up_w1tH_jAv4_eec0716b713");
    }
}
```
### Solution and Learning :
The program when executed asks the user to enter the password inorder to get access.The program had a comparison block and in this code block the flag is present .So we get the flag easily just by going through the programm.

### Flag : picoCTF{w4rm1ng_Up_w1tH_jAv4_eec0716b713}


### Challenge : vault-door-1
This vault uses some complicated arrays! I hope you can make sense of it, special agent. The source code for this vault is here: VaultDoor1.java
  
```
import java.util.*;

class VaultDoor1 {
    public static void main(String args[]) {
        VaultDoor1 vaultDoor = new VaultDoor1();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
	String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
	}
    }

    // I came up with a more secure way to check the password without putting
    // the password itself in the source code. I think this is going to be
    // UNHACKABLE!! I hope Dr. Evil agrees...
    //
    // -Minion #8728
    public boolean checkPassword(String password) {
        return password.length() == 32 &&
               password.charAt(0)  == 'd' &&
               password.charAt(29) == '3' &&
               password.charAt(4)  == 'r' &&
               password.charAt(2)  == '5' &&
               password.charAt(23) == 'r' &&
               password.charAt(3)  == 'c' &&
               password.charAt(17) == '4' &&
               password.charAt(1)  == '3' &&
               password.charAt(7)  == 'b' &&
               password.charAt(10) == '_' &&
               password.charAt(5)  == '4' &&
               password.charAt(9)  == '3' &&
               password.charAt(11) == 't' &&
               password.charAt(15) == 'c' &&
               password.charAt(8)  == 'l' &&
               password.charAt(12) == 'H' &&
               password.charAt(20) == 'c' &&
               password.charAt(14) == '_' &&
               password.charAt(6)  == 'm' &&
               password.charAt(24) == '5' &&
               password.charAt(18) == 'r' &&
               password.charAt(13) == '3' &&
               password.charAt(19) == '4' &&
               password.charAt(21) == 'T' &&
               password.charAt(16) == 'H' &&
               password.charAt(27) == 'f' &&
               password.charAt(30) == 'b' &&
               password.charAt(25) == '_' &&
               password.charAt(22) == '3' &&
               password.charAt(28) == '6' &&
               password.charAt(26) == 'f' &&
               password.charAt(31) == '0';
    }
}

```
### Solving and Learning :
Rearrange the charAt index and filter out the text inside *' '* and added picCTF{ to the start and } to the end ,that was the flag.Wrote a python program to perform this but it failed some case so used chatGpt to perform the above operations .

### Flag : picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_ff63b0}

### Challenge 3 : vault-door-3
This vault uses for-loops and byte arrays. The source code for this vault is here: VaultDoor3.java
```
import java.util.*;

class VaultDoor3 {
    public static void main(String args[]) {
        VaultDoor3 vaultDoor = new VaultDoor3();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Our security monitoring team has noticed some intrusions on some of the
    // less secure doors. Dr. Evil has asked me specifically to build a stronger
    // vault door to protect his Doomsday plans. I just *know* this door will
    // keep all of those nosy agents out of our business. Mwa ha!
    //
    // -Minion #2671
    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        char[] buffer = new char[32];
        int i;
        for (i=0; i<8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (; i<16; i++) {
            buffer[i] = password.charAt(23-i);
        }
        for (; i<32; i+=2) {
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) {
            buffer[i] = password.charAt(i);
        }
        String s = new String(buffer);
        return s.equals("jU5t_a_sna_3lpm18gb41_u_4_mfr340");
    }
}

```

### solving and Learning :
| Index.   | value.   |   Total     |
|----------|----------|-------------|
| 0-7      |  8       |     8       |  
| 8-15     | 23-i     |     8       |
|16-31 e   | 46-i     |     8       |
|17-31 o   | i        |     8       |

On the index positions 8-15 and 16-31 we are just reversing the small part of the original string and on other index the password is the same as the part of the java file .I wrote the following python  program to get the string .
```
se="jU5t_a_sna_3lpm18gb41_u_4_mfr340"
idx=len(se)
passw =""
for i in range(idx):
    if(i<8):
        passw = passw+se[i]
    elif(i>7 and i<16):
        passw=passw+se[23-i]
    elif(i>15 and i<32 and i%2==0):
        passw=passw+se[46-i]
    elif(i>15 and i<32 and i%2!=0):
        passw=passw+se[i]
print(passw)
```

### Flag : picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_1fb380}

### Challenge 4 : vault-door-4
This vault uses ASCII encoding for the password. The source code for this vault is here: VaultDoor4.java
```
import java.util.*;

class VaultDoor4 {
    public static void main(String args[]) {
        VaultDoor4 vaultDoor = new VaultDoor4();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // I made myself dizzy converting all of these numbers into different bases,
    // so I just *know* that this vault will be impenetrable. This will make Dr.
    // Evil like me better than all of the other minions--especially Minion
    // #5620--I just know it!
    //
    //  .:::.   .:::.
    // :::::::.:::::::
    // :::::::::::::::
    // ':::::::::::::'
    //   ':::::::::'
    //     ':::::'
    //       ':'
    // -Minion #7781
    public boolean checkPassword(String password) {
        byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063 , 0163, 0137, 0143, 061 ,
            '9' , '4' , 'f' , '7' , '4' , '5' , '8' , 'e' ,
        };
        for (int i=0; i<32; i++) {
            if (passBytes[i] != myBytes[i]) {
                return false;
            }
        }
        return true;
    }
}

```
### Solving and Learning :
I did the following inorder to get the flag.
| Conversion Type      | Characters / Codes                                      | Corresponding String |
|---------------------|--------------------------------------------------------|---------------------|
| ASCII code to ASCII  | 106, 85, 53, 116, 95, 52, 95, 98                       | jU5t_4_b            |
| Hexadecimal to ASCII | 0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f         | UnCh_0f_            |
| Octal to ASCII       | 0142, 0131, 0164, 063, 0163, 0137, 0143, 061            | bYt3s_c1            |
| Already ASCII        | '9', '4', 'f', '7', '4', '5', '8', 'e'                 | 94f7458e            |



### Flag : picoCTF{jU5t_4_bUnCh_0f_bYt3s_c194f7458e}



### Challenge 5 : vault-door-5
In the last challenge, you mastered octal (base 8), decimal (base 10), and hexadecimal (base 16) numbers, but this vault door uses a different change of base as well as URL encoding! The source code for this vault is here: VaultDoor5.java
```
import java.net.URLDecoder;
import java.util.*;

class Main {
    public static void main(String args[]) {
        Main vaultDoor = new Main();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Minion #7781 used base 8 and base 16, but this is base 64, which is
    // like... eight times stronger, right? Riiigghtt? Well that's what my twin
    // brother Minion #2415 says, anyway.
    //
    // -Minion #2414
    public String base64Encode(byte[] input) {
        return Base64.getEncoder().encodeToString(input);
    }

    // URL encoding is meant for web pages, so any double agent spies who steal
    // our source code will think this is a web site or something, defintely not
    // vault door! Oh wait, should I have not said that in a source code
    // comment?
    //
    // -Minion #2415
    public String urlEncode(byte[] input) {
        StringBuffer buf = new StringBuffer();
        for (int i=0; i<input.length; i++) {
            buf.append(String.format("%%%2x", input[i]));
        }
        return buf.toString();
    }

    public boolean checkPassword(String password) {
        String urlEncoded = urlEncode(password.getBytes());
        String base64Encoded = base64Encode(urlEncoded.getBytes());
        String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
                        + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
                        + "JTM0JTVmJTM4JTM0JTY2JTY0JTM1JTMwJTM5JTM1";
        return base64Encoded.equals(expected);
    }
}

```
### Solving and Learning :
The password we enter is first converted to a byte array where % is added to every charcter and the character is converted to hexadecimal in the urlEncode function
Then again the string returned from urlencoded is converted to byte array and convert it into base 64 

```
Password Input
    │
    ▼
Convert to Byte Array
    │
    ▼
URL Encode Each Byte (% added and converted to hex)
    │
    ▼
URL-Encoded String
    │
    ▼
Convert to Byte Array Again
    │
    ▼
Base64 Encode the Byte Array
    │
    ▼
Final Base64-Encoded String
```
After this it is comapred with the expected string present in the code .So we have to just decode this inorder to get the password.I coded the follwing to get the password

```
import base64

se="JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"+ "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"+ "JTM0JTVmJTM4JTM0JTY2JTY0JTM1JTMwJTM5JTM1"
bs = base64.b64decode(se)
bs2 = bs.decode('utf-8')

parts = bs2.split("%")
pas = ""
for i in parts:
    bytes_obj = bytes.fromhex(i)
    pas = pas+bytes_obj.decode("utf-8")
print(pas)
```
I learned about various conversion modules in python and some library functions of java .

### Flag : picoCTF{c0nv3rt1ng_fr0m_ba5e_64_84fd5095}

### Challenge 6 : Vault-door-6
This vault uses an XOR encryption scheme. The source code for this vault is here: VaultDoor6.java
```
import java.util.*;

class VaultDoor6 {
    public static void main(String args[]) {
        VaultDoor6 vaultDoor = new VaultDoor6();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Dr. Evil gave me a book called Applied Cryptography by Bruce Schneier,
    // and I learned this really cool encryption system. This will be the
    // strongest vault door in Dr. Evil's entire evil volcano compound for sure!
    // Well, I didn't exactly read the *whole* book, but I'm sure there's
    // nothing important in the last 750 pages.
    //
    // -Minion #3091
    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            0x3b, 0x65, 0x21, 0xa , 0x38, 0x0 , 0x36, 0x1d,
            0xa , 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa ,
            0x21, 0x1d, 0x61, 0x3b, 0xa , 0x2d, 0x65, 0x27,
            0xa , 0x66, 0x36, 0x30, 0x67, 0x6c, 0x64, 0x6c,
        };
        for (int i=0; i<32; i++) {
            if (((passBytes[i] ^ 0x55) - myBytes[i]) != 0) {
                return false;
            }
        }
        return true;
    }
}

```
### Solving and Learning :
Performing XOR on the result using the same key restores the original value.The passbytes array is supposed exor is supposed to be equal to mybytes.But if we exor mybytes we will get passbytes .So i generated the following code to perform this 
```
se = "0x3b, 0x65, 0x21, 0xa , 0x38, 0x0 , 0x36, 0x1d, 0xa , 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa , 0x21, 0x1d, 0x61, 0x3b, 0xa , 0x2d, 0x65, 0x27, 0xa , 0x66, 0x36, 0x30, 0x67, 0x6c, 0x64, 0x6c"

# Split and strip each item
ls = [i.strip() for i in se.split(",")]

# Convert each hex string to int
ls1 = [int(i, 16) for i in ls]
ls_con = [hex(c ^ 0x55) for c in ls1]
pas = ""
for i in ls_con:
    hex_str = i[2:]  # remove '0x' prefix
    if len(hex_str) == 1:
        hex_str = '0' + hex_str  # pad single digit hex

    bytes_obj = bytes.fromhex(hex_str)
    pas += bytes_obj.decode("utf-8", errors="replace")  # use replace to avoid crash on bad chars

print(pas)
```







### Flag :picoCTF{n0t_mUcH_h4rD3r_tH4n_x0r_3ce2919}
