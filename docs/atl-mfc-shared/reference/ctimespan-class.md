---
title: Classe CTimeSpan
ms.date: 10/18/2018
f1_keywords:
- CTimeSpan
- ATLTIME/ATL::CTimeSpan
- ATLTIME/ATL::CTimeSpan::CTimeSpan
- ATLTIME/ATL::CTimeSpan::Format
- ATLTIME/ATL::CTimeSpan::GetDays
- ATLTIME/ATL::CTimeSpan::GetHours
- ATLTIME/ATL::CTimeSpan::GetMinutes
- ATLTIME/ATL::CTimeSpan::GetSeconds
- ATLTIME/ATL::CTimeSpan::GetTimeSpan
- ATLTIME/ATL::CTimeSpan::GetTotalHours
- ATLTIME/ATL::CTimeSpan::GetTotalMinutes
- ATLTIME/ATL::CTimeSpan::GetTotalSeconds
- ATLTIME/ATL::CTimeSpan::Serialize64
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
ms.openlocfilehash: 14aa5eb52e2c631a92e40ae7053c566284e00e57
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317500"
---
# <a name="ctimespan-class"></a>Classe CTimeSpan

Un temps, qui est stocké à l’interne comme le nombre de secondes dans la durée.

## <a name="syntax"></a>Syntaxe

```
class CTimeSpan
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CTimeSpan::CTimeSpan](#ctimespan)|Construit `CTimeSpan` des objets de différentes manières.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTimeSpan::Format](#format)|Convertit `CTimeSpan` un en une chaîne formatée.|
|[CTimeSpan::GetDays](#getdays)|Retourne une valeur qui représente le `CTimeSpan`nombre de jours complets dans ce .|
|[CTimeSpan::GetHours](#gethours)|Retourne une valeur qui représente le nombre d’heures dans la journée en cours (-23 à 23).|
|[CTimeSpan::GetMinutes](#getminutes)|Retourne une valeur qui représente le nombre de minutes dans l’heure en cours (-59 à 59).|
|[CTimeSpan::GetSeconds](#getseconds)|Retourne une valeur qui représente le nombre de secondes dans la minute actuelle (-59 à 59).|
|[CTimeSpan::GetTimeSpan](#gettimespan)|Retourne la valeur `CTimeSpan` de l’objet.|
|[CTimeSpan::GetTotalHours](#gettotalhours)|Retourne une valeur qui représente le nombre `CTimeSpan`total d’heures complètes dans ce .|
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|Retourne une valeur qui représente le nombre `CTimeSpan`total de minutes complètes dans ce .|
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|Retourne une valeur qui représente le nombre `CTimeSpan`total de secondes complètes dans ce .|
|[CTimeSpan::Serialize64](#serialize64)|Sérialise les données à partir ou à partir d’une archive.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur -](#operator_add_-)|Ajoute et soustrait des `CTimeSpan` objets.|
|[opérateur - -MD](#operator_add_eq_-_eq)|Ajoute et soustrait un `CTimeSpan` objet `CTimeSpan`à et de cela .|
|[l’opérateur < etc.](#ctimespan_comparison_operators)|Compare deux valeurs temporelles relatives.|

## <a name="remarks"></a>Notes

`CTimeSpan`n’a pas de classe de base.

`CTimeSpan`les fonctions convertissent les secondes en diverses combinaisons de jours, d’heures, de minutes et de secondes.

L’objet `CTimeSpan` est stocké dans une structure **__time64_t,** soit 8 octets.

Une classe d’accompagnement, [CTime](../../atl-mfc-shared/reference/ctime-class.md), représente un temps absolu.

Les `CTime` `CTimeSpan` cours et les classes ne sont pas conçus pour la dérivation. Parce qu’il n’y a `CTime` pas `CTimeSpan` de fonctions virtuelles, la taille des deux et des objets est exactement 8 octets. La plupart des fonctions des membres sont inline.

Pour `CTimeSpan`plus d’informations sur l’utilisation , voir les articles Date and [Time](../../atl-mfc-shared/date-and-time.md), et Time [Management](../../c-runtime-library/time-management.md) dans la référence de la bibliothèque *Run-Time*.

## <a name="requirements"></a>Spécifications

**En-tête:** atltime.h

## <a name="ctimespan-comparison-operators"></a><a name="ctimespan_comparison_operators"></a>Opérateurs de comparaison CTimeSpan

Opérateurs de comparaison.

```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*Span*<br/>
Objet à comparer.

### <a name="return-value"></a>Valeur de retour

Ces opérateurs comparent deux valeurs temporelles relatives. Ils retournent VRAI si la condition est vraie; autrement FALSE.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

## <a name="ctimespanctimespan"></a><a name="ctimespan"></a>CTimeSpan::CTimeSpan

Construit `CTimeSpan` des objets de différentes manières.

```
CTimeSpan() throw();
CTimeSpan(__time64_t time) throw();

CTimeSpan(
    LONG lDays,
    int nHours,
    int nMins,
    int nSecs) throw();
```

### <a name="parameters"></a>Paramètres

*timeSpanSrc*<br/>
Un `CTimeSpan` objet qui existe déjà.

*Temps*<br/>
Une valeur de temps **__time64_t,** c’est-à-propos du nombre de secondes dans le laps de temps.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Jours, heures, minutes et secondes, respectivement.

### <a name="remarks"></a>Notes

Tous ces constructeurs `CTimeSpan` créent un nouvel objet para initialisé avec le temps relatif spécifié. Chaque constructeur est décrit ci-dessous :

- `CTimeSpan( );`Construit un objet uninitialisé. `CTimeSpan`

- `CTimeSpan( const CTimeSpan& );`Construit un `CTimeSpan` objet `CTimeSpan` à partir d’une autre valeur.

- `CTimeSpan( __time64_t );`Construit un `CTimeSpan` objet à partir **d’un type __time64_t.**

- `CTimeSpan( LONG, int, int, int );`Construit un `CTimeSpan` objet à partir de composants avec chaque composant limité aux plages suivantes :

   |Composant|Plage|
   |---------------|-----------|
   |*lDays (en)*|0-25 000 (environ)|
   |*nHours*|0-23|
   |*nMins*|0-59|
   |*nSecs (en anglais)*|0-59|

Notez que la version Debug de la Microsoft Foundation Class Library affirme si un ou plusieurs des composants de la journée de temps est hors de portée. Il est de votre responsabilité de valider les arguments avant d’appeler.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

## <a name="ctimespanformat"></a><a name="format"></a>CTimeSpan::Format

Génère une chaîne formatée qui `CTimeSpan`correspond à cela .

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Paramètres

*pFormat*, *pszFormat*<br/>
Une chaîne de formatage similaire à la `printf` chaîne de formatage. Les codes de formatage,`%`précédés d’un signe `CTimeSpan` en pourcentage, sont remplacés par le composant correspondant. D’autres caractères de la chaîne de formatage sont copiés inchangés à la chaîne retournée. La valeur et la signification `Format` des codes de formatage pour sont énumérés ci-dessous:

- **%D** Nombre total de jours dans cette`CTimeSpan`

- **%H** Heures dans la journée actuelle

- **%M** Procès-verbal dans l’heure actuelle

- **%S** Secondes dans la minute actuelle

- **%%** Signe de pourcentage

*nID*<br/>
L’ID de la chaîne qui identifie ce format.

### <a name="return-value"></a>Valeur de retour

Un `CString` objet qui contient le temps formaté.

### <a name="remarks"></a>Notes

La version Debug de la bibliothèque vérifie les codes de formatage et affirme si le code n’est pas dans la liste ci-dessus.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

## <a name="ctimespangetdays"></a><a name="getdays"></a>CTimeSpan::GetDays

Retourne une valeur qui représente le `CTimeSpan`nombre de jours complets dans ce .

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de jours complets de 24 heures dans le laps de temps. Cette valeur peut être négative si le délai est négatif.

### <a name="remarks"></a>Notes

Notez que l’heure d’été peut entraîner le `GetDays` retour d’un résultat potentiellement surprenant. Par exemple, lorsque l’heure `GetDays` d’été est en vigueur, indique le nombre de jours entre le 1er avril et le 1er mai comme 29, et non 30, parce qu’un jour d’avril est raccourci d’une heure et ne compte donc pas comme une journée complète.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

## <a name="ctimespangethours"></a><a name="gethours"></a>CTimeSpan::GetHours

Retourne une valeur qui représente le nombre d’heures dans la journée en cours (-23 à 23).

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’heures en cours. La plage est de -23 à 23.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

## <a name="ctimespangetminutes"></a><a name="getminutes"></a>CTimeSpan::GetMinutes

Retourne une valeur qui représente le nombre de minutes dans l’heure en cours (-59 à 59).

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de minutes dans l’heure actuelle. La gamme est de -59 à 59.

### <a name="example"></a>Exemple

Voir l’exemple pour [GetHours](#gethours).

## <a name="ctimespangetseconds"></a><a name="getseconds"></a>CTimeSpan::GetSeconds

Retourne une valeur qui représente le nombre de secondes dans la minute actuelle (-59 à 59).

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de secondes dans la minute actuelle. La gamme est de -59 à 59.

### <a name="example"></a>Exemple

Voir l’exemple pour [GetHours](#gethours).

## <a name="ctimespangettimespan"></a><a name="gettimespan"></a>CTimeSpan::GetTimeSpan

Retourne la valeur `CTimeSpan` de l’objet.

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur `CTimeSpan` actuelle de l’objet.

## <a name="ctimespangettotalhours"></a><a name="gettotalhours"></a>CTimeSpan::GetTotalHours

Retourne une valeur qui représente le nombre `CTimeSpan`total d’heures complètes dans ce .

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre total d’heures complètes dans ce `CTimeSpan`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

## <a name="ctimespangettotalminutes"></a><a name="gettotalminutes"></a>CTimeSpan::GetTotalMinutes

Retourne une valeur qui représente le nombre `CTimeSpan`total de minutes complètes dans ce .

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre total de `CTimeSpan`minutes complètes dans ce .

### <a name="example"></a>Exemple

Voir l’exemple pour [GetTotalHours](#gettotalhours).

## <a name="ctimespangettotalseconds"></a><a name="gettotalseconds"></a>CTimeSpan::GetTotalSeconds

Retourne une valeur qui représente le nombre `CTimeSpan`total de secondes complètes dans ce .

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre total de `CTimeSpan`secondes complètes dans ce .

### <a name="example"></a>Exemple

Voir l’exemple pour [GetTotalHours](#gettotalhours).

## <a name="ctimespanoperator---"></a><a name="operator_add_-"></a>CTimeSpan::opérateur, -

Ajoute et soustrait des `CTimeSpan` objets.

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*Span*<br/>
La valeur à `CTimeSpan` ajouter à l’objet.

### <a name="return-value"></a>Valeur de retour

Un `CTimeSpan` objet représentant le résultat de l’opération.

### <a name="remarks"></a>Notes

Ces deux opérateurs vous permettent `CTimeSpan` d’ajouter et de soustraire des objets les uns aux autres.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

## <a name="ctimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>CTimeSpan: :opérateur , -MD

Ajoute et soustrait un `CTimeSpan` objet `CTimeSpan`à et de cela .

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*Span*<br/>
La valeur à `CTimeSpan` ajouter à l’objet.

### <a name="return-value"></a>Valeur de retour

L’objet mis à jour. `CTimeSpan`

### <a name="remarks"></a>Notes

Ces opérateurs vous permettent d’ajouter et de soustraire un `CTimeSpan` objet à et de cela `CTimeSpan`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

## <a name="ctimespanserialize64"></a><a name="serialize64"></a>CTimeSpan::Serialize64

> [!NOTE]
> Cette méthode n’est disponible que dans les projets MFC.

Sérialise les données associées à la variable du membre vers ou depuis une archive.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*Ar*<br/>
L’objet `CArchive` que vous souhaitez mettre à jour.

### <a name="return-value"></a>Valeur de retour

L’objet mis à jour. `CArchive`

## <a name="see-also"></a>Voir aussi

[asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
