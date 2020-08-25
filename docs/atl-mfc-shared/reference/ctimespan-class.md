---
title: CTimeSpan, classe
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
ms.openlocfilehash: 0c13aa0d8f6c46db3b018283ab2a408a3f9531e1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832020"
---
# <a name="ctimespan-class"></a>CTimeSpan, classe

Durée, qui est stockée en interne comme nombre de secondes dans l’intervalle de temps.

## <a name="syntax"></a>Syntaxe

```
class CTimeSpan
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CTimeSpan::CTimeSpan](#ctimespan)|Construit `CTimeSpan` des objets de différentes façons.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTimeSpan :: format](#format)|Convertit `CTimeSpan` en chaîne mise en forme.|
|[CTimeSpan::GetDays](#getdays)|Retourne une valeur qui représente le nombre de jours complets dans ce `CTimeSpan` .|
|[CTimeSpan :: GetHours](#gethours)|Retourne une valeur qui représente le nombre d’heures dans le jour actuel (-23 à 23).|
|[CTimeSpan :: GetMinutes](#getminutes)|Retourne une valeur qui représente le nombre de minutes dans l’heure actuelle (-59 à 59).|
|[CTimeSpan :: GetSeconds](#getseconds)|Retourne une valeur qui représente le nombre de secondes de la minute actuelle (-59 à 59).|
|[CTimeSpan :: GetTimeSpan](#gettimespan)|Retourne la valeur de l' `CTimeSpan` objet.|
|[CTimeSpan::GetTotalHours](#gettotalhours)|Retourne une valeur qui représente le nombre total d’heures complètes dans ce `CTimeSpan` .|
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|Retourne une valeur qui représente le nombre total de minutes entières dans ce `CTimeSpan` .|
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|Retourne une valeur qui représente le nombre total de secondes complètes dans ce `CTimeSpan` .|
|[CTimeSpan::Serialize64](#serialize64)|Sérialise les données vers ou à partir d’une archive.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur +-](#operator_add_-)|Ajoute et soustrait des `CTimeSpan` objets.|
|[opérateur + =-=](#operator_add_eq_-_eq)|Ajoute et soustrait un `CTimeSpan` objet à ce `CTimeSpan` .|
|[opérateur = = < etc.](#ctimespan_comparison_operators)|Compare deux valeurs d’heure relatives.|

## <a name="remarks"></a>Notes

`CTimeSpan` n’a pas de classe de base.

`CTimeSpan` les fonctions convertissent les secondes en différentes combinaisons de jours, d’heures, de minutes et de secondes.

L' `CTimeSpan` objet est stocké dans une structure **__time64_t** , qui est de 8 octets.

Une classe complémentaire, [ctime](../../atl-mfc-shared/reference/ctime-class.md), représente une heure absolue.

Les `CTime` classes et ne `CTimeSpan` sont pas conçues pour la dérivation. Étant donné qu’il n’existe pas de fonctions virtuelles, la taille des `CTime` `CTimeSpan` objets et est exactement de 8 octets. La plupart des fonctions membres sont Inline.

Pour plus d’informations sur l’utilisation de `CTimeSpan` , consultez les articles [date et heure](../../atl-mfc-shared/date-and-time.md)et [gestion du temps](../../c-runtime-library/time-management.md) dans la référence de la *bibliothèque Runtime*.

## <a name="requirements"></a>Configuration requise

**En-tête :** atltime. h

## <a name="ctimespan-comparison-operators"></a><a name="ctimespan_comparison_operators"></a> CTimeSpan opérateurs de comparaison

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

*répartis*<br/>
Objet à comparer.

### <a name="return-value"></a>Valeur renvoyée

Ces opérateurs comparent deux valeurs d’heure relatives. Elles retournent la valeur TRUE si la condition est true ; Sinon, FALSe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

## <a name="ctimespanctimespan"></a><a name="ctimespan"></a> CTimeSpan::CTimeSpan

Construit `CTimeSpan` des objets de différentes façons.

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
`CTimeSpan`Objet qui existe déjà.

*time*<br/>
Valeur d’heure de **__time64_t** , qui correspond au nombre de secondes dans l’intervalle de temps.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Jours, heures, minutes et secondes, respectivement.

### <a name="remarks"></a>Notes

Tous ces constructeurs créent un nouvel `CTimeSpan` objet initialisé avec l’heure relative spécifiée. Chaque constructeur est décrit ci-dessous :

- `CTimeSpan( );` Construit un objet non initialisé `CTimeSpan` .

- `CTimeSpan( const CTimeSpan& );` Construit un `CTimeSpan` objet à partir d’une autre `CTimeSpan` valeur.

- `CTimeSpan( __time64_t );` Construit un `CTimeSpan` objet à partir d’un type de **__time64_t** .

- `CTimeSpan( LONG, int, int, int );` Construit un `CTimeSpan` objet à partir de composants dont chaque composant est soumis aux limites suivantes :

   |Composant|Plage|
   |---------------|-----------|
   |*lDays*|0-25000 (approximativement)|
   |*nHours*|0-23|
   |*nMins*|0-59|
   |*nSecs*|0-59|

Notez que la version de débogage de l’bibliothèque MFC (Microsoft Foundation Class) déclare si un ou plusieurs composants de l’heure de la journée sont hors limites. Il vous incombe de valider les arguments avant d’appeler.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

## <a name="ctimespanformat"></a><a name="format"></a> CTimeSpan :: format

Génère une chaîne mise en forme qui correspond à ce `CTimeSpan` .

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Paramètres

*pFormat*, *pszFormat*<br/>
Chaîne de mise en forme similaire à la `printf` chaîne de mise en forme. Les codes de mise en forme, précédés d’un signe de pourcentage ( `%` ), sont remplacés par le `CTimeSpan` composant correspondant. Les autres caractères de la chaîne de mise en forme sont copiés sans modification dans la chaîne retournée. La valeur et la signification des codes de mise en forme pour `Format` sont répertoriées ci-dessous :

- **% D** Nombre total de jours dans ce `CTimeSpan`

- **% H** Heures du jour en cours

- **% M** Minutes dans l’heure actuelle

- **% S** Secondes dans la minute actuelle

- **%%** Signe de pourcentage

*nID*<br/>
ID de la chaîne qui identifie ce format.

### <a name="return-value"></a>Valeur renvoyée

`CString`Objet qui contient l’heure mise en forme.

### <a name="remarks"></a>Notes

La version de débogage de la bibliothèque vérifie les codes de mise en forme et les assertions si le code ne figure pas dans la liste ci-dessus.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

## <a name="ctimespangetdays"></a><a name="getdays"></a> CTimeSpan::GetDays

Retourne une valeur qui représente le nombre de jours complets dans ce `CTimeSpan` .

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre de jours de 24 heures dans l’intervalle de temps. Cette valeur peut être négative si l’intervalle de temps est négatif.

### <a name="remarks"></a>Notes

Notez que l’heure d’été peut entraîner `GetDays` le retour d’un résultat potentiellement surprenant. Par exemple, lorsque l’heure d’été est activée, `GetDays` indique le nombre de jours entre le 1er avril et le 1er mai comme 29, et non 30, car un jour en avril est réduit d’une heure et n’est donc pas comptabilisé comme un jour complet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

## <a name="ctimespangethours"></a><a name="gethours"></a> CTimeSpan :: GetHours

Retourne une valeur qui représente le nombre d’heures dans le jour actuel (-23 à 23).

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’heures dans le jour actuel. La plage est comprise entre-23 et 23.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

## <a name="ctimespangetminutes"></a><a name="getminutes"></a> CTimeSpan :: GetMinutes

Retourne une valeur qui représente le nombre de minutes dans l’heure actuelle (-59 à 59).

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre de minutes de l’heure actuelle. La plage est comprise entre-59 et 59.

### <a name="example"></a>Exemple

Consultez l’exemple pour [getHours](#gethours).

## <a name="ctimespangetseconds"></a><a name="getseconds"></a> CTimeSpan :: GetSeconds

Retourne une valeur qui représente le nombre de secondes de la minute actuelle (-59 à 59).

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre de secondes de la minute actuelle. La plage est comprise entre-59 et 59.

### <a name="example"></a>Exemple

Consultez l’exemple pour [getHours](#gethours).

## <a name="ctimespangettimespan"></a><a name="gettimespan"></a> CTimeSpan :: GetTimeSpan

Retourne la valeur de l' `CTimeSpan` objet.

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur actuelle de l' `CTimeSpan` objet.

## <a name="ctimespangettotalhours"></a><a name="gettotalhours"></a> CTimeSpan::GetTotalHours

Retourne une valeur qui représente le nombre total d’heures complètes dans ce `CTimeSpan` .

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre total d’heures effectuées dans ce `CTimeSpan` .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

## <a name="ctimespangettotalminutes"></a><a name="gettotalminutes"></a> CTimeSpan::GetTotalMinutes

Retourne une valeur qui représente le nombre total de minutes entières dans ce `CTimeSpan` .

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre total de minutes complètes dans ce `CTimeSpan` .

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetTotalHours](#gettotalhours).

## <a name="ctimespangettotalseconds"></a><a name="gettotalseconds"></a> CTimeSpan::GetTotalSeconds

Retourne une valeur qui représente le nombre total de secondes complètes dans ce `CTimeSpan` .

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre total de secondes complètes dans ce `CTimeSpan` .

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetTotalHours](#gettotalhours).

## <a name="ctimespanoperator---"></a><a name="operator_add_-"></a> CTimeSpan :: Operator +,-

Ajoute et soustrait des `CTimeSpan` objets.

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*répartis*<br/>
Valeur à ajouter à l' `CTimeSpan` objet.

### <a name="return-value"></a>Valeur renvoyée

`CTimeSpan`Objet représentant le résultat de l’opération.

### <a name="remarks"></a>Notes

Ces deux opérateurs vous permettent d’ajouter et de soustraire des objets l’un `CTimeSpan` à l’autre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

## <a name="ctimespanoperator---"></a><a name="operator_add_eq_-_eq"></a> CTimeSpan :: Operator + =,-=

Ajoute et soustrait un `CTimeSpan` objet à ce `CTimeSpan` .

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*répartis*<br/>
Valeur à ajouter à l' `CTimeSpan` objet.

### <a name="return-value"></a>Valeur renvoyée

Objet mis à jour `CTimeSpan` .

### <a name="remarks"></a>Notes

Ces opérateurs vous permettent d’ajouter et de soustraire un `CTimeSpan` objet à ce `CTimeSpan` .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

## <a name="ctimespanserialize64"></a><a name="serialize64"></a> CTimeSpan::Serialize64

> [!NOTE]
> Cette méthode est uniquement disponible dans les projets MFC.

Sérialise les données associées à la variable membre vers ou à partir d’une archive.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*AR*<br/>
`CArchive`Objet que vous souhaitez mettre à jour.

### <a name="return-value"></a>Valeur renvoyée

Objet mis à jour `CArchive` .

## <a name="see-also"></a>Voir aussi

[asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
