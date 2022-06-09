# proiectJavaPathfinding
Acest proiect implementeaza in Java, in mod asincron folosind thread-uri, algoritmul de pathfinding A*, care este defapt algoritmul Dijkstra euristic.  
Proiectul in sine este un plugin pentru jocul video Minecraft, intrucat jocul este o platforma ideala pentru a testa algoritmi de pathfinding.  
Pentru a rula proiectul, plugin-ul trebuie compilat in Intellij, apoi fisierul .jar fara "original" in nume, din folderul "target" trebuie mutat in folderul "plugins" al serverului de Minecraft Paper (V1.18.1) la alegere.  

Modul de functionare: 
Serverele de Minecraft sunt implicit sincrone, adica toate operatiunile au loc pe acelasi thread. Daca as efectua calculele de pathfinding pe thread-ul principal, intreg server-ul s-ar bloca in timpul efectuarii calculelor. Din acest motiv, fiecare calcul are loc intr-un Thread separat, iar rezultatul este scris intr-o lista, din care thread-ul principal citeste si aplica rezultatele (construind path-ul), apoi curata lista.  
Calculul propriu-zis al path-urilor se bazeaza pe algoritmul A*, cu urmatoarele precizari:  

- Nodurile specifice algoritmului A* sunt reprezentate de blocurile (cuburile) din joc, pentru care jocul ofera un API extensiv pentru a stoca si obtine date despre acestea, inclusiv un sistem de coordonate spatiale.
- Nodurle vecine unui nod anume sunt reprezentate de blocurile care se afla la distanta de un bloc fata de acesta, intr-una din directiile cardinale. 
- Algoritmul va considera tipul de bloc Material.AIR ca fiind spatiu liber, si orice alt tip de bloc ca fiind un obstacol/zid
- Euristica aleasa pentru aceasta implementare a algoritmului A* este formula Pitagora aplicata coordonatelor blocurilor.

Acest proiect a fost initial conceput ca si extensie de joc, deci poate contine unele quirks si feature-uri pe care nu le-am dezactivat, desi cred ca le-am eliminat pe toate care ar putea incurca demonstratia. Din acelasi motiv, structurile de date din cod sunt mai complexe decat este necesar pentru proiect, dar tin sa precizez ca scopul initial era simularea multiplelor entitati capabile de pathfinding.
