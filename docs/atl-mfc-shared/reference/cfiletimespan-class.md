---
title: CFileTimeSpan, classe
ms.date: 10/18/2018
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
ms.openlocfilehash: f9bb42ba4c142f671a83dcfa7e99cff940fff047
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491292"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan, classe

Cette classe fournit des méthodes pour gérer les valeurs de date et d’heure relatives associées à un fichier.

## <a name="syntax"></a>Syntaxe

```
class CFileTimeSpan
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFileTimeSpan:: GetTimeSpan](#gettimespan)|Appelez cette méthode pour récupérer l’intervalle de temps à `CFileTimeSpan` partir de l’objet.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Appelez cette méthode pour définir l’intervalle de temps de `CFileTimeSpan` l’objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CFileTimeSpan::operator -](#operator_-)|Effectue une soustraction sur `CFileTimeSpan` un objet.|
|[CFileTimeSpan::operator !=](#operator_neq)|Compare deux objets `CFileTimeSpan` pour déterminer s'ils sont différents.|
|[CFileTimeSpan:: Operator +](#operator_add)|Effectue l’ajout sur `CFileTimeSpan` un objet.|
|[CFileTimeSpan::operator +=](#operator_add_eq)|Effectue l’ajout sur `CFileTimeSpan` un objet et assigne le résultat à l’objet actuel.|
|[CFileTimeSpan::, opérateur&lt;](#operator_lt)|Compare deux `CFileTimeSpan` objets pour déterminer le plus petit.|
|[CFileTimeSpan::, opérateur&lt;=](#operator_lt_eq)|Compare deux `CFileTimeSpan` objets pour déterminer l’égalité ou le plus petit.|
|[CFileTimeSpan::operator =](#operator_eq)|Opérateur d’assignation.|
|[CFileTimeSpan::operator -=](#operator_-_eq)|Effectue une soustraction sur `CFileTimeSpan` un objet et assigne le résultat à l’objet actuel.|
|[CFileTimeSpan::operator ==](#operator_eq_eq)|Compare deux objets `CFileTimeSpan` pour déterminer s’ils sont égaux.|
|[CFileTimeSpan::, opérateur&gt;](#operator_gt)|Compare deux `CFileTimeSpan` objets pour déterminer le plus grand.|
|[CFileTimeSpan::, opérateur&gt;=](#operator_gt_eq)|Compare deux `CFileTimeSpan` objets pour déterminer l’égalité ou le plus grand.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes pour la gestion des périodes relatives au moment où des opérations sont exécutées lors de l’exécution d’opérations concernant le moment de la création, du dernier accès ou de la dernière modification d’un fichier. Les méthodes de cette classe sont fréquemment utilisées conjointement aux objets de la [classe CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md) .

## <a name="example"></a>Exemple

Consultez l’exemple pour [CFileTime:: Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Configuration requise

**En-tête:** atltime. h

##  <a name="cfiletimespan"></a>  CFileTimeSpan::CFileTimeSpan

Constructeur.

```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan` existant.

*nSpan*<br/>
Durée en millisecondes.

### <a name="remarks"></a>Notes

L' `CFileTimeSpan` objet peut être créé à l’aide `CFileTimeSpan` d’un objet existant ou exprimé sous la forme d’une valeur 64 bits. Le constructeur par défaut affecte la valeur 0 à l’intervalle de temps.

##  <a name="gettimespan"></a>  CFileTimeSpan::GetTimeSpan

Appelez cette méthode pour récupérer l’intervalle de temps à `CFileTimeSpan` partir de l’objet.

```
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’intervalle de temps en millisecondes.

##  <a name="operator_-"></a>  CFileTimeSpan::operator -

Effectue une soustraction sur `CFileTimeSpan` un objet.

```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne un `CFileTimeSpan` objet représentant le résultat de la différence entre deux intervalles de temps.

##  <a name="operator_neq"></a>  CFileTimeSpan::operator !=

Compare deux objets `CFileTimeSpan` pour déterminer s'ils sont différents.

```
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si l’élément en cours de comparaison n' `CFileTimeSpan` est pas égal à l’objet; sinon, false.

##  <a name="operator_add"></a>  CFileTimeSpan::operator +

Effectue l’ajout sur `CFileTimeSpan` un objet.

```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne un `CFileTimeSpan` objet contenant la somme des deux intervalles de temps.

##  <a name="operator_add_eq"></a>  CFileTimeSpan::operator +=

Effectue l’ajout sur `CFileTimeSpan` un objet et assigne le résultat à l’objet actuel.

```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet `CFileTimeSpan` mis à jour qui contient la somme des deux intervalles de temps.

##  <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;

Compare deux `CFileTimeSpan` objets pour déterminer le plus petit.

```
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est inférieur (c’est-à-dire, représente une période plus petite) que le second, sinon FALSe.

##  <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=

Compare deux `CFileTimeSpan` objets pour déterminer l’égalité ou le plus petit.

```
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est inférieur à (autrement dit, représente une période de temps plus petite) ou s’il est égal au second, sinon FALSe.

##  <a name="operator_eq"></a>  CFileTimeSpan::operator =

Opérateur d’assignation.

```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet `CFileTimeSpan` mis à jour.

##  <a name="operator_-_eq"></a>  CFileTimeSpan::operator -=

Effectue une soustraction sur `CFileTimeSpan` un objet et assigne le résultat à l’objet actuel.

```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet `CFileTimeSpan` mis à jour.

##  <a name="operator_eq_eq"></a>  CFileTimeSpan::operator ==

Compare deux objets `CFileTimeSpan` pour déterminer s’ils sont égaux.

```
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les objets sont égaux, sinon FALSe.

##  <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;

Compare deux `CFileTimeSpan` objets pour déterminer le plus grand.

```
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est supérieur à (ce qui représente une période plus longue) que le deuxième, sinon FALSe.

##  <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=

Compare deux `CFileTimeSpan` objets pour déterminer l’égalité ou le plus grand.

```
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*span*<br/>
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est supérieur à (c’est-à-dire qu’il s’agit d’un délai plus long) ou s’il est égal au second, sinon FALSe.

##  <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan

Appelez cette méthode pour définir l’intervalle de temps de `CFileTimeSpan` l’objet.

```
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Paramètres

*nSpan*<br/>
Nouvelle valeur de l’intervalle de temps, en millisecondes.

## <a name="see-also"></a>Voir aussi

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTime, classe](../../atl-mfc-shared/reference/cfiletime-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
