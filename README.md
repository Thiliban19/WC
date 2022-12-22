### Ex No : 2 To study the DS spread spectrum Modulation and Demodulation Technique

## Aim: Write a Matlab program to study the DS spread spectrum Modulation and Demodulation Technique
## Apparatus required:
## MATLAB 9, Simulink, and computer
## Program :
clc;</br>
close all;</br>
clear all;</br>
b=input('Enter The input Bits : ');</br>
ln=length(b);</br>
% Converting bit 0 to -1</br>
for i=1:ln</br>
if b(i)==0</br>
b(i)=-1;</br>
end</br>
end</br>
% Generating the bit sequence with each bit 8 samples long</br>
k=1;</br>
for i=1:ln</br>
for j=1:8</br>
bb(k)=b(i);</br>
j=j+1;</br>
k=k+1;</br>
end</br>
i=i+1;</br>
end</br>
len=length(bb);</br>
subplot(2,1,1);</br>
stairs(bb,'linewidth',2); axis([0 len -2 3]);</br>
title('ORIGINAL BIT SEQUENCE b(t)');</br>
% Generating the pseudo random bit pattern for spreading</br>
pr_sig=round(rand(1,len));</br>
for i=1:len</br>
if pr_sig(i)==0</br>
pr_sig(i)=-1;</br>
end</br>
end</br>
subplot(2,1,2);</br>
stairs(pr_sig,'linewidth',2); axis([0 len -2 3]);</br>
title('PSEUDORANDOM BIT SEQUENCE pr_sig(t)');</br>
% Multiplying bit sequence with Pseudorandom Sequence</br>
for i=1:len</br>
bbs(i)=bb(i).*pr_sig(i);</br>
end</br>
% Modulating the hopped signal</br>
dsss=[];</br>
t=0:1/10:2*pi;</br>
c1=cos(t);</br>
c2=cos(t+pi);</br>
for k=1:len</br>
if bbs(1,k)==-1</br>
dsss=[dsss c1];</br>
else</br>
dsss=[dsss c2];</br>
end</br>
end</br>
figure,</br>
subplot(2,1,1);</br>
stairs(bbs,'linewidth',2); axis([0 len -2 3]);</br>
title('MULTIPLIER OUTPUT SEQUENCE b(t)*pr_sig(t)');</br>
subplot(2,1,2);</br>
plot(dsss);</br>
title(' DS-SS SIGNAL...');</br>
Output :</br>
Enter The input Bits :</br>
[1 0 0 1 1 0 1 0 1]</br>
