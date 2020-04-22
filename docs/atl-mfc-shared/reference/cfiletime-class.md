---
title: Classe CFileTime
ms.date: 10/18/2018
f1_keywords:
- CFileTime
- ATLTIME/ATL::CFileTime
- ATLTIME/ATL::CFileTime::CFileTime
- ATLTIME/ATL::CFileTime::GetCurrentTime
- ATLTIME/ATL::CFileTime::GetTime
- ATLTIME/ATL::CFileTime::LocalToUTC
- ATLTIME/ATL::CFileTime::SetTime
- ATLTIME/ATL::CFileTime::UTCToLocal
- ATLTIME/ATL::CFileTime::Day
- ATLTIME/ATL::CFileTime::Hour
- ATLTIME/ATL::CFileTime::Millisecond
- ATLTIME/ATL::CFileTime::Minute
- ATLTIME/ATL::CFileTime::Second
- ATLTIME/ATL::CFileTime::Week
helpviewer_keywords:
- CFileTime class
- shared classes, CFileTime
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
ms.openlocfilehash: fd19d941365c7772363417ce3e9225bd9b0300b2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748841"
---
# <a name="cfiletime-class"></a>Classe CFileTime

Ce cours fournit des méthodes pour gérer les valeurs de date et d’heure associées à un fichier.

## <a name="syntax"></a>Syntaxe

```
class CFileTime :  public FILETIME
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFileTime::CFileTime](#cfiletime)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFileTime::GetCurrentTime](#getcurrenttime)|Appelez cette fonction statique `CFileTime` pour récupérer un objet qui représente la date et l’heure du système actuel.|
|[CFileTime::GetTime](#gettime)|Appelez cette méthode pour récupérer `CFileTime` l’heure de l’objet.|
|[CFileTime::LocalToUTC](#localtoutc)|Appelez cette méthode pour convertir un temps de fichier local en un temps de fichier basé sur le temps universel coordonné (UTC).|
|[CFileTime::SetTime](#settime)|Appelez cette méthode pour définir la `CFileTime` date et l’heure stockées par l’objet.|
|[CFileTime::UTCToLocal](#utctolocal)|Appelez cette méthode pour convertir le temps basé sur le temps universel coordonné (UTC) en temps de fichier local.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CFileTime::opérateur -](#operator_-)|Cet opérateur est utilisé pour effectuer `CFileTime` `CFileTimeSpan` la soustraction sur un ou un objet.|
|[CFileTime::opérateur !](#operator_neq)|Cet opérateur compare `CFileTime` deux objets à l’inégalité.|
|[CFileTime::opérateur](#operator_add)|Cet opérateur permet d'effectuer une addition sur un objet `CFileTimeSpan`.|
|[CFileTime::opérateur](#operator_add_eq)|Cet opérateur permet d'effectuer une addition sur un objet `CFileTimeSpan` et d'assigner le résultat à l'objet actuel.|
|[CFileTime::opérateur&lt;](#operator_lt)|Cet opérateur compare deux objets `CFileTime` pour déterminer le plus petit.|
|[CFileTime::opérateur&lt;=](#operator_lt_eq)|Cet opérateur compare deux objets `CFileTime` pour déterminer le plus petit ou leur égalité.|
|[CFileTime::opérateur](#operator_eq)|L’opérateur de l’affectation.|
|[CFileTime::opérateur -MD](#operator_-_eq)|Cet opérateur est utilisé pour effectuer `CFileTimeSpan` la soustraction sur un objet et attribuer le résultat à l’objet actuel.|
|[CFileTime::opérateur](#operator_eq_eq)|Cet opérateur compare deux objets `CFileTime` pour déterminer leur égalité.|
|[CFileTime::opérateur&gt;](#operator_gt)|Cet opérateur compare deux objets `CFileTime` pour déterminer le plus grand.|
|[CFileTime::opérateur&gt;=](#operator_gt_eq)|Cet opérateur compare deux objets `CFileTime` pour déterminer le plus grand ou leur égalité.|

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[CFileTime::Day](#day)|Un membre de données statiques stockant le nombre d’intervalles de 100 nanosecondes qui composent un jour.|
|[CFileTime::Heure](#hour)|Un membre de données statiques stockant le nombre d’intervalles de 100 nanosecondes qui constituent une heure.|
|[CFileTime::Milliseconde](#millisecond)|Un membre de données statiques stockant le nombre d’intervalles de 100 nanosecondes qui constituent une milliseconde.|
|[CFileTime::Minute](#minute)|Un membre de données statiques stockant le nombre d’intervalles de 100 nanosecondes qui constituent une minute.|
|[CFileTime::Deuxième](#second)|Un membre de données statiques stockant le nombre d’intervalles de 100 nanosecondes qui constituent une seconde.|
|[CFileTime::Semaine](#week)|Un membre de données statiques stockant le nombre d’intervalles de 100 nanosecondes qui composent une semaine.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes pour gérer les valeurs de date et d’heure associées à la création, à l’accès et à la modification des fichiers. Les méthodes et les données de cette `CFileTimeSpan` classe sont fréquemment utilisées en conjonction avec des objets, qui traitent des valeurs de temps relatives.

La valeur de la date et de l’heure est stockée sous forme de valeur 64 bits représentant le nombre d’intervalles de 100 nanosecondes depuis le 1er janvier 1601. Il s’agit du format Coordinated Universal Time (UTC).

Les variables suivantes des membres de cône statique sont fournies pour simplifier les calculs :

|Variable membre|Nombre d’intervalles de 100 nanosecondes|
|---------------------|-----------------------------------------|
|Milliseconde|10 000|
|Seconde|Milliseconde \* 1 000|
|Minute|Deuxième \* 60|
|Heure|Minute \* 60|
|jour|Heure \* 24|
|Week|Jour \* 7|

**Note** Tous les systèmes de fichiers ne peuvent pas enregistrer la création et le dernier temps d’accès et tous les systèmes de fichiers ne les enregistrent pas de la même manière. Par exemple, sur le système de fichiers Windows NT FAT, créer du temps a une résolution de 10 millisecondes, écrire le temps a une résolution de 2 secondes, et le temps d’accès a une résolution de 1 jour (la date d’accès). Sur NTFS, le temps d’accès a une résolution d’une heure. En outre, FAT enregistre les temps sur disque dans l’heure locale, mais NTFS enregistre les temps sur le disque dans UTC. Pour plus d’informations, voir [File Times](/windows/win32/SysInfo/file-times).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`FILETIME`

`CFileTime`

## <a name="requirements"></a>Spécifications

**En-tête:** atltime.h

## <a name="cfiletimecfiletime"></a><a name="cfiletime"></a>CFileTime::CFileTime

Constructeur.

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Paramètres

*Ft*<br/>
Une structure [FILETIME.](/windows/win32/api/minwinbase/ns-minwinbase-filetime)

*n Temps*<br/>
La date et l’heure exprimées comme une valeur 64 bits.

### <a name="remarks"></a>Notes

L’objet `CFileTime` peut être créé à l’aide d’une date et d’une heure existantes à partir d’une `FILETIME` structure, ou exprimé comme une valeur 64 bits (dans les formats de temps universels locaux ou coordonnés (UTC). Le constructeur par défaut fixe le temps à 0.

## <a name="cfiletimeday"></a><a name="day"></a>CFileTime::Day

Un membre de données statiques stockant le nombre d’intervalles de 100 nanosecondes qui composent un jour.

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>Exemple

Voir l’exemple pour [CFileTime:Milliseconde](#millisecond).

## <a name="cfiletimegetcurrenttime"></a><a name="getcurrenttime"></a>CFileTime::GetCurrentTime

Appelez cette fonction statique `CFileTime` pour récupérer un objet qui représente la date et l’heure du système actuel.

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>Valeur de retour

Renvoie la date et l’heure actuelles du système dans le format Temps universel coordonné (UTC).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

## <a name="cfiletimegettime"></a><a name="gettime"></a>CFileTime::GetTime

Appelez cette méthode pour récupérer `CFileTime` l’heure de l’objet.

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la date et l’heure en tant que numéro 64 bits, qui peut être dans le format local ou coordonné de temps universel (UTC).

## <a name="cfiletimehour"></a><a name="hour"></a>CFileTime::Heure

Un membre de données statiques stockant le nombre d’intervalles de 100 nanosecondes qui constituent une heure.

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>Exemple

Voir l’exemple pour [CFileTime:Milliseconde](#millisecond).

## <a name="cfiletimelocaltoutc"></a><a name="localtoutc"></a>CFileTime::LocalToUTC

Appelez cette méthode pour convertir un temps de fichier local en un temps de fichier basé sur le temps universel coordonné (UTC).

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne `CFileTime` un objet contenant l’heure en format UTC.

### <a name="example"></a>Exemple

Voir l’exemple pour [CFileTime:UTCToLocal](#utctolocal).

## <a name="cfiletimemillisecond"></a><a name="millisecond"></a>CFileTime::Milliseconde

Un membre de données statiques stockant le nombre d’intervalles de 100 nanosecondes qui constituent une milliseconde.

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

## <a name="cfiletimeminute"></a><a name="minute"></a>CFileTime::Minute

Un membre de données statiques stockant le nombre d’intervalles de 100 nanosecondes qui constituent une minute.

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>Exemple

Voir l’exemple pour [CFileTime:Milliseconde](#millisecond).

## <a name="cfiletimeoperator--"></a><a name="operator_-"></a>CFileTime::opérateur -

Cet opérateur est utilisé pour effectuer `CFileTime` `CFileTimeSpan` la soustraction sur un ou un objet.

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*Span*<br/>
Objet `CFileTimeSpan` .

*Ft*<br/>
Objet `CFileTime` .

### <a name="return-value"></a>Valeur de retour

Renvoie `CFileTime` un `CFileTimeSpan` objet ou un objet représentant le résultat du décalage horaire entre les deux objets.

## <a name="cfiletimeoperator-"></a><a name="operator_neq"></a>CFileTime::opérateur !

Cet opérateur compare `CFileTime` deux objets à l’inégalité.

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*Ft*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’élément comparé `CFileTime` n’est pas égal à l’objet, sinon FALSE.

## <a name="cfiletimeoperator-"></a><a name="operator_add"></a>CFileTime::opérateur

Cet opérateur permet d'effectuer une addition sur un objet `CFileTimeSpan`.

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*Span*<br/>
Objet `CFileTimeSpan` .

### <a name="return-value"></a>Valeur de retour

Renvoie `CFileTime` un objet représentant le résultat du temps d’origine plus un temps relatif.

## <a name="cfiletimeoperator-"></a><a name="operator_add_eq"></a>CFileTime::opérateur

Cet opérateur permet d'effectuer une addition sur un objet `CFileTimeSpan` et d'assigner le résultat à l'objet actuel.

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*Span*<br/>
Objet `CFileTimeSpan` .

### <a name="return-value"></a>Valeur de retour

Retourne l’objet mis à jour, `CFileTime` représentant le résultat de l’heure d’origine plus un temps relatif.

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt"></a>CFileTime::opérateur&lt;

Cet opérateur compare deux objets `CFileTime` pour déterminer le plus petit.

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*Ft*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le premier objet est moins (plus tôt dans le temps) que le second, FALSE autrement.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt_eq"></a>CFileTime::opérateur&lt;=

Cet opérateur compare deux objets `CFileTime` pour déterminer le plus petit ou leur égalité.

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*Ft*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le premier objet est inférieur à (plus tôt dans le temps) ou égal au second, sinon FALSE.

## <a name="cfiletimeoperator-"></a><a name="operator_eq"></a>CFileTime::opérateur

L’opérateur de l’affectation.

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>Paramètres

*Ft*<br/>
Un `CFileTime` objet contenant la nouvelle heure et la date.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet mis à jour. `CFileTime`

## <a name="cfiletimeoperator--"></a><a name="operator_-_eq"></a>CFileTime::opérateur -MD

Cet opérateur est utilisé pour effectuer `CFileTimeSpan` la soustraction sur un objet et attribuer le résultat à l’objet actuel.

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*Span*<br/>
Un `CFileTimeSpan` objet contenant le temps relatif pour soustraire.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet mis à jour. `CFileTime`

## <a name="cfiletimeoperator-"></a><a name="operator_eq_eq"></a>CFileTime::opérateur

Cet opérateur compare deux objets `CFileTime` pour déterminer leur égalité.

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*Ft*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si les objets sont égaux, sinon FALSE.

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt"></a>CFileTime::opérateur&gt;

Cet opérateur compare deux objets `CFileTime` pour déterminer le plus grand.

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*Ft*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le premier objet est plus grand que (plus tard dans le temps) que le second, sinon FALSE.

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt_eq"></a>CFileTime::opérateur&gt;=

Cet opérateur compare deux objets `CFileTime` pour déterminer le plus grand ou leur égalité.

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*Ft*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le premier objet est plus grand que (plus tard dans le temps) ou égal au second, sinon FALSE.

## <a name="cfiletimesecond"></a><a name="second"></a>CFileTime::Deuxième

Un membre de données statiques stockant le nombre d’intervalles de 100 nanosecondes qui composent un jour.

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>Exemple

Voir l’exemple pour [CFileTime:Milliseconde](#millisecond).

## <a name="cfiletimesettime"></a><a name="settime"></a>CFileTime::SetTime

Appelez cette méthode pour définir la `CFileTime` date et l’heure stockées par l’objet.

```cpp
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Paramètres

*n Temps*<br/>
La valeur 64 bits représentant la date et l’heure, en format temps universel local ou coordonné (UTC).

## <a name="cfiletimeutctolocal"></a><a name="utctolocal"></a>CFileTime::UTCToLocal

Appelez cette méthode pour convertir le temps basé sur le temps universel coordonné (UTC) en temps de fichier local.

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne `CFileTime` un objet contenant l’heure dans le format de temps de fichier local.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

## <a name="cfiletimeweek"></a><a name="week"></a>CFileTime::Semaine

Un membre de données statiques stockant le nombre d’intervalles de 100 nanosecondes qui composent une semaine.

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>Exemple

Voir l’exemple pour [CFileTime:Milliseconde](#millisecond).

## <a name="see-also"></a>Voir aussi

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[Classe CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
