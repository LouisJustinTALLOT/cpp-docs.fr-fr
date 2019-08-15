---
title: CFileTime, classe
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
ms.openlocfilehash: b24d1e4d3e670a820c41735617b7db6780ff137c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491484"
---
# <a name="cfiletime-class"></a>CFileTime, classe

Cette classe fournit des méthodes pour gérer les valeurs de date et d’heure associées à un fichier.

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
|[CFileTime::GetCurrentTime](#getcurrenttime)|Appelez cette fonction statique pour récupérer un `CFileTime` objet qui représente la date et l’heure système actuelles.|
|[CFileTime::GetTime](#gettime)|Appelez cette méthode pour récupérer l’heure de l' `CFileTime` objet.|
|[CFileTime::LocalToUTC](#localtoutc)|Appelez cette méthode pour convertir une heure de fichier local en heure de fichier en fonction du temps universel coordonné (UTC).|
|[CFileTime::SetTime](#settime)|Appelez cette méthode pour définir la date et l’heure stockées par `CFileTime` l’objet.|
|[CFileTime::UTCToLocal](#utctolocal)|Appelez cette méthode pour convertir l’heure en fonction du temps universel coordonné (UTC, Universal Time Coordinated) en heure locale du fichier.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CFileTime:: Operator-](#operator_-)|Cet opérateur est utilisé pour effectuer une soustraction sur `CFileTime` un `CFileTimeSpan` objet ou.|
|[CFileTime:: Operator! =](#operator_neq)|Cet opérateur compare l' `CFileTime` inégalité de deux objets.|
|[CFileTime:: Operator +](#operator_add)|Cet opérateur permet d'effectuer une addition sur un objet `CFileTimeSpan`.|
|[CFileTime::operator +=](#operator_add_eq)|Cet opérateur permet d'effectuer une addition sur un objet `CFileTimeSpan` et d'assigner le résultat à l'objet actuel.|
|[CFileTime::, opérateur&lt;](#operator_lt)|Cet opérateur compare deux objets `CFileTime` pour déterminer le plus petit.|
|[CFileTime::, opérateur&lt;=](#operator_lt_eq)|Cet opérateur compare deux objets `CFileTime` pour déterminer le plus petit ou leur égalité.|
|[CFileTime:: Operator =](#operator_eq)|Opérateur d’assignation.|
|[CFileTime::operator -=](#operator_-_eq)|Cet opérateur est utilisé pour effectuer une soustraction sur `CFileTimeSpan` un objet et assigner le résultat à l’objet actuel.|
|[CFileTime::operator ==](#operator_eq_eq)|Cet opérateur compare deux objets `CFileTime` pour déterminer leur égalité.|
|[CFileTime::, opérateur&gt;](#operator_gt)|Cet opérateur compare deux objets `CFileTime` pour déterminer le plus grand.|
|[CFileTime::, opérateur&gt;=](#operator_gt_eq)|Cet opérateur compare deux objets `CFileTime` pour déterminer le plus grand ou leur égalité.|

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[CFileTime::Day](#day)|Un membre de données statique stockant le nombre d’intervalles de 100 nanosecondes qui composent un jour.|
|[CFileTime::Hour](#hour)|Un membre de données statique stockant le nombre d’intervalles de 100 nanosecondes qui composent une heure.|
|[CFileTime::Millisecond](#millisecond)|Un membre de données statique stockant le nombre d’intervalles de 100 nanosecondes qui composent une milliseconde.|
|[CFileTime::Minute](#minute)|Un membre de données statique stockant le nombre d’intervalles de 100 nanosecondes qui composent une minute.|
|[CFileTime::Second](#second)|Un membre de données statique stockant le nombre d’intervalles de 100 nanosecondes qui composent une seconde.|
|[CFileTime:: semaine](#week)|Un membre de données statique stockant le nombre d’intervalles de 100 nanosecondes qui composent une semaine.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes pour gérer les valeurs de date et d’heure associées à la création, l’accès et la modification de fichiers. Les méthodes et les données de cette classe sont fréquemment utilisées conjointement avec `CFileTimeSpan` les objets, qui gèrent les valeurs d’heure relatives.

La valeur de date et d’heure est stockée sous la forme d’une valeur 64 bits représentant le nombre d’intervalles de 100 nanosecondes depuis le 1er janvier 1601. Il s’agit du format de temps universel coordonné (UTC, Coordinated Universal Time).

Les variables de membre const statiques suivantes sont fournies pour simplifier les calculs:

|Variable membre|Nombre d’intervalles de 100 nanosecondes|
|---------------------|-----------------------------------------|
|Milliseconde|10 000|
|Seconde|Milliseconde \* 1 000|
|Minute|Deuxième \* 60|
|Heure|Minute \* 60|
|jour|Heure \* 24|
|Semaine|Jour \* 7|

**Remarque** Tous les systèmes de fichiers ne peuvent pas enregistrer le temps de création et de dernier accès et tous les systèmes de fichiers ne les enregistrent pas de la même manière. Par exemple, sur le système de fichiers FAT Windows NT, l’heure de création a une résolution de 10 millisecondes, le temps d’écriture a une résolution de 2 secondes et le temps d’accès a une résolution de 1 jour (la date d’accès). Sur NTFS, le temps d’accès a une résolution de 1 heure. En outre, le système de fichiers FAT enregistre les temps sur le disque en heure locale, mais il enregistre les temps sur le disque au format UTC. Pour plus d’informations, consultez [temps de fichier](/windows/win32/SysInfo/file-times).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`FILETIME`

`CFileTime`

## <a name="requirements"></a>Configuration requise

**En-tête:** atltime. h

##  <a name="cfiletime"></a>  CFileTime::CFileTime

Constructeur.

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Paramètres

*ft*<br/>
Structure [fileTime](/windows/win32/api/minwinbase/ns-minwinbase-filetime) .

*nTime*<br/>
Date et heure exprimées sous la forme d’une valeur de 64 bits.

### <a name="remarks"></a>Notes

L' `CFileTime` objet peut être créé à l’aide d’une date et d' `FILETIME` une heure existantes à partir d’une structure, ou exprimé sous la forme d’une valeur 64 bits (dans des formats de temps UTC (Universal Time Coordinated) ou locaux. Le constructeur par défaut affecte la valeur 0 à l’heure.

##  <a name="day"></a>  CFileTime::Day

Un membre de données statique stockant le nombre d’intervalles de 100 nanosecondes qui composent un jour.

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>Exemple

Consultez l’exemple pour [CFileTime:: Millisecond](#millisecond).

##  <a name="getcurrenttime"></a>  CFileTime::GetCurrentTime

Appelez cette fonction statique pour récupérer un `CFileTime` objet qui représente la date et l’heure système actuelles.

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la date et l’heure système actuelles au format de temps universel coordonné (UTC, Universal Time Coordinated).

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

##  <a name="gettime"></a>  CFileTime::GetTime

Appelez cette méthode pour récupérer l’heure de l' `CFileTime` objet.

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la date et l’heure sous la forme d’un nombre de 64 bits, qui peut être au format local ou UTC (Universal Time Coordinated).

##  <a name="hour"></a>  CFileTime::Hour

Un membre de données statique stockant le nombre d’intervalles de 100 nanosecondes qui composent une heure.

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>Exemple

Consultez l’exemple pour [CFileTime:: Millisecond](#millisecond).

##  <a name="localtoutc"></a>  CFileTime::LocalToUTC

Appelez cette méthode pour convertir une heure de fichier local en heure de fichier en fonction du temps universel coordonné (UTC).

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un `CFileTime` objet contenant l’heure au format UTC.

### <a name="example"></a>Exemple

Consultez l’exemple de [CFileTime:: UTCToLocal](#utctolocal).

##  <a name="millisecond"></a>  CFileTime::Millisecond

Un membre de données statique stockant le nombre d’intervalles de 100 nanosecondes qui composent une milliseconde.

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

##  <a name="minute"></a>  CFileTime::Minute

Un membre de données statique stockant le nombre d’intervalles de 100 nanosecondes qui composent une minute.

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>Exemples

Consultez l’exemple pour [CFileTime:: Millisecond](#millisecond).

##  <a name="operator_-"></a>  CFileTime::operator -

Cet opérateur est utilisé pour effectuer une soustraction sur `CFileTime` un `CFileTimeSpan` objet ou.

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan`.

*ft*<br/>
Objet `CFileTime`.

### <a name="return-value"></a>Valeur de retour

Retourne un `CFileTime` objet ou un `CFileTimeSpan` objet représentant le résultat de la différence de temps entre les deux objets.

##  <a name="operator_neq"></a>CFileTime:: Operator! =

Cet opérateur compare l' `CFileTime` inégalité de deux objets.

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*ft*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si l’élément en cours de comparaison n' `CFileTime` est pas égal à l’objet; sinon, false.

##  <a name="operator_add"></a>  CFileTime::operator +

Cet opérateur permet d'effectuer une addition sur un objet `CFileTimeSpan`.

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne un `CFileTime` objet représentant le résultat de l’heure d’origine plus une heure relative.

##  <a name="operator_add_eq"></a>  CFileTime::operator +=

Cet opérateur permet d'effectuer une addition sur un objet `CFileTimeSpan` et d'assigner le résultat à l'objet actuel.

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet `CFileTime` mis à jour représentant le résultat de l’heure d’origine plus une heure relative.

##  <a name="operator_lt"></a>  CFileTime::operator &lt;

Cet opérateur compare deux objets `CFileTime` pour déterminer le plus petit.

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*ft*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est inférieur (antérieur dans le temps) à la seconde, FALSe dans le cas contraire.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

##  <a name="operator_lt_eq"></a>CFileTime::, opérateur&lt;=

Cet opérateur compare deux objets `CFileTime` pour déterminer le plus petit ou leur égalité.

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*ft*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est inférieur à (antérieur dans le temps) ou égal au second, sinon FALSe.

##  <a name="operator_eq"></a>  CFileTime::operator =

Opérateur d’assignation.

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>Paramètres

*ft*<br/>
`CFileTime` Objet contenant la nouvelle date et l’heure.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet `CFileTime` mis à jour.

##  <a name="operator_-_eq"></a>  CFileTime::operator -=

Cet opérateur est utilisé pour effectuer une soustraction sur `CFileTimeSpan` un objet et assigner le résultat à l’objet actuel.

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
`CFileTimeSpan` Objet contenant le temps relatif à soustraire.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet `CFileTime` mis à jour.

##  <a name="operator_eq_eq"></a>  CFileTime::operator ==

Cet opérateur compare deux objets `CFileTime` pour déterminer leur égalité.

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*ft*<br/>
`CFileTime` Objet à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les objets sont égaux, sinon FALSe.

##  <a name="operator_gt"></a>  CFileTime::operator &gt;

Cet opérateur compare deux objets `CFileTime` pour déterminer le plus grand.

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*ft*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est supérieur à (plus tard dans le temps) que le second, sinon FALSe.

##  <a name="operator_gt_eq"></a>CFileTime::, opérateur&gt;=

Cet opérateur compare deux objets `CFileTime` pour déterminer le plus grand ou leur égalité.

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*ft*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est supérieur à (plus tard dans le temps) ou égal au second, sinon FALSe.

##  <a name="second"></a>  CFileTime::Second

Un membre de données statique stockant le nombre d’intervalles de 100 nanosecondes qui composent un jour.

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>Exemple

Consultez l’exemple pour [CFileTime:: Millisecond](#millisecond).

##  <a name="settime"></a>  CFileTime::SetTime

Appelez cette méthode pour définir la date et l’heure stockées par `CFileTime` l’objet.

```
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Paramètres

*nTime*<br/>
Valeur 64 bits représentant la date et l’heure, au format local ou UTC (Coordinated Universal Time).

##  <a name="utctolocal"></a>  CFileTime::UTCToLocal

Appelez cette méthode pour convertir l’heure en fonction du temps universel coordonné (UTC, Universal Time Coordinated) en heure locale du fichier.

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un `CFileTime` objet contenant l’heure au format d’heure de fichier local.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

##  <a name="week"></a>  CFileTime::Week

Un membre de données statique stockant le nombre d’intervalles de 100 nanosecondes qui composent une semaine.

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>Exemple

Consultez l’exemple pour [CFileTime:: Millisecond](#millisecond).

## <a name="see-also"></a>Voir aussi

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTimeSpan, classe](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
