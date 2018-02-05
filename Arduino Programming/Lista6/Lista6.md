# Lista 6

1.  Wykorzystaj tranzystor MOSFET (np. [IRF520](https://www.vishay.com/docs/91017/91017.pdf) z zestawu, [schemat](https://skos.ii.uni.wroc.pl/pluginfile.php/13854/mod_assign/intro/schemat.png), należy pamiętać o podłączeniu diody) lub układ [L293D](http://www.ti.com/lit/ds/symlink/l293.pdf) (schemat połączeń w zalinkowanej nocie katalogowej, obrazek 9) do jednokierunkowego sterowania silnikiem. Sygnał sterujący dla silnika powinien być sygnałem PWM generowanym przez licznik (można użyć dowolnego trybu PWM). Wypełnienie sygnału PWM (prędkość obrotową silnika) należy ustawić przez potencjometr podłączony do ADC. **[2]**
2.  Rozszerz rozwiązanie poprzedniego zadania o kontroler PID sterujący prędkością obrotową silnika. Można wykorzystać [implementację PID](https://skos.ii.uni.wroc.pl/pluginfile.php/13854/mod_assign/intro/AVR221.zip) z [noty aplikacyjnej AVR221](https://skos.ii.uni.wroc.pl/pluginfile.php/13854/mod_assign/intro/AVR221.pdf). Wejściem do kontrolera PID powinno być napięcie zmierzone na silniku przez ADC w momencie, gdy sygnał PWM ma wartość niską (tranzystor zasilający silnik jest wyłączony), a wyjściem - wypełnienie sygnału PWM. Zadanie jest zrealizowane poprawnie, jeśli przy małej ustawionej prędkości będzie trudniej zatrzymać silnik palcami, niż w poprzednim zadaniu (będzie się "siłował"). **[3]**  

    Podpowiedzi:
    *   Należy zastosować tryb Phase Correct PWM lub Phase and Frequency Correct PWM, częstotliwość PWM powinna być najlepiej w zakresie 500 Hz - 1 kHz.
    *   Jeśli używane jest wyjście bez odwracania (non-inverting) a wartość szczytową ustawia się przez rejestr ICR1, pomiary ADC można inicjować na przerwaniu TIMER1_CAPT (Input Capture).
3.  Napisz program, który używając sygnału PWM będzie sterował serwem modelarskim. (W serwie z zestawu: czerwony przewód to zasilanie, czarny to ziemia, biały to sygnał sterujący) Wychylenie serwa jest proporcjonalne do wypełnienia sygnału PWM, należy zastosować częstotliwość ok. 50 Hz. Należy unikać skrajnych wartości wychylenia – serwo można uszkodzić, nakazując mu obrót poza zakres! Docelowa pozycja serwa ma być zadana przez potencjometr odczytywany przez ADC. **[2]**
4.  Rozszerz rozwiązanie zadania 1 o możliwość obracania silnikiem w obu kierunkach. Należy wykorzystać układ [L293D](http://www.ti.com/lit/ds/symlink/l293.pdf), schemat połączeń jest w nocie katalogowej na rysunku 10 (nie trzeba stosować zewnętrznych diod, diody wbudowane w układ wystarczają). Zmianę kierunku obrotu można zrealizować np. przez naciśnięcie przycisku. **[2]**