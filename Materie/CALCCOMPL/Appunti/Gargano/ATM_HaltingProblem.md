Il linguaggio ATM non è decidibile:
Definiamo ATM: {(M,w) | M è una MT ed M accetta w}

Non possiamo costruire una MT che ci può dire se la stringa in input è accettata oppure no. 

Dimostrazione standard: Assumiamo che Atm è decidibile e chiamiamo Halt la MT che decide il linguaggio, Halt è una MT che si ferma sempre e funziona cosi:
Usiamo <> per denotare il progetto o la descrizione di una MT

Halt(<M,w>): accetta se M accetta w, rifiuta altrimenti

Ora costruiamo una nuova macchina 

Flipper(<M>): result = Halt(<M,M>) e rifiuta se result = 'accept' altrimenti accetta, quindi questa macchina effettua una negazione sul risultato di Halt

Se adesso diamo in input <Flipper> a Flipper...

Flipper(<Flipper>): rifiuta se Flipper accetta <Flipper> altrimenti accetta, ma questa è una contraddizione!

Diagonalizzazione: Prendiamo una matrice con i righe e j colonne ed in ogni riga troviamo delle MT: M0,M1,M2... Mi
Nelle colonne troviamo delle *descrizioni* delle MT: <M0>,<M1>,<M2>...<Mj>

Usiamo la macchina H (Halt)
con input nella forma: <Mi,Mj> per determinare lo stato di una cella che può essere 'reject' oppure 'accept'

La macchina D prende in input la stessa macchina con la sua descrizione ed il suo output sarà l'opposto di H (Halt): Quindi l'opposto di Halt(<M,M>)
Quando la macchina D esegue <D> (la sua descrizione) allora essa darà come risultato l'opposto di se stessa.
Questo corrisponde alla negazione di tutte le entry della diagonale principale, quindi stiamo dicendo che non esiste una riga in questa tabella infinita in cui tutte le entry
siano la negazione della diagonale, ma come tesi avevamo detto che H era un decisore per ATM.

-----
  
SAT is NP-Complete: PROOF

Ogni problema di classe NP si riduce polinomialmente a SAT

Usiamo una NTM, e costruiamo una tabella che sarà grande n^k * n^k
Le righe della tabella sono i rami di ogni calcolo della NTM
Consideriamo una delle celle della tabella la cella i, questa dipenderà soltanto dalle 3 celle del calcolo avvenuto nella riga precedente
Perchè la testina si può essere spostata da una delle due celle adiacenti o aver modificato il contenuto di quella in cui si trova, quindi vogliamo
Ogni per ogni cella abbiamo una formula booleana (un circuito) che soddisfa un certo compito.
E per ognugna dovremmo dire se essa è soddisfacibile
La tabella accetta se ogni riga accetta

La complessità totale è : O(n^2k) che è ancora polinomiale, quindi abbiamo trovato una riduzione polinomiale da un problema NP arbitrario a SAT
