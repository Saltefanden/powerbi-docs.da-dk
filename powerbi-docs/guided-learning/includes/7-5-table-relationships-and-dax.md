Med Power BI kan du oprette relationer mellem flere tabeller, herunder tabeller, der stammer fra helt forskellige datakilder. Du kan se disse relationer for en datamodel i visningen **Relationer** i Power BI Desktop.

![](media/7-5-table-relationships-and-dax/dax-relationships_1.png)

## <a name="dax-relational-functions"></a>DAX – relationelle funktioner
DAX har **relationelle funktioner**, der giver dig mulighed for at interagere med tabeller med fastlagte relationer.

Du kan returnere værdien af en kolonne, eller du kan returnere alle rækker i en relation, ved hjælp af DAX-funktioner.

For eksempel følger funktionen **TABLE** relationer og returnerer værdien af en kolonne, mens **RELATEDTABLE** følger relationer og returnerer en hel tabel, der er filtreret, så den kun indeholder relaterede rækker.

![](media/7-5-table-relationships-and-dax/dax-relationships_2.png)

Funktionen **RELATED** fungerer på *mange til en*-relationer, mens **RELATEDTABLE** er til *en til mange*-relationer.

Du kan bruge relationelle funktioner til at oprette udtryk, der indeholder værdier på tværs af flere tabeller. DAX returnerer et resultat med disse funktioner, uanset hvor lang kæden af relationen er.

> Videoindholdet er fra [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit)
> 
> 
