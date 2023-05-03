Download Link: https://assignmentchef.com/product/solved-cryptography-and-network-security-homework-1
<br>
<h1>Instruction</h1>

<ul>

 <li><strong>Submission Guide: </strong>Please submit all your codes and report to CEIBA. You need to put all of them in a folder named by your student id, compress it to hw1 {student id}.zip. For example, hw1 r04922456.zip. The report must be in <strong>PDF </strong>format, and named report.pdf.</li>

 <li>You may encounter new concepts that haven’t been taught in class, and thus you’re encouraged to discuss with your classmates, search online, ask TAs, etc. However, you must write your own answer and code. Violation of this policy leads to serious consequence.</li>

 <li>You may need to write programs in the Capture The Flag (CTF) problems. Since you can use any programming language you like, we will use a pseudo extension code<strong>.ext </strong>(e.g., code.py, code.c) when referring to the file name in the problem descriptions.</li>

 <li>This homework set are worthy of 110 points including bonus. If you get more than 100 points, your score will still be counted as 100 points.</li>

 <li>You are recommended to provide a brief usage of your code in <strong>txt </strong>(e.g., how to compile, if needed, and execute). You may lose points if TAs can’t run your code.</li>

 <li>In each of the Capture The Flag (CTF) problems, you need to find out a flag, which is in BALSN{…} format, to prove that you have succeeded in solving the problem.</li>

 <li>Besides the flag, you also need to submit the code you used and a short write-up in the report to get full points. The code should be named <strong>code</strong><em>{</em><strong>problem number</strong><em>}</em><strong>.ext</strong>. For example, code3.py.</li>

 <li>In some CTF problems, you need to connect to a given service to get the flag. These services only allow connections from 140.112.0.0/16, 140.118.0.0/16 and 140.122.0.0/16.</li>

</ul>

<h1>Handwriting</h1>

<h2>1.      CIA (10%)</h2>

Please explain three major security requirements: confidentiality, integrity and availability. For each security requirement, please give an example in the real world.

<h2>2.      Hash Function (10%)</h2>

Please explain three properties of a cryptographic hash function: one-wayness, weak collision resistance and strong collision resistance.

For each property, please give an example applied in the real world.

<h2>3.      Threshold Signature (15%)</h2>

Lets recall the Shamir’s Secret Sharing.

<em>A</em>(<em>x</em>) = <em>a</em><sub>0 </sub>+ <em>a</em><sub>1</sub><em>x </em>+ <em>… </em>+ <em>a<sub>t</sub></em>−<sub>1</sub><em>x<sup>t</sup></em><sup>−1</sup>

The secret is <em>a</em><sub>0</sub>, and the <em>i</em>th user will receive (<em>i,A</em>(<em>i</em>) <em>mod p</em>), where <em>p </em>is a prime.

Suppose <em>z </em>= <em>xy</em>, we call a function <em>e </em>is pairing if it satisfies:

<em>e</em>(<em>g<sup>x</sup>,g<sup>y</sup></em>) = <em>e</em>(<em>g,g</em>)<em><sup>xy </sup></em>= <em>e</em>(<em>g,g</em>)<em><sup>z </sup></em>= <em>e</em>(<em>g,g<sup>z</sup></em>)

Now consider the following BLS signature scheme:

Setup:

hash function : <em>Hash</em>(<em>msg</em>)

large prime : <em>q </em>generator : <em>g</em>

secret key : <em>sk </em>= <em>x </em>public key : <em>pk </em>≡ <em>g<sup>x</sup></em>(<em>mod q</em>)

Signing:

plaintext : <em>m</em>

hash value : <em>h </em>= <em>Hash</em>(<em>m</em>) signature : <em>σ </em>≡ <em>h<sup>sk</sup></em>(<em>mod q</em>)

Verification:

Valid : <em>e</em>(<em>σ,g</em>) = <em>e</em>(<em>h,g<sup>sk</sup></em>)

You should revise the setting above to accomplish BLS threshold signature, such that a plaintext message <em>m </em>can be signed as a valid threshold signature only if <em>t </em>out of <em>n </em>users collaborate. Everyone should be able to verify the <strong>user signature </strong>and the <strong>threshold signature </strong>by performing the verification procedure, which means you should not split the message before signing as you can’t ensure the integrity of splited messages. You should design the BLS threshold signature scheme which include <em>Setup, User Signature Signing, User Signature Verification, Threshold Signature Signing, Threshold Signature Verification </em>procedure. Note that all the users will receive (<em>i,A</em>(<em>i</em>) <em>mod p</em>) by a secure channel, and you should assume all other communication is done via an authenticated but not secret channel. Your solution should prevent the adversary (including some of the users) to forge a valid signature.

<em>Hint1: h<sup>a </sup></em>· <em>h<sup>b </sup></em>= <em>h<sup>a</sup></em><sup>+<em>b</em></sup>

<em>Hint2: </em>(<em>h<sup>a</sup></em>)<em><sup>b </sup></em>= <em>h<sup>ab</sup></em>

<em>Hint3: Except Threshold Signature Signing, other procedures should similar to BLS signature scheme.</em>

<h1>Capture The Flag</h1>

<h2>4.      Babe crypto (10%)</h2>

Welcome to the Crypto World. To prove you are ready for the journey in the Crypto World, please solve all the Classical cipher challenges yourself. Even though Classical cipher only used in the past and most of them can be practically computed and solved, I dont think you can figure it out that easily :P. Be careful and dont use Classical cipher to keep your secret!

You can access the service by nc 140.112.31.96 10151. If this is your first CTF challenge, highly recommend you to solve this challenge first.

<h2>5.      OTP (15%)</h2>

<ul>

 <li>(5%) If a one-time pad XORs a message with a random key of same length, it achieves perfect security. Can you decrypt the perfect secret? Access the challenge server by nc 140.112.31.96 10152, and the server source code is provided in otp-1.py using Python 3.6.7.</li>

 <li>(10%) It seems that one-time pad is not secure enough so I use multiple random keys to encrypt my top secret flag. You can access the challenge server by nc 140.112.31.96 10153, and the server source code is provided in otp-2.py using Python 3.6.7</li>

</ul>

<h2>6.        MD5 Collision (10% + Bonus 5%)</h2>

Checksum is used to ensure integrity of a given file. However, if the chosen hash function has collision, then the checksum is no longer trustworthy.

The service nc 140.112.31.96 10150 requires two inputs, which are two base64-encoded python2 code. For instance, this is a python2 code: print ‘Hello’, the base64-encoded python2 code will be cHJpbnQgJ0hlbGxvJwo=. You have to input <strong>two base64-encoded python2 codes </strong>that satisfied the following conditions:

<ul>

 <li>One of the code will output “MD5 is secure!” (without the quotes).</li>

 <li>Another code will output “Just kidding!” (without the quotes).</li>

 <li>Both codes has the same MD5 hash value.</li>

 <li>Of course, two codes should be different.</li>

 <li>The code size should be less than 500 bytes.</li>

</ul>

You will receive the <strong>FLAG </strong>if you succeed. You are required to attach both same MD5 codes in base64 encoding in the report (code1: &lt;insert base64-encoded code1&gt;, code2:

&lt;insert base64-encoded code2&gt;), otherwise you will not receive any credit.

<em>Bonus (5%): Try to find another hidden flag &#x1f642; (No hint will be provided for bonus)</em>

<h2>7.        Flag Market (10% + Bonus 5%)</h2>

Welcome to Flag Market, we sell a lot of <strong>Flags </strong>here, you don’t want to miss this! Oh, we only accept <strong>BALSN Coin</strong>, so please buy <strong>BALSN Coin </strong>from our cryptocurrency market.

You can access the service by nc 140.112.31.96 10154.

<em>Bonus (5%): Try to find another hidden flag &#x1f642; (No hint will be provided for bonus)</em>

<h2>8.      RSA (10%)</h2>

After learning RSA in class, I think it is a good encryption unless hackers have lots of computation resource. Therefore, I followed the operation in RSA encryption algorithm to keep my flag. You can ask for the cipher as many times as you want, but you will never know how to decrypt it without the private key! Go and find the flag by nc 140.112.31.96 10155.

<h2>9.       The Backdoor of Diffie-Hellman (10%)</h2>

“Hi, I am Alice. I used the script DH_backdoor/DH.py to send a top secret flag to my best friend, Bob. However, after sending the flag, I noticed that the generator <em>g </em>was modified by someone. It must be a backdoor of the Diffie Hellman algorithm. I have collected the parameters we used in the file DH_ backdoor/parameters. Can you find out whether our flag is leaked?” Decrypt the variable <strong>cipher </strong>in the file DH_backdoor/parameters to get the flag.

<em>Hint:</em><em> is this simply a coincidence?</em>