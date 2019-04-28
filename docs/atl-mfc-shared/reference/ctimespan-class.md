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
ms.openlocfilehash: 3c80260c1f57e49a34b4e9f3331f4d0d69ab30ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252524"
---
# <a name="ctimespan-class"></a>CTimeSpan, classe

Un laps de temps, ce qui est stocké en interne en tant que le nombre de secondes dans l’intervalle de temps.

## <a name="syntax"></a>Syntaxe

```
class CTimeSpan
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CTimeSpan::CTimeSpan](#ctimespan)|Construit `CTimeSpan` objets de différentes manières.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CTimeSpan::Format](#format)|Convertit un `CTimeSpan` dans une chaîne mise en forme.|
|[CTimeSpan::GetDays](#getdays)|Retourne une valeur qui représente le nombre de jours terminées dans ce `CTimeSpan`.|
|[CTimeSpan::GetHours](#gethours)|Retourne une valeur qui représente le nombre d’heures du jour actuel (-23 à 23).|
|[CTimeSpan::GetMinutes](#getminutes)|Retourne une valeur qui représente le nombre de minutes à l’heure actuelle (entre-59 et 59).|
|[CTimeSpan::GetSeconds](#getseconds)|Retourne une valeur qui représente le nombre de secondes dans la minute actuelle (entre-59 et 59).|
|[CTimeSpan::GetTimeSpan](#gettimespan)|Retourne la valeur de la `CTimeSpan` objet.|
|[CTimeSpan::GetTotalHours](#gettotalhours)|Retourne une valeur qui représente le nombre total d’heures complètes dans ce `CTimeSpan`.|
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|Retourne une valeur qui représente le nombre total de minutes complètes dans ce `CTimeSpan`.|
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|Retourne une valeur qui représente le nombre total de secondes complètes dans ce `CTimeSpan`.|
|[CTimeSpan::Serialize64](#serialize64)|Sérialise les données vers ou à partir d’une archive.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur + -](#operator_add_-)|Ajoute et soustrait `CTimeSpan` objets.|
|[operator += -=](#operator_add_eq_-_eq)|Ajoute et soustrait un `CTimeSpan` objet vers et depuis ce `CTimeSpan`.|
|[operator == < etc.](#ctimespan_comparison_operators)|Compare deux valeurs de temps relatif.|

## <a name="remarks"></a>Notes

`CTimeSpan` n’a pas d’une classe de base.

`CTimeSpan` fonctions convertissent secondes pour différentes combinaisons de jours, heures, minutes et secondes.

Le `CTimeSpan` objet est stocké dans un **__time64_t** structure, ce qui est de 8 octets.

Une classe Compagnon, [CTime](../../atl-mfc-shared/reference/ctime-class.md), représente une heure absolue.

Le `CTime` et `CTimeSpan` classes ne sont pas conçues pour la dérivation. Étant donné qu’aucune fonction virtuelle, la taille des deux `CTime` et `CTimeSpan` objets correspond exactement à 8 octets. La plupart des fonctions de membre sont inline.

Pour plus d’informations sur l’utilisation de `CTimeSpan`, consultez les articles [Date et heure](../../atl-mfc-shared/date-and-time.md), et [gestion du temps](../../c-runtime-library/time-management.md) dans le *Run-Time Library Reference*.

## <a name="requirements"></a>Configuration requise

**En-tête :** atltime.h

##  <a name="ctimespan_comparison_operators"></a>  Opérateurs de comparaison de CTimeSpan

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

*span*<br/>
Objet à comparer.

### <a name="return-value"></a>Valeur de retour

Ces opérateurs comparent deux valeurs de temps relatif. Elles retournent la valeur TRUE si la condition est true ; Sinon, FALSE.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

##  <a name="ctimespan"></a>  CTimeSpan::CTimeSpan

Construit `CTimeSpan` objets de différentes manières.

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

*time*<br/>
Un **__time64_t** valeur de temps, ce qui correspond au nombre de secondes dans l’intervalle de temps.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Jours, heures, minutes et secondes, respectivement.

### <a name="remarks"></a>Notes

Toutes ces constructeurs créent un nouveau `CTimeSpan` objet initialisé avec l’heure relative spécifiée. Chaque constructeur est décrite ci-dessous :

- `CTimeSpan( );` Construit un non initialisé `CTimeSpan` objet.

- `CTimeSpan( const CTimeSpan& );` Construit un `CTimeSpan` objet à partir d’un autre `CTimeSpan` valeur.

- `CTimeSpan( __time64_t );` Construit un `CTimeSpan` de l’objet à partir d’un **__time64_t** type.

- `CTimeSpan( LONG, int, int, int );` Construit un `CTimeSpan` objet à partir de composants avec chaque composant est limité aux plages suivantes :

   |Composant|Plage|
   |---------------|-----------|
   |*lDays*|0-25 000 (environ)|
   |*nHours*|0-23|
   |*nMins*|0-59|
   |*nSecs*|0-59|

Notez que la version Debug de la bibliothèque Microsoft Foundation Class déclare si un ou plusieurs des composants heure est hors limites. Il vous incombe de valider les arguments avant d’appeler.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

##  <a name="format"></a>  CTimeSpan::Format

Génère une chaîne mise en forme qui correspond à cet `CTimeSpan`.

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Paramètres

*pFormat*, *pszFormat*<br/>
Une mise en forme de chaîne similaire à la `printf` mise en forme de chaîne. Mise en forme de codes, précédés d’un pourcentage (`%`) vous connecter, sont remplacés par le correspondantes `CTimeSpan` composant. Autres caractères dans la chaîne mise en forme sont copiées sans modification à la chaîne retournée. La valeur et la signification des codes de mise en forme pour `Format` sont répertoriées ci-dessous :

- **%D** nombre total de jours dans ce `CTimeSpan`

- **%H** heures du jour actuel

- **%M** minutes à l’heure actuelle

- **%S** secondes dans la minute actuelle

- **%%** Signe de pourcentage

*nID*<br/>
L’ID de la chaîne qui identifie ce format.

### <a name="return-value"></a>Valeur de retour

Un `CString` objet qui contient l’heure de mise en forme.

### <a name="remarks"></a>Notes

La version Debug de la bibliothèque vérifie les codes de mise en forme et indique si le code n’est pas dans la liste ci-dessus.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

##  <a name="getdays"></a>  CTimeSpan::GetDays

Retourne une valeur qui représente le nombre de jours terminées dans ce `CTimeSpan`.

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de jours de 24 heures terminées dans l’intervalle de temps. Cette valeur peut être négative si l’intervalle de temps est un nombre négatif.

### <a name="remarks"></a>Notes

Notez que l’heure d’été peut provoquer `GetDays` pour retourner un résultat potentiellement surprenant. Par exemple, lorsque l’heure d’été est en vigueur, `GetDays` indique le nombre de jours entre le 1er avril et le 1er mai comme 29, 30 pas, car un jour en avril est réduit en une heure et par conséquent ne compte pas comme une journée complète.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

##  <a name="gethours"></a>  CTimeSpan::GetHours

Retourne une valeur qui représente le nombre d’heures du jour actuel (-23 à 23).

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’heures du jour actuel. La plage est -23 et 23.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

##  <a name="getminutes"></a>  CTimeSpan::GetMinutes

Retourne une valeur qui représente le nombre de minutes à l’heure actuelle (entre-59 et 59).

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de minutes à l’heure actuelle. La plage est entre-59 et 59.

### <a name="example"></a>Exemple

Consultez l’exemple de [GetHours](#gethours).

##  <a name="getseconds"></a>  CTimeSpan::GetSeconds

Retourne une valeur qui représente le nombre de secondes dans la minute actuelle (entre-59 et 59).

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de secondes dans la minute actuelle. La plage est entre-59 et 59.

### <a name="example"></a>Exemple

Consultez l’exemple de [GetHours](#gethours).

##  <a name="gettimespan"></a>  CTimeSpan::GetTimeSpan

Retourne la valeur de la `CTimeSpan` objet.

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur actuelle de la `CTimeSpan` objet.

##  <a name="gettotalhours"></a>  CTimeSpan::GetTotalHours

Retourne une valeur qui représente le nombre total d’heures complètes dans ce `CTimeSpan`.

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre total d’heures complètes dans cet `CTimeSpan`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

##  <a name="gettotalminutes"></a>  CTimeSpan::GetTotalMinutes

Retourne une valeur qui représente le nombre total de minutes complètes dans ce `CTimeSpan`.

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre total de minutes complètes dans cet `CTimeSpan`.

### <a name="example"></a>Exemple

Consultez l’exemple de [GetTotalHours](#gettotalhours).

##  <a name="gettotalseconds"></a>  CTimeSpan::GetTotalSeconds

Retourne une valeur qui représente le nombre total de secondes complètes dans ce `CTimeSpan`.

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre total de secondes complètes dans cet `CTimeSpan`.

### <a name="example"></a>Exemple

Consultez l’exemple de [GetTotalHours](#gettotalhours).

##  <a name="operator_add_-"></a>  CTimeSpan::operator +, -

Ajoute et soustrait `CTimeSpan` objets.

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
La valeur à ajouter à la `CTimeSpan` objet.

### <a name="return-value"></a>Valeur de retour

Un `CTimeSpan` objet représentant le résultat de l’opération.

### <a name="remarks"></a>Notes

Ces deux opérateurs permettent d’ajouter et de soustraire `CTimeSpan` objets vers et depuis les uns des autres.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  CTimeSpan::operator +=, -=

Ajoute et soustrait un `CTimeSpan` objet vers et depuis ce `CTimeSpan`.

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
La valeur à ajouter à la `CTimeSpan` objet.

### <a name="return-value"></a>Valeur de retour

La mise à jour `CTimeSpan` objet.

### <a name="remarks"></a>Notes

Ces opérateurs permettent d’ajouter et de soustraire un `CTimeSpan` objet vers et depuis ce `CTimeSpan`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

##  <a name="serialize64"></a>  CTimeSpan::Serialize64

> [!NOTE]
>  Cette méthode est uniquement disponible dans les projets MFC.

Sérialise les données associées à la variable de membre vers ou à partir d’une archive.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*ar*<br/>
Le `CArchive` objet que vous souhaitez mettre à jour.

### <a name="return-value"></a>Valeur de retour

La mise à jour `CArchive` objet.

## <a name="see-also"></a>Voir aussi

[asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
