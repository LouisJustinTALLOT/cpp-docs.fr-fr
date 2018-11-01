---
title: Cfiletimespan, classe
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
ms.openlocfilehash: dc59a300fc48f180fb593500ed85ee1a4c34c07e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468924"
---
# <a name="cfiletimespan-class"></a>Cfiletimespan, classe

Cette classe fournit des méthodes pour la gestion relatif valeurs de date et heure associées à un fichier.

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
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Appelez cette méthode pour récupérer l’intervalle de temps à partir de la `CFileTimeSpan` objet.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Appelez cette méthode pour définir l’intervalle de temps du `CFileTimeSpan` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CFileTimeSpan::operator-](#operator_-)|Effectue une soustraction sur un `CFileTimeSpan` objet.|
|[CFileTimeSpan::operator ! =](#operator_neq)|Compare deux objets `CFileTimeSpan` pour déterminer s'ils sont différents.|
|[CFileTimeSpan::operator +](#operator_add)|Effectue l’addition sur un `CFileTimeSpan` objet.|
|[CFileTimeSpan::operator +=](#operator_add_eq)|Effectue l’addition sur un `CFileTimeSpan` de l’objet et assigner le résultat à l’objet actuel.|
|[CFileTimeSpan::operator &lt;](#operator_lt)|Compare deux `CFileTimeSpan` objets pour déterminer le plus petit.|
|[CFileTimeSpan::operator &lt;=](#operator_lt_eq)|Compare deux `CFileTimeSpan` objets pour déterminer l’égalité ou le plus petit.|
|[CFileTimeSpan::operator =](#operator_eq)|L’opérateur d’assignation.|
|[CFileTimeSpan::operator =](#operator_-_eq)|Effectue une soustraction sur un `CFileTimeSpan` de l’objet et assigner le résultat à l’objet actuel.|
|[CFileTimeSpan::operator ==](#operator_eq_eq)|Compare deux objets `CFileTimeSpan` pour déterminer s’ils sont égaux.|
|[CFileTimeSpan::operator &gt;](#operator_gt)|Compare deux `CFileTimeSpan` objets pour déterminer le plus grand.|
|[CFileTimeSpan::operator &gt;=](#operator_gt_eq)|Compare deux `CFileTimeSpan` objets pour déterminer l’égalité ou la plus grande.|

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes pour la gestion des périodes relatives de temps plus souvent rencontrés lors des opérations quand un fichier a été créé, du dernier accès ou de dernière modification. Les méthodes de cette classe sont fréquemment utilisés conjointement avec [cfiletime, classe](../../atl-mfc-shared/reference/cfiletime-class.md) objets.

## <a name="example"></a>Exemple

Consultez l’exemple de [CFileTime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Configuration requise

**En-tête :** atltime.h

##  <a name="cfiletimespan"></a>  CFileTimeSpan::CFileTimeSpan

Constructeur.

```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan` existant.

*nSpan*<br/>
Une période de temps en millisecondes.

### <a name="remarks"></a>Notes

Le `CFileTimeSpan` objet peut être créé à l’aide d’un existant `CFileTimeSpan` de l’objet ou exprimé comme une valeur 64 bits. Le constructeur par défaut définit l’intervalle de temps à 0.

##  <a name="gettimespan"></a>  CFileTimeSpan::GetTimeSpan

Appelez cette méthode pour récupérer l’intervalle de temps à partir de la `CFileTimeSpan` objet.

```
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’intervalle de temps en millisecondes.

##  <a name="operator_-"></a>  CFileTimeSpan::operator-

Effectue une soustraction sur un `CFileTimeSpan` objet.

```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne un `CFileTimeSpan` objet représentant le résultat de la différence entre deux intervalles de temps.

##  <a name="operator_neq"></a>  CFileTimeSpan::operator ! =

Compare deux objets `CFileTimeSpan` pour déterminer s'ils sont différents.

```
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’élément en cours de comparaison n’est pas égale à la `CFileTimeSpan` objet ; sinon, FALSE.

##  <a name="operator_add"></a>  CFileTimeSpan::operator +

Effectue l’addition sur un `CFileTimeSpan` objet.

```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne un `CFileTimeSpan` contenant la somme de l’heure en deux étendues de l’objet.

##  <a name="operator_add_eq"></a>  CFileTimeSpan::operator +=

Effectue l’addition sur un `CFileTimeSpan` de l’objet et assigne le résultat à l’objet actuel.

```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne la mise à jour `CFileTimeSpan` contenant la somme de l’heure en deux étendues de l’objet.

##  <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;

Compare deux `CFileTimeSpan` objets pour déterminer le plus petit.

```
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est inférieur (autrement dit, représente une période de temps plus courte) au second, sinon, FALSE.

##  <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=

Compare deux `CFileTimeSpan` objets pour déterminer l’égalité ou le plus petit.

```
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE si le premier objet est inférieur à (autrement dit, représente une période de temps plus courte) ou égale à la seconde, sinon, FALSE.

##  <a name="operator_eq"></a>  CFileTimeSpan::operator =

L’opérateur d’assignation.

```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne la mise à jour `CFileTimeSpan` objet.

##  <a name="operator_-_eq"></a>  CFileTimeSpan::operator =

Effectue une soustraction sur un `CFileTimeSpan` de l’objet et assigne le résultat à l’objet actuel.

```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne la mise à jour `CFileTimeSpan` objet.

##  <a name="operator_eq_eq"></a>  CFileTimeSpan::operator ==

Compare deux objets `CFileTimeSpan` pour déterminer s’ils sont égaux.

```
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les objets sont égaux ; sinon, FALSE.

##  <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;

Compare deux `CFileTimeSpan` objets pour déterminer le plus grand.

```
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est supérieur à (autrement dit, représente une période plus longue) au second, sinon, FALSE.

##  <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=

Compare deux `CFileTimeSpan` objets pour déterminer l’égalité ou la plus grande.

```
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*étendue*<br/>
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est supérieur à (autrement dit, représente une période plus longue) ou égal au second, sinon, FALSE.

##  <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan

Appelez cette méthode pour définir l’intervalle de temps du `CFileTimeSpan` objet.

```
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Paramètres

*nSpan*<br/>
La nouvelle valeur pour l’intervalle de temps en millisecondes.

## <a name="see-also"></a>Voir aussi

[FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284)<br/>
[CFileTime, classe](../../atl-mfc-shared/reference/cfiletime-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
