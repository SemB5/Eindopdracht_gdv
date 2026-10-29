# Mini-level — Inleveren

**Naam:** Sem Bakker  
**Klas:** SD1C  
**Datum:** 29-10-2026  
**Les:** GDV Les 6

---

## Wat heb ik gemaakt?

Ik heb een mini-level gemaakt waarin je munten moet verzamelen. Op de route staat een rode laser die de speler schade geeft als je hem aanraakt. Daarom heb ik ook een healing-object toegevoegd, zodat je je HP weer kunt aanvullen en het level kunt uitspelen.

---

## Screenshot / GIF van je level

![Mini-level preview](images/game.png)

---

## Bewegend object

De munten in mijn game draaien rond. Ik heb dit gedaan door een rotatiescript aan de munten toe te voegen. Het script draait de munt elke frame een stukje om de Y-as. Door `Time.deltaTime` te gebruiken draait de munt op elke computer even snel.

```csharp
public float speed = 100f;

void Update()
{
    // Draai de munt om de Y-as
    transform.Rotate(0, speed * Time.deltaTime, 0);
}
```

---

## Collider of trigger

Mijn munten hebben een trigger. Als de speler de munt aanraakt, verzamelt hij de munt: de teller gaat met 1 omhoog, ik laat de score zien in de Console en de munt verdwijnt uit het level. Ik controleer met de tag `coin` of het object echt een munt is.

```csharp
private void OnTriggerEnter(Collider other)
{
    if (other.CompareTag("coin"))
    {
        coins++;

        Debug.Log("coins: " + coins);

        Destroy(other.gameObject);
    }
}
```

---

## Logica met `if` of `switch`

Ik heb `if` gebruikt voor het health-systeem. Als de speler schade krijgt, gaat er HP af. Met een `if` zorg ik ervoor dat de health nooit lager dan 0 wordt. Daarnaast heb ik een healing-object gemaakt: als de speler schade heeft gehad, kan hij dit object pakken om weer meer HP te krijgen.

```csharp
public void TakeDamage(int damage)
{
    health -= damage;

    if (health < 0)
    {
        health = 0;
    }

    Debug.Log("Health: " + health);
}

// Plak hier ook de code van je healing-object (bijv. health += ...)
```

---

## Eigen extra idee

Mijn extra idee is dat de speler kan springen. Dit heb ik zo gemaakt dat je de springknop echt nodig hebt om de munten te verzamelen, omdat sommige munten hoog liggen. Zo is het level meer dan alleen lopen en wordt het een beetje uitdagender.

```csharp
// Optioneel: plak hier de code van je sprong

```

---

## Evaluatie

### Wat ging goed? en waarom?

Ik ben eigenlijk best trots op alles wat ik heb gemaakt. Ik had niet echt gedacht dat ik zoiets zou kunnen. Het is gelukt om munten te laten draaien en verzamelen, een health-systeem te maken en de speler te laten springen.

### Wat vond je lastig? en waarom?

Code schrijven vind ik gewoon lastig, omdat je precies de goede woorden en tekens moet gebruiken. Maar het lukt me nu al veel beter dan in het begin.

### Wat zou je een volgende keer anders doen?

Ik heb in deze opdracht veel geleerd, want daarvoor wist ik nog niks van het maken van een game. Een volgende keer wil ik meer gebruikmaken van wat ik nu weet en mijn level uitbreiden met meer dingen.
