# Juhend K-lähima naabri ülesandeks

### 1. Tõmba alla "wines_data.xlsx" ja ava Excelis

Siin samas kaustas:
https://github.com/andribusch/machine_learning_examples/tree/master/init_2022/wines_dataset.xlsx

### 2. Määra igale veinile (reale) juhuslik arv. Reasta juhuslikud arvud (funktsioon RANK())

**Hint: Rank funktsiooni kasutamine**
```
=RANK(O2;$O$2:$O$179)
```

### 3. Määra, kui palju andmeid on treeningandmetes (nt 70%) ning eralda need eraldi töölehtedele (worksheets).

### 4. Arvutame iga test-veini kauguse treening-veinist - tulemuseks kauguste tabel "Distances" 
	- Tee tabel, kus päised
	- read: Test objektid
	- Veerud: Treening objektid
	- CTRL + T teeb Exceli maagiat

**Hint: kasuta seda koodi**
```
=SQRT((VLOOKUP(NUMBERVALUE(DistanceTable[[#Headers];[1]]);Training!$A$1:$O$126;3;FALSE)-VLOOKUP(NUMBERVALUE(DistanceTable[@[TestID]:[TestID]]);Test!$A$1:$O$54;3;FALSE))^2+(VLOOKUP(NUMBERVALUE(DistanceTable[[#Headers];[1]]);Training!$A$1:$O$126;4;FALSE)-VLOOKUP(NUMBERVALUE(DistanceTable[@[TestID]:[TestID]]);Test!$A$1:$O$54;4;FALSE))^2+(VLOOKUP(NUMBERVALUE(DistanceTable[[#Headers];[1]]);Training!$A$1:$O$126;5;FALSE)-VLOOKUP(NUMBERVALUE(DistanceTable[@[TestID]:[TestID]]);Test!$A$1:$O$54;5;FALSE))^2+(VLOOKUP(NUMBERVALUE(DistanceTable[[#Headers];[1]]);Training!$A$1:$O$126;6;FALSE)-VLOOKUP(NUMBERVALUE(DistanceTable[@[TestID]:[TestID]]);Test!$A$1:$O$54;6;FALSE))^2+(VLOOKUP(NUMBERVALUE(DistanceTable[[#Headers];[1]]);Training!$A$1:$O$126;7;FALSE)-VLOOKUP(NUMBERVALUE(DistanceTable[@[TestID]:[TestID]]);Test!$A$1:$O$54;7;FALSE))^2*(VLOOKUP(NUMBERVALUE(DistanceTable[[#Headers];[1]]);Training!$A$1:$O$126;8;FALSE)-VLOOKUP(NUMBERVALUE(DistanceTable[@[TestID]:[TestID]]);Test!$A$1:$O$54;8;FALSE))^2+(VLOOKUP(NUMBERVALUE(DistanceTable[[#Headers];[1]]);Training!$A$1:$O$126;9;FALSE)-VLOOKUP(NUMBERVALUE(DistanceTable[@[TestID]:[TestID]]);Test!$A$1:$O$54;9;FALSE))^2+(VLOOKUP(NUMBERVALUE(DistanceTable[[#Headers];[1]]);Training!$A$1:$O$126;10;FALSE)-VLOOKUP(NUMBERVALUE(DistanceTable[@[TestID]:[TestID]]);Test!$A$1:$O$54;10;FALSE))^2+(VLOOKUP(NUMBERVALUE(DistanceTable[[#Headers];[1]]);Training!$A$1:$O$126;11;FALSE)-VLOOKUP(NUMBERVALUE(DistanceTable[@[TestID]:[TestID]]);Test!$A$1:$O$54;11;FALSE))^2+(VLOOKUP(NUMBERVALUE(DistanceTable[[#Headers];[1]]);Training!$A$1:$O$126;12;FALSE)-VLOOKUP(NUMBERVALUE(DistanceTable[@[TestID]:[TestID]]);Test!$A$1:$O$54;12;FALSE))^2+(VLOOKUP(NUMBERVALUE(DistanceTable[[#Headers];[1]]);Training!$A$1:$O$126;13;FALSE)-VLOOKUP(NUMBERVALUE(DistanceTable[@[TestID]:[TestID]]);Test!$A$1:$O$54;13;FALSE))^2)
```


### 5. Lähimate naabrite arvutamine
	- Leiame igale testveinile k-lähimat naabri treeningveinide hulgast
	- Vaatame, mis "klassi" need naabrid on
	- Võtame populaarseima ja see ongi meie ennustus!
	
**Hint: Kasuta seda koodi**
```
=VLOOKUP(NUMBERVALUE(INDEX(DistanceTable[#headers],MATCH(SMALL($Distance.$B2:$DV2,1),$Distance.2:2,0))),$Training.$A$1:$O$126,2,0)
```
*Funktsioonis SMALL, väärtus 1 näitab, et 1. väikseim väärtus. See on vaja asendada igas tulbas vastavalt 2, 3 jne.*
	
### 6. Testime mudelit!

- Tee uus tööleht "KNN model" nt
- Ennustame iga veini jaoks, mis klassi see kuulub
- 

**Hint: Kasuta seda koodi, et saada ennustus. NB! See on k=4 jaoks**
```

=IFS($B$1=1;'Nearest neighbors'!B6;$B$1=2;IFERROR(INDEX('Nearest neighbors'!B6:C6;MODE(MATCH('Nearest neighbors'!B6:C6; 'Nearest neighbors'!B6:C6;0)));'Nearest neighbors'!B6);$B$1=3;IFERROR(INDEX('Nearest neighbors'!B6:D6;MODE(MATCH('Nearest neighbors'!B6:D6; 'Nearest neighbors'!B6:D6;0)));'Nearest neighbors'!B6);$B$1=4;IFERROR(INDEX('Nearest neighbors'!B6:E6;MODE(MATCH('Nearest neighbors'!B6:E6; 'Nearest neighbors'!B6:E6;0)));'Nearest neighbors'!B6))
```

**Mis oli tegelik klass**
```
=VLOOKUP(A4,$Test.A1:O54,2,0)
```


