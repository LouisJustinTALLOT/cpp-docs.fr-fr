---
title: Cfiletime, classe | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CFileTime class
- shared classes, CFileTime
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36e71cd975ff138343770b80e60b0287faa32558
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808821"
---
# <a name="cfiletime-class"></a>Cfiletime, classe

Cette classe fournit des méthodes pour gérer les valeurs de date et heure associées à un fichier.

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
|[CFileTime::GetCurrentTime](#getcurrenttime)|Appelez cette fonction statique pour récupérer un `CFileTime` objet qui représente la date système actuelle et l’heure.|
|[CFileTime::GetTime](#gettime)|Appelez cette méthode pour récupérer l’heure à partir de la `CFileTime` objet.|
|[CFileTime::LocalToUTC](#localtoutc)|Appelez cette méthode pour convertir une heure de fichier local en une heure de fichier basée sur le temps universel coordonné (UTC).|
|[CFileTime::SetTime](#settime)|Appelez cette méthode pour définir la date et l’heure stockées par le `CFileTime` objet.|
|[CFileTime::UTCToLocal](#utctolocal)|Appelez cette méthode pour convertir l’heure basée sur le temps universel coordonné (UTC), heure de fichier local.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CFileTime::operator-](#operator_-)|Cet opérateur est utilisé pour effectuer une soustraction sur un `CFileTime` ou `CFileTimeSpan` objet.|
|[CFileTime::operator ! =](#operator_neq)|Cet opérateur compare deux `CFileTime` objets sont inégaux.|
|[CFileTime::operator +](#operator_add)|Cet opérateur permet d'effectuer une addition sur un objet `CFileTimeSpan`.|
|[CFileTime::operator +=](#operator_add_eq)|Cet opérateur permet d'effectuer une addition sur un objet `CFileTimeSpan` et d'assigner le résultat à l'objet actuel.|
|[CFileTime::operator &lt;](#operator_lt)|Cet opérateur compare deux objets `CFileTime` pour déterminer le plus petit.|
|[CFileTime::operator &lt;=](#operator_lt_eq)|Cet opérateur compare deux objets `CFileTime` pour déterminer le plus petit ou leur égalité.|
|[CFileTime::operator =](#operator_eq)|L’opérateur d’assignation.|
|[CFileTime::operator =](#operator_-_eq)|Cet opérateur est utilisé pour effectuer une soustraction sur un `CFileTimeSpan` de l’objet et assigner le résultat à l’objet actuel.|
|[CFileTime::operator ==](#operator_eq_eq)|Cet opérateur compare deux objets `CFileTime` pour déterminer leur égalité.|
|[CFileTime::operator &gt;](#operator_gt)|Cet opérateur compare deux objets `CFileTime` pour déterminer le plus grand.|
|[CFileTime::operator &gt;=](#operator_gt_eq)|Cet opérateur compare deux objets `CFileTime` pour déterminer le plus grand ou leur égalité.|

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[CFileTime::Day](#day)|Une donnée membre static stocker le nombre d’intervalles de 100 nanosecondes qui composent un jour.|
|[CFileTime::Hour](#hour)|Une donnée membre static stocker le nombre d’intervalles de 100 nanosecondes qui composent une heure.|
|[CFileTime::Millisecond](#millisecond)|Une donnée membre static stocker le nombre d’intervalles de 100 nanosecondes qui composent une milliseconde.|
|[CFileTime::Minute](#minute)|Une donnée membre static stocker le nombre d’intervalles de 100 nanosecondes qui composent une minute.|
|[CFileTime::Second](#second)|Une donnée membre static stocker le nombre d’intervalles de 100 nanosecondes qui composent une seconde.|
|[CFileTime::Week](#week)|Une donnée membre static stocker le nombre d’intervalles de 100 nanosecondes qui composent une semaine.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes pour gérer les valeurs de date et heure associées à la création, l’accès et la modification des fichiers. Les méthodes et les données de cette classe sont fréquemment utilisées conjointement avec `CFileTimeSpan` les objets, gérer les valeurs de temps relatif.

La valeur de date et d’heure est stockée en tant qu’une valeur 64 bits représentant le nombre d’intervalles de 100 nanosecondes depuis le 1er janvier 1601. Il s’agit du format de temps universel coordonné (UTC).

Les variables membres constantes static suivantes sont fournies pour simplifier les calculs :

|Variable de membre|Nombre d’intervalles de 100 nanosecondes.|
|---------------------|-----------------------------------------|
|Milliseconde|10,000|
|Seconde|Milliseconde \* 1 000|
|Minute|Deuxième \* 60|
|Heure|Minute \* 60|
|Jour|Heure \* 24|
|Semaine|Jour \* 7|

**Remarque** pas tous les systèmes de fichiers peuvent enregistrer la création et heure du dernier accès et pas tous les systèmes de fichiers les enregistrent dans la même manière. Par exemple, sur le système de fichiers FAT Windows NT, créez heure a une résolution de 10 millisecondes, temps d’écriture a une résolution de 2 secondes et temps d’accès présente une résolution de 1 jour (date d’accès). Sur NTFS, temps d’accès présente une résolution de 1 heure. En outre, FAT enregistre la fois sur le disque en heure locale, mais NTFS enregistre la fois sur le disque au format UTC. Pour plus d’informations, consultez [heures de fichier](/windows/desktop/SysInfo/file-times).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`FILETIME`

`CFileTime`

## <a name="requirements"></a>Configuration requise

**En-tête :** atltime.h

##  <a name="cfiletime"></a>  CFileTime::CFileTime

Constructeur.

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Paramètres

*FT*<br/>
Un [FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) structure.

*Nintervalle*<br/>
La date et l’heure exprimée sous la forme d’une valeur 64 bits.

### <a name="remarks"></a>Notes

Le `CFileTime` objet peut être créé à l’aide d’une date existante et l’heure à partir d’un `FILETIME` structure ou exprimé comme une valeur 64 bits (en local ou de formats d’heure de temps universel coordonné (UTC)). Le constructeur par défaut définit la durée sur 0.

##  <a name="day"></a>  CFileTime::Day

Une donnée membre static stocker le nombre d’intervalles de 100 nanosecondes qui composent un jour.

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>Exemple

Consultez l’exemple de [CFileTime::Millisecond](#millisecond).

##  <a name="getcurrenttime"></a>  CFileTime::GetCurrentTime

Appelez cette fonction statique pour récupérer un `CFileTime` objet qui représente la date système actuelle et l’heure.

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la date système actuelle et l’heure au format de temps universel coordonné (UTC).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

##  <a name="gettime"></a>  CFileTime::GetTime

Appelez cette méthode pour récupérer l’heure à partir de la `CFileTime` objet.

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la date et l’heure sous la forme un nombre 64 bits, qui peut être au format de temps universel coordonné (UTC) ou local.

##  <a name="hour"></a>  CFileTime::Hour

Une donnée membre static stocker le nombre d’intervalles de 100 nanosecondes qui composent une heure.

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>Exemple

Consultez l’exemple de [CFileTime::Millisecond](#millisecond).

##  <a name="localtoutc"></a>  CFileTime::LocalToUTC

Appelez cette méthode pour convertir une heure de fichier local en une heure de fichier basée sur le temps universel coordonné (UTC).

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un `CFileTime` objet contenant l’heure au format UTC.

### <a name="example"></a>Exemple

Consultez l’exemple de [CFileTime::UTCToLocal](#utctolocal).

##  <a name="millisecond"></a>  CFileTime::Millisecond

Une donnée membre static stocker le nombre d’intervalles de 100 nanosecondes qui composent une milliseconde.

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

##  <a name="minute"></a>  CFileTime::Minute

Une donnée membre static stocker le nombre d’intervalles de 100 nanosecondes qui composent une minute.

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>Exemple

Consultez l’exemple de [CFileTime::Millisecond](#millisecond).

##  <a name="operator_-"></a>  CFileTime::operator-

Cet opérateur est utilisé pour effectuer une soustraction sur un `CFileTime` ou `CFileTimeSpan` objet.

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan`.

*FT*<br/>
Objet `CFileTime`.

### <a name="return-value"></a>Valeur de retour

Retourne un `CFileTime` objet ou un `CFileTimeSpan` objet représentant le résultat de la différence de temps entre les deux objets.

##  <a name="operator_neq"></a>  CFileTime::operator ! =

Cet opérateur compare deux `CFileTime` objets sont inégaux.

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*FT*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’élément en cours de comparaison n’est pas égale à la `CFileTime` objet, sinon, FALSE.

##  <a name="operator_add"></a>  CFileTime::operator +

Cet opérateur permet d'effectuer une addition sur un objet `CFileTimeSpan`.

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne un `CFileTime` objet représentant le résultat de l’heure d’origine plus une heure relative.

##  <a name="operator_add_eq"></a>  CFileTime::operator +=

Cet opérateur permet d'effectuer une addition sur un objet `CFileTimeSpan` et d'assigner le résultat à l'objet actuel.

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne la mise à jour `CFileTime` objet représentant le résultat de l’heure d’origine plus une heure relative.

##  <a name="operator_lt"></a>  CFileTime::operator &lt;

Cet opérateur compare deux objets `CFileTime` pour déterminer le plus petit.

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*FT*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est inférieur (précédemment dans le temps) à la seconde, sinon FALSE.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

##  <a name="operator_lt_eq"></a>  CFileTime::operator &lt;=

Cet opérateur compare deux objets `CFileTime` pour déterminer le plus petit ou leur égalité.

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*FT*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est inférieur à (antérieur dans le temps) ou égal au second, sinon, FALSE.

##  <a name="operator_eq"></a>  CFileTime::operator =

L’opérateur d’assignation.

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>Paramètres

*FT*<br/>
Un `CFileTime` objet contenant la nouvelle heure et date.

### <a name="return-value"></a>Valeur de retour

Retourne la mise à jour `CFileTime` objet.

##  <a name="operator_-_eq"></a>  CFileTime::operator =

Cet opérateur est utilisé pour effectuer une soustraction sur un `CFileTimeSpan` de l’objet et assigner le résultat à l’objet actuel.

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Un `CFileTimeSpan` objet contenant l’heure relative à soustraire.

### <a name="return-value"></a>Valeur de retour

Retourne la mise à jour `CFileTime` objet.

##  <a name="operator_eq_eq"></a>  CFileTime::operator ==

Cet opérateur compare deux objets `CFileTime` pour déterminer leur égalité.

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*FT*<br/>
Le `CFileTime` objet à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les objets sont égaux ; sinon, FALSE.

##  <a name="operator_gt"></a>  CFileTime::operator &gt;

Cet opérateur compare deux objets `CFileTime` pour déterminer le plus grand.

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*FT*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est supérieur à (plus loin dans le temps) à la seconde, sinon, FALSE.

##  <a name="operator_gt_eq"></a>  CFileTime::operator &gt;=

Cet opérateur compare deux objets `CFileTime` pour déterminer le plus grand ou leur égalité.

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Paramètres

*FT*<br/>
Objet `CFileTime` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est supérieur (plus loin dans le temps) ou égal au second, sinon, FALSE.

##  <a name="second"></a>  CFileTime::Second

Une donnée membre static stocker le nombre d’intervalles de 100 nanosecondes qui composent un jour.

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>Exemple

Consultez l’exemple de [CFileTime::Millisecond](#millisecond).

##  <a name="settime"></a>  CFileTime::SetTime

Appelez cette méthode pour définir la date et l’heure stockées par le `CFileTime` objet.

```
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Paramètres

*Nintervalle*<br/>
La valeur de 64 bits qui représente la date et l’heure, au format de temps universel coordonné (UTC) ou local.

##  <a name="utctolocal"></a>  CFileTime::UTCToLocal

Appelez cette méthode pour convertir l’heure basée sur le temps universel coordonné (UTC), heure de fichier local.

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un `CFileTime` objet contenant l’heure au format d’heure de fichier local.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

##  <a name="week"></a>  CFileTime::Week

Une donnée membre static stocker le nombre d’intervalles de 100 nanosecondes qui composent une semaine.

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>Exemple

Consultez l’exemple de [CFileTime::Millisecond](#millisecond).

## <a name="see-also"></a>Voir aussi

[FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284)<br/>
[CFileTimeSpan, classe](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
