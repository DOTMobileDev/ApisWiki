# [DotMobile] Geofencing

Servizio per le attività nelle zone

NB: i dati sulle distanze sono espressi in km e le date sono in formato UTC.

(WSDL)[http://webservices.dotmobile.it/geofencing.asmx?WSDL]

**Esempio di chiamata in C# di una funzione di Geofencing:** (nell'esempio Geofencing è il nome del namespace)

```
using (Geofencing.GeofencingSoapClient client = new Geofencing.GeofencingSoapClient()){
    DateTime fromUTC = DateTime.Today.Date.ToUniversalTime();
    DateTime toUTC = DateTime.UtcNow;
    Geofencing.MembershipSoapHeader header = new Geofencing.MembershipSoapHeader();
    header.Username = @"99999\johndoe"; //99999 = codice cliente, johndoe = username
    header.Password = "12345"; //12345 = password
    client.Open();
    Geofencing.ZoneActivityRecord[] zoneActivityRecords = client.GetZoneActivities(header, fromUTC, toUTC);
    client.Close();
}
```

**Metodi:**

--

# GetZoneActivity
Metodo che, quando un target effettua un segmento di ingresso-uscita da una zona, ne riporta gli elementi salienti quali tempo di permanenza nella zona e km percorsi.

(Esempio di richiesta e risposta XML)[http://webservices.dotmobile.it/geofencing.asmx?op=GetZoneActivities]

```
public ZoneActivityRecord[] GetZoneActivities(DateTime fromUtc, DateTime toUtc)
```

**fromUtc:** data di partenza per l'intervallo di interesse (formato UTC);
**toUtc:** data conclusiva per l'intervallo di interesse (formato UTC).
