﻿# Specificatie topics

Er zijn een aantal topics:
- sensoren_rijbaan
- sensoren_speciaal
- sensoren_bruggen
- stoplichten
- tijd
- voorrangsvoertuig

![Envelope](../assets/zeromq/envelope.png)

De topics hebben één publisher en één subscriber. De gedachte is dat een publisher een envelope (topic) met een body (bericht) stuurt. De subscriber is dan verantwoordelijk voor het verder afhandelen van de envelope. De publisher is de eigenaar van de data, en update de inhoud van deze topic.
De subscriber krijgt een update als een topic veranderd, en kan de inhoud alleen maar lezen.
De synchronisatie van topic-data tussen publisher en subscriber wordt beheerd door [ZeroMQ](../zeromq/README.md).
Er wordt gebruik gemaakt van het PUB/SUB-patroon.

## Uitgangspunten: 
- Verbinding is live (lage latency < 100ms)
- Pakketverlies wordt afgehandeld achter de schermen.
- Het protocol houdt ***G E E N*** rekening met ongelukken etc.
- Het protocol richt zich ***N I E T*** op een specifieke implementatie (van controller en/of simulatie)
- Simulatie geeft simulatietijd door aan controller (via topic [tijd](./tijd/README.md)).
- Elke keer dat een topic gestuurd wordt, bevat dit de volledige data van die topic. (geen gedeeltelijke update berichten)

Voor elke topic is een aparte specificatie geschreven.