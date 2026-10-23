# Les meves fitxes de funcions de Google Sheets

> Copia aquesta plantilla al teu repositori com a `funcions.md`. Fes una fitxa per funció.
> Escriu amb les teves paraules. Els exemples de la lliga, provats al teu full.

---

## COUNTIFS

**Documentació:** <https://support.google.com/docs/answer/3256550?hl=ca>

**Què fa:** Compta el nombre de cel·les, en un interval determinat, que compleixen una o més condicions.

**Sintaxi:**

```
=COUNTIFS(interval1, criteri1, [interval2, criteri2])
```

| Argument | Obligatori? | Què és |
|---|---|---|
| `...` | Sí | ... |
| `...` | No | ... |

**Exemple de la documentació:** `COUNTIFS(A1:A10, ">20", B1:B10, "<30")`

**El meu exemple amb la lliga:**

```
=COUNTIFS(Jornada1!G2:G49, "Laberint", Jornada1!N2:N49, "OK")
```

Resultat: `11` Hi ha 11 curses completades de la categoria Laberint.

**Compte!** (una cosa que diu l'apartat *Notes* de la documentació i que pot fer fallar la fórmula)
Els intervals addicionals han de contenir el mateix nombre de files i columnes que interval_de_criteris1.
---

## SUMIFS

**Documentació:**<https://support.google.com/docs/answer/3238496?sjid=7136460724739179651-EU>
**Què fa:** Suma el valor de cel·les, en un interval determinat, que compleixen una o més condicions.

**Sintaxi:**

```
=SUMIFS(interval_de_suma, interval_de_criteris1, criteri1, [interval_de_criteris2, criteri2, etc.])
```

| Argument | Obligatori? | Què és |
|---|---|---|
| `...` | Sí | ... |
| `...` | No | ... |

**Exemple de la documentació:** `SUMIFS(A1:A10, B1:B10, ">20")`

**El meu exemple amb la lliga:**

```
=SUMIFS(Jornada1!M2:M49, Jornada1!G2:G49, "Laberint"))
```

Resultat: `878.99` Preu total de la categoria Laberint.

---

## IFS

**Documentació:** <https://support.google.com/docs/answer/7014145?hl=ca&sjid=1738065501235460319-EU>

**Què fa:** Considera diverses condicions impostes per l'usuari, en un rang de cel·les, retornarà el que haguem posat o simplement el valor de la cel·la que correspon a la condició imposta.
**Sintaxi:**

```
=IFS(condició, valor1, [condició2, valor2, …])
```

| Argument | Obligatori? | Què és |
|---|---|---|
| `...` | Sí | ... |
| `...` | No | ... |

**Exemple de la documentació:** `IFS(A1>90, "A", A1>80, "B", A1>70, "C")`

**El meu exemple amb la lliga:**

```
=IFS(N2="DSQ", 0, N2="DNF", 1, J2<=25.74, 6, N2="OK", 3)
```

Resultat: `6`Són els punts de la fila 2.
---

## XLOOKUP

**Documentació:** <https://support.google.com/docs/answer/12405947?hl=ca&sjid=17946853577362252109-EU>

**Què fa:** Busca un valor en un interval per saber la seva posició, i et retorna el valor de una cel·la que esta en un altre interval pero a la mateixa posició 
**Sintaxi:**

```
=XLOOKUP(valor_de_cerca; interval_cerca; interval_de_resultats, valor_no_trobat; mode_de_coincidència; mode_de_cerca)
```

| Argument | Obligatori? | Què és |
|---|---|---|
| `...` | Sí | ... |
| `...` | No | ... |

**Exemple de la documentació:** `XLOOKUP("Poma"; A2:A; E2:E) per substituir VLOOKUP("Poma"; A2:E; 5; FALSE)`

**El meu exemple amb la lliga:**

```
=XLOOKUP("Laberint", Categories!A2:A4, Categories!B2:B4)
```

Resultat: `500` és el valor que hi ha en una cel·la en el rang B2:B4, en la mateixa posició que el valor "Laberint" en el rang A2:A4.

---


## Preguntes de lectura

1. Què passa amb `SUMIFS` si l'interval de suma i l'interval del criteri no tenen la mateixa mida? Dona error `#VALUE!`
2. Què torna `IFS` si cap de les condicions és certa? Com ho podeu evitar? Dona error `#N/A`, a no ser que posis un `Valor2`
3. Per a què serveix el quart argument de `XLOOKUP`? Què passa si no el poseu i no es troba res? Diu quin text donar si no es troba cap valor. Sensd dona `#N/A`
4. Escriu la sintaxi de `SUMIF` i la de `SUMIFS` una sota l'altra. Què canvia de lloc? Canvia el interval de suma per el interval de criteri.
   `=SUMIF(interval_criteri, criteri, [interval_suma])`
   `=SUMIFS(interval_suma, interval_criteri1, criteri1, ...)`
