# [DotMobile] Position Services

Servizio mediante il quale è possibile accedere a determinate informazioni riguardanti i target associati all'utente, nello specifico relative al collocamento dei dispositivi in una posizione in un determinato momento.

NB: i dati sulle distanze sono espressi in km e le date sono in formato UTC.

(WSDL)[http://webservices.dotmobile.it/positionsservice.asmx?WSDL]

**Esempio di chiamata in C# di una funzione del Position Services:** (nell'esempio PositionServices è il nome del namespace)

```
using (PositionServices.PositionsServiceSoapClient client = new PositionServices.PositionsServiceSoapClient()){
    PositionServices.MembershipSoapHeader header = new PositionServices.MembershipSoapHeader();
    header.Username = @"99999\johndoe"; //99999 = codice cliente, johndoe = username
    header.Password = "12345"; //12345 = password
    client.Open();
    double mileage = client.GetMileage(header, "JOHNDOE001", null); //JOHNDOE001 = codice target
    client.Close();
}
```

**Metodi:**

--

# GetCANData
Metodo per ottenere dalla box i dati del CAN, come ad esempio distanza percorsa, temperatura del motore, rpm, livello e consumo del carburante; i dati si riferiscono a un intervallo temporale compreso tra due date da indicare.

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/positionsservice.asmx?op=GetCANData]

```
public TargetCANDataDTO[] GetCANData(string target, string tag, DateTime fromUtc, DateTime toUtc)
```

**target:** oggetto da tracciare;
**tag:** tag dell'oggetto;
**fromUtc:** data di partenza per l'intervallo di interesse (formato UTC);
**toUtc:** data conclusiva per l'intervallo di interesse (formato UTC).

--

# GetDatedMileage
Metodo per ottenere la distanza percorsa in km e la data a cui si riferisce l'informazione; i km percorsi sono sia quelli registrati dalla box sia quelli che eventualmente erano presenti prima dell'installazione (dato richiesto all'utente in un primo momento).

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/positionsservice.asmx?op=GetDatedMileage]

```
public MileageDTO GetDatedMileage(string target, string tag)
```

**target:** oggetto da tracciare;
**tag:** tag dell'oggetto;

--

# GetDatedPartialMileage
Metodo per ottenere la distanza percorsa in km in un intervallo temporale specificato e la data a cui si riferisce l'informazione.

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/positionsservice.asmx?op=GetDatedPartialMileage]

```
public MileageDTO GetDatedPartialMileage(string target, string tag, DateTime fromUtc, DateTime toUtc)
```

**target:** oggetto da tracciare;
**tag:** tag dell'oggetto;
**fromUtc:** data di partenza per l'intervallo di interesse (formato UTC);
**toUtc:** data conclusiva per l'intervallo di interesse (formato UTC).

--

# GetHistory
Metodo per sapere, in un intervallo temporale indicato tra due date, dove e quando è stato localizzato il target richiesto; le informazioni sulla posizione sono indicate in latitudine e longitudine.

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/positionsservice.asmx?op=GetHistorye]

```
public TargetGeocodedPositionDTO[] GetHistory(string target, string tag, DateTime fromUtc, DateTime toUtc)
```

**target:** oggetto da tracciare;
**tag:** tag dell'oggetto;
**fromUtc:** data di partenza per l'intervallo di interesse (formato UTC);
**toUtc:** data conclusiva per l'intervallo di interesse (formato UTC).

--

# GetHistoryWithGeocoding
Metodo per sapere, in un intervallo temporale indicato tra due date, dove e quando è stato localizzato il target richiesto; oltre alle coordinate geografiche è presente il servizio di geocodifica della posizione nel quale una posizione indicata in latitudine e longitudine viene tradotta in un indirizzo stradale.

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/positionsservice.asmx?op=GetHistoryWithGeocoding]

```
public TargetGeocodedPositionDTO[] GetHistoryWithGeocoding(string target, string tag, DateTime fromUtc, DateTime toUtc)
```

**target:** oggetto da tracciare;
**tag:** tag dell'oggetto;
**fromUtc:** data di partenza per l'intervallo di interesse (formato UTC);
**toUtc:** data conclusiva per l'intervallo di interesse (formato UTC).

--

# GetLastPosition
Metodo per sapere dove e quando è stato localizzato il target richiesto l'ultima volta che l'apparato ha inviato una posizione; le informazioni sulla posizione sono indicate in latitudine e longitudine.

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/positionsservice.asmx?op=GetLastPosition]

```
public TargetGeocodedPositionDTO GetLastPosition(string target, string tag)
```

**target:** oggetto da tracciare;
**tag:** tag dell'oggetto;

--

# GetLastPositionWithGeocoding
Metodo per sapere dove e quando è stato localizzato il target richiesto l'ultima volta che l'apparato ha inviato una posizione; oltre alle coordinate geografiche è presente il servizio di geocodifica della posizione nel quale una posizione indicata in latitudine e longitudine viene tradotta in un indirizzo stradale.

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/positionsservice.asmx?op=GetLastPositionWithGeocoding]

```
public TargetGeocodedPositionDTO GetLastPositionWithGeocoding(string target, string tag)
```

**target:** oggetto da tracciare;
**tag:** tag dell'oggetto;

--

# GetLastPositions
Metodo per sapere dove e quando sono stati localizzati tutti i target dell'utente l'ultima volta che gli apparati hanno inviato una posizione; le informazioni sulla posizione sono indicate in latitudine e longitudine.

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/positionsservice.asmx?op=GetLastPositions]

```
public TargetGeocodedPositionDTO[] GetLastPositions()
```

--

# GetLastPositionsWithGeocoding
Metodo per sapere dove e quando sono stati localizzati tutti i target dell'utente l'ultima volta che gli apparati hanno inviato una posizione; oltre alle coordinate geografiche è presente il servizio di geocodifica della posizione nel quale una posizione indicata in latitudine e longitudine viene tradotta in un indirizzo stradale.

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/positionsservice.asmx?op=GetLastPositionWithGeocoding]

```
public TargetGeocodedPositionDTO[] GetLastPositionsWithGeocoding()
```

--

# GetMileage
Metodo che restituisce la distanza percorsa in km dal target; include anche un eventuale chilometraggio precedente all'installazione della box (dato già inserito dall'utente).

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/positionsservice.asmx?op=GetMileage]

```
public double GetMileage(string target, string tag)
```

**target:** oggetto da tracciare;
**tag:** tag dell'oggetto;

--

# GetPartialMileage
Metodo che restituisce la distanza percorsa in km dal target in un intervallo temporale compreso tra due date.

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/positionsservice.asmx?op=GetLastPositionWithGeocoding]

```
http://webservices.dotmobile.it/positionsservice.asmx?op=GetPartialMileage
```

**target:** oggetto da tracciare;
**tag:** tag dell'oggetto;
**fromUtc:** data di partenza per l'intervallo di interesse (formato UTC);
**toUtc:** data conclusiva per l'intervallo di interesse (formato UTC).

--

# SetMileage
Metodo che consente di impostare il chilometraggio della box a un valore desiderato.

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/positionsservice.asmx?op=SetMileage]

```
public void SetMileage(string target, string tag, double mileage)
```

**target:** oggetto da tracciare;
**tag:** tag dell'oggetto;
**mileage:** numero di km da impostare.

--

# TestConnection
Metodo che invia un messaggio di test alla box che risponderà con il messaggio stesso preceduto da "Received ".

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/positionsservice.asmx?op=TestConnection]

```
public string TestConnection(string testMessage)
```

**testMessage:** messaggio di test da inviare.