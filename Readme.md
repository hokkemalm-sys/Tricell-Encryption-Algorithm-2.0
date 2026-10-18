1. Projektbeskrivning
Tricell Encryption Algorithm 2.0 är en krypteringsmetod som utvecklades som en del av kursen Introduktion till IT. Syftet var att skapa ett meddelande som är svårt att tolka utan kunskap om krypteringsmetoden och dess nyckel.
Vi använde Google Sheets för att utföra beräkningarna och omvandla meddelandets tecken. Krypteringen kombinerar en numerisk förskjutning av Unicode-kodpunkter med salt i början och slutet av meddelandet.
2. Hur algoritmen fungerar
Krypteringen består av följande steg:
	1	Förbered meddelandet: Originaltexten förbereds för kryptering. I vår implementation används understreck i stället för mellanslag.
	2	Konvertera tecken: Varje tecken omvandlas till sitt numeriska Unicode-värde.
	3	Förskjut kodpunkterna: Det hexadecimala värdet 7B32 omvandlas till decimaltalet 31538, som adderas till varje teckens Unicode-värde.
	4	Skapa nya tecken: De resulterande värdena omvandlas tillbaka till Unicode-tecken.
	5	Lägg till salt: Salt läggs till i början och slutet av det krypterade meddelandet. I vår konfiguration används 2 tecken som prefix och 4 tecken som suffix.
Resultatet blir ett meddelande vars tecken skiljer sig från originaltextens och som kräver kännedom om metoden för att kunna återskapas.
3. Nyckel och parametrar
Parameter
Värde
Betydelse
Salt prefix
2 tecken
Antal salttecken i början
Salt suffix
4 tecken
Antal salttecken i slutet
Förskjutning
7B32 (hex)
Värdet som adderas till varje Unicode-kodpunkt
Förskjutning i decimalform
31538
Samma värde uttryckt decimalt
4. Dekryptering
För att återskapa originalmeddelandet behöver mottagaren känna till saltets längder och förskjutningsvärdet.
	1	Ta bort saltet från början och slutet av meddelandet.
	2	Omvandla varje återstående tecken till dess Unicode-kodpunkt.
	3	Subtrahera 31538 från varje kodpunkt.
	4	Omvandla de resulterande kodpunkterna till tecken.
	5	Ersätt understreck med mellanslag för att återställa textens ursprungliga format.
Om samtliga steg utförs korrekt kan originalmeddelandet återskapas.
5. Exempel
Förskjutning: 7B32 (hexadecimalt) = 31538 (decimalt).
För varje tecken beräknas den krypterade kodpunkten enligt följande:
Krypterad kodpunkt = Ursprunglig kodpunkt + 31538
Vid dekryptering används den omvända beräkningen:
Ursprunglig kodpunkt = Krypterad kodpunkt - 31538
6. Begränsningar
Metoden utvecklades som en del av en utbildningsuppgift och ska inte betraktas som säker kryptering för känslig information. En fast och känd förskjutning kan reverseras, och salt i sig gör inte en krypteringsmetod säker. Projektet illustrerar hur teckenkodning, numeriska operationer och kunskap om en algoritm påverkar möjligheten att återskapa ett meddelande.
7. Projektets innehåll
Detta repository dokumenterar Tricell Encryption Algorithm 2.0 genom en beskrivning av metoden, dess parametrar och hur kryptering och dekryptering går till.
