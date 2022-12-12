## 1)Frequenzgang bekannt
- mit der Transformation von Rechteckfunktion im Frequenzbereich zu si-Funktion im Zeitbereich
```Matlab
close all
clear all

wg = pi/2   %Grenzfreqz
wa = 1000   %Abtastfreqz
N = 4       %Ordnung

b = [zeros(1,(N+1))];    %Array erzeugen
for ip = 1 : N+1            %ip:i_positiv : von 1 bis N+1
    i = ip - 1 - N/2;       %i: von -N/2 bis N/2
    if i ~= 0               %if i != 0
        b(ip) = wg/pi*sin(wg*i) /(wg*i); %wg/pi*si(wg*i)
    else
        b(ip) = wg/pi*1;                 %wg/pi*1
    end
end
b                           %Koeffizient b
a = [zeros(1,N+1)];
a(1) = 1;
a                           %Koeffizient a

figure(1)
k=[0:N];                    %k: von 0 bis N
stem(k,b)                   %stem(x,y): Plot discrete sequence data
title('N = 4')
ylabel('F(z)');
xlabel('z');
grid;

figure(2)
[H,w] = freqz(b,a);
freqz(b,a)                  %Frequenzgang
title('Frequenzgang');
```

- mit der Z
