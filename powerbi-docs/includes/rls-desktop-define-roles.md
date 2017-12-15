## <a name="define-roles-and-rules-within-power-bi-desktop"></a>Definer roller og regler i Power BI Desktop
Du kan definere roller og regler i Power BI Desktop. Når du publicerer til Power BI, publicerer det også rolledefinitionerne.

Følg nedenstående trin for at definere sikkerhedsroller.

1. Importér data til din Power BI Desktop-rapport, eller konfigurer en DirectQuery-forbindelse.
   
   > [!NOTE]
   > Du kan ikke definere roller i Power BI Desktop for dynamiske forbindelser til Analysis Services. Det skal du gøre i Analysis Services-modellen.
   > 
   > 
2. Vælg fanen **Modellering**.
3. Vælg **Administrer roller**.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
4. Vælg **Opret**.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
5. Angiv et navn for rollen. 
6. Vælg den tabel, hvor du vil anvende en DAX-regel.
7. Angiv DAX-udtrykkene. Dette udtryk skal returnere true eller false. Eksempel: [Entity ID] = “Value”.
   
   > [!NOTE]
   > Du kan bruger *username()* i udtrykket. Vær opmærksom på, at *username()* har formatet *DOMÆNE\brugernavn* i Power BI Desktop. I Power BI-tjenesten vil det være i formatet af brugerens UPN. Du kan alternativt bruge *userprincipalname()*, som altid returnerer brugeren i formatet af brugerens hovednavn (UPN).
   > 
   > 
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)
8. Når du har oprettet DAX-udtrykket, kan du vælge at markere afkrydsningsfeltet over udtryksfeltet for at validere udtrykket.
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
9. Vælg **Gem**.

Du kan ikke tildele brugere til en rolle i Power BI Desktop. Det skal gøres i Power BI-tjenesten. Du kan aktivere dynamisk sikkerhed i Power BI Desktop ved at bruge DAX-funktionen *username()* eller *userprincipalname()* og have konfigureret de relevante relationer.
