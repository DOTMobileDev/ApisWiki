# [DotMobile] Events Service

Servizio per l'accesso ad eventi dei target, in particolare relativi a segmenti di accensione e prese di forza.

NB: i dati sulle distanze sono espressi in km e le date sono in formato UTC.

(WSDL)[http://webservices.dotmobile.it/eventsservice.asmx?WSDL]

**Esempio di chiamata in C# di una funzione del Event Services:** (nell'esempio EventServices è il nome del namespace)

```
using (EventsServices.EventsServiceSoapClient client = new EventsServices.EventsServiceSoapClient()){
    DateTime fromUTC = DateTime.Today.Date.ToUniversalTime();
    DateTime toUTC = DateTime.UtcNow;
    EventsServices.MembershipSoapHeader header = new EventsServices.MembershipSoapHeader();
    header.Username = @"99999\johndoe"; //99999 = codice cliente, johndoe = username
    header.Password = "12345"; //12345 = password
    client.Open();
    EventSegmentDTO[] ret = client.GetAccSegments(header, "DOTMOBI073", fromUTC, toUTC);
    client.Close();
}
```

**Metodi:**

--

# GetAccSegments
Metodo per ottenere, in uno specificato periodo, i segmenti di accensione-spegnimento del mezzo, calcolando per ciascuno la distanza percorsa e identificandone tutti i punti di tracking, per i quali ne viene verificata l'appartenenza ad una o più zone.

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/eventsservice.asmx?op=GetAccSegments]

```
public EventSegmentDTO[] GetAccSegments(string targetCode, DateTime fromUtc, DateTime toUtc)
```

**targetCode:** oggetto da tracciare;
**fromUtc:** data di partenza per l'intervallo di interesse (formato UTC);
**toUtc:** data conclusiva per l'intervallo di interesse (formato UTC).

--

# GetForceSegments
Metodo per ottenere, in uno specificato periodo, i segmenti di accensione-spegnimento delle prese di forza mezzo, calcolando per ciascuno la distanza percorsa e identificandone tutti i punti di tracking, per i quali ne viene verificata l'appartenenza ad una o più zone.

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/eventsservice.asmx?op=GetForceSegments]

```
public EventSegmentDTO[] GetForceSegments(string targetCode, DateTime fromUtc, DateTime toUtc)
```

**targetCode:** oggetto da tracciare;
**fromUtc:** data di partenza per l'intervallo di interesse (formato UTC);
**toUtc:** data conclusiva per l'intervallo di interesse (formato UTC).
