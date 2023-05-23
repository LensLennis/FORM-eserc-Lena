Lena Lorenzo – S5212736 
Commento per la seconda parte dell’esercita

1 Documentazione / Commenti

1.a Generare la documentazione usando Doxygen e verificare se la documentazione prodotta permette di orientarsi nella struttura del progetto software. Indicare i punti che potrebbero essere migliorati.

-La documentazione è stata generata correttamente, nonostante sia confusionario l’inserimento nel main sia di commenti con il prefisso “\” sia di commenti con il prefisso “@”, creando confusione nella simbologia. Ci si può orientare senza confusione tra le funzioni; il diagramma (da noi chiamato pallogramma) è visualizzato correttamente; ogni variabile è dichiarata correttamente ed è abbastanza comprensibile la descrizione, nonostante si potesse essere più precisi nel lessico o nella spiegazione di alcune.

1.b Utilizzando la documentazione e i commenti inseriti nei file .ccp e .h verificare se il progetto software aderisce alle specifiche assegnate durante la prima settimana. Indicare le eventuali specifiche non rispettate.

-Il progetto contiene documentazione e commenti corretti nonostante, come sopracitato, sia un po’ confusionaria la descrizione nel main e la dichiarazioni di alcuni commenti con doxygen per via dell’ibrido “\” e “@”. Non è stato particolarmente apprezzato l’uso sia di lingua inglese che di lingua italiana, poiché potrebbe suggerire (se non conoscessi le persone direttamente e non sapessi che hanno scritto loro stessi) che sia stato effettuato un copia incolla senza un controllo.

1.c Verificare che il file README introduca correttamente lo scopo del progetto software e che dia sufficienti informazioni per un corretto uso dell’interfaccia a riga di comando. Indicare eventuali mancanze e/o possibili migliorie.

-Non è stato creato un file readme da nessuno dei due membri della coppia, quindi non mi posso esprimere a riguardo.


2 Compilazione e prima sessione di test

2.a Verificare se è possibile compilare il progetto – Sì, è possibile.
2.b Test dell’interfaccia a riga di comando: l’interfaccia funziona correttamente? L’interfaccia è di facile utilizzo? Quali prove sono state eseguite per fare il test? 

-L’interfaccia funziona correttamente, il menu è intuitivo e sia la creazione di nuovi oggetti che la stampa dei valori di area e perimetro sono funzionanti.
Per quanto riguarda i test effettuati, ho provato dapprima a creare 3 oggetti (uno per tipo) e a farne stampare i valori, e fin qua tutto funziona correttamente.
Per fare una prova più veloce, è possibile inserire direttamente “1 2 3  2  2 3  3  3 4  4”.
A questo punto ho provato ad inserire, al posto dei numeri, alcune lettere, e sia nel menu che nell’inserimento dei parametri il programma va in loop e dà problemi, creando innumerevoli poligoni. 
Un altro test effettuato è stato il controllo della stampa vuota: non viene stampato, come dovrebbe, nessun poligono, anche se sarebbe stato più chiaro un messaggio con il controllo di “MAX_NUM” (particolarmente apprezzato invece nell’indicizzazione dei poligoni).
Un grosso problema del programma è la mancanza del delete per i poligoni: non è stato chiamato il distruttore perciò i poligoni rimangono “costruiti” nella RAM, potenzialmente creando problemi.
Non è stata scritta la definizione degli operatori == e = nella classe triangolo isoscele, così come la definizione di “<<” e “>>”.




3 Seconda sessione di test

3.a Definire una procedura di test che permetta di identificare possibili bug nel codice prodotto per le singole classi e i singoli metodi di ogni classe

***DA ULTIMARE***





	#include "isotriangle.h"
	#include "rhombus.h"
	#include "rectangle.h"
	#define MAX_NUM 10
	using namespace std;
	int main() {
	int number = 0;
	Polygon* universo[MAX_NUM] = { 0 };
	universo[number] = new Rectangle(2, 3);
	universo[number]->Draw();
	cout << "Draw of the rectangle succesful. Deleting..." << endl;
	delete universo[number];
	cout << "______________________________________________" << endl;
	universo[number] = new Rhombus(2, 3);
	universo[number]->Draw();
	cout << "Draw of the Rhombus succesful. Deleting..." << endl;
	delete universo[number];
	cout << "______________________________________________" << endl;
	universo[number] = new IsoTriangle(2, 3);
	universo[number]->Draw();
	cout << "Draw of the Triangle succesful. Deleting..." << endl;
	delete universo[number];
	cout << "______________________________________________" << endl;
	universo[number=3] = new IsoTriangle;
	universo[number = 4] = new IsoTriangle(2, 3);
	universo[3] = universo[4];
	universo[3]->Draw();
	if (universo[3] == universo[4])
		cout << "Operators == and = work fine." << endl;
	else { cout << "There is some issue with == || =."; }
	cout << "______________________________________________" << endl;
	universo[3]->Reset();
	universo[2]=new IsoTriangle(0,0);
	if (universo[3] == universo[2])
		cout << "Reset works as well." << endl;
	else cout << "Reset does not work." << endl;
	cout << "______________________________________________" << endl;
	//cout << universo[2]->ErrorMessage("PROVA DELLA FUNZIONE ERRORE: OK") << endl;
	//cout << universo[2]->WarningMessage("PROVA DELLA FUNZIONE WARNING: OK") << endl;
	//bisogna commentare questa parte poichè non essendo definito << non è possibile scriverla
	return 0;

	}
