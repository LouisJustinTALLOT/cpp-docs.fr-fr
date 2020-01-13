---
title: CFileTimeSpan, classe
description: La classe CFileTimeSpan (ATL) et Microsoft Foundation Classes (MFC) gère Active Template Library les intervalles de temps dans les unités FILETIME.
ms.date: 01/10/2020
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
ms.openlocfilehash: 89d95759b11ff7e52c2a8fa75cf94f7b7b81fa36
ms.sourcegitcommit: c3283062ce4e382aec7f11626d358a37caf8cdbb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75914378"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan, classe

Cette classe fournit des méthodes pour gérer les valeurs de date et d’heure relatives associées à un fichier.

## <a name="syntax"></a>Syntaxe

```cpp
class CFileTimeSpan
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|Constructeur.|

### <a name="public-methods"></a>Méthodes publiques

|Name|Description|
|----------|-----------------|
|[CFileTimeSpan :: GetTimeSpan](#gettimespan)|Appelez cette méthode pour récupérer l’intervalle de temps à partir de l’objet `CFileTimeSpan`.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Appelez cette méthode pour définir l’intervalle de temps de l’objet `CFileTimeSpan`.|

### <a name="public-operators"></a>Opérateurs publics

|Name|Description|
|----------|-----------------|
|[CFileTimeSpan::operator -](#operator_-)|Effectue une soustraction sur un objet `CFileTimeSpan`.|
|[CFileTimeSpan::operator !=](#operator_neq)|Compare deux objets `CFileTimeSpan` pour déterminer s'ils sont différents.|
|[CFileTimeSpan :: Operator +](#operator_add)|Effectue l’ajout sur un objet `CFileTimeSpan`.|
|[CFileTimeSpan::operator +=](#operator_add_eq)|Effectue une addition sur un objet `CFileTimeSpan` et assigne le résultat à l’objet actuel.|
|[CFileTimeSpan :: Operator &lt;](#operator_lt)|Compare deux objets `CFileTimeSpan` pour déterminer le plus petit.|
|[CFileTimeSpan :: Operator &lt;=](#operator_lt_eq)|Compare deux objets `CFileTimeSpan` pour déterminer l’égalité ou le plus petit.|
|[CFileTimeSpan::operator =](#operator_eq)|Opérateur d’assignation.|
|[CFileTimeSpan::operator -=](#operator_-_eq)|Effectue une soustraction sur un objet `CFileTimeSpan` et assigne le résultat à l’objet actuel.|
|[CFileTimeSpan::operator ==](#operator_eq_eq)|Compare deux objets `CFileTimeSpan` pour déterminer s’ils sont égaux.|
|[CFileTimeSpan :: Operator &gt;](#operator_gt)|Compare deux objets `CFileTimeSpan` pour déterminer le plus grand.|
|[CFileTimeSpan :: Operator &gt;=](#operator_gt_eq)|Compare deux objets `CFileTimeSpan` pour déterminer l’égalité ou le plus grand.|

## <a name="remarks"></a>Notes

La classe `CFileTimeSpan` fournit des méthodes pour gérer les périodes relatives de temps dans les unités utilisées par le système de fichiers. Ces unités sont souvent utilisées dans les opérations de fichier, par exemple lors de la création d’un fichier, du dernier accès ou de la dernière modification. Les méthodes de cette classe sont fréquemment utilisées conjointement aux objets de la [classe CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md) .

## <a name="example"></a>Exemple

Consultez l’exemple pour [CFileTime :: Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Configuration requise pour

**En-tête :** atltime. h

## <a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

Constructeur.

```cpp
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parameters

*span*\
Objet `CFileTimeSpan` existant.

*nSpan*\
Durée en unités FILETIME.

### <a name="remarks"></a>Notes

L’objet `CFileTimeSpan` peut être créé à l’aide d’un objet `CFileTimeSpan` existant, ou exprimé sous la forme d’une valeur 64 bits en unités FILETIME de 100 nanosecondes. Pour plus d’informations, consultez [CFileTime](cfiletime-class.md). Le constructeur par défaut affecte la valeur 0 à l’intervalle de temps.

## <a name="gettimespan"></a>CFileTimeSpan :: GetTimeSpan

Appelez cette méthode pour récupérer l’intervalle de temps à partir de l’objet `CFileTimeSpan`.

```cpp
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’intervalle de temps en unités FILETIME de 100 nanosecondes. Pour plus d’informations, consultez [CFileTime](cfiletime-class.md).

## <a name="operator_-"></a>  CFileTimeSpan::operator -

Effectue une soustraction sur un objet `CFileTimeSpan`.

```cpp
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

*span*\
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne un objet `CFileTimeSpan` représentant le résultat de la différence entre deux intervalles de temps.

## <a name="operator_neq"></a>  CFileTimeSpan::operator !=

Compare deux objets `CFileTimeSpan` pour déterminer s'ils sont différents.

```cpp
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

*span*\
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’élément en cours de comparaison n’est pas égal à l’objet `CFileTimeSpan` ; Sinon, FALSe.

## <a name="operator_add"></a>  CFileTimeSpan::operator +

Effectue l’ajout sur un objet `CFileTimeSpan`.

```cpp
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

*span*\
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne un objet `CFileTimeSpan` contenant la somme des deux intervalles de temps.

## <a name="operator_add_eq"></a>  CFileTimeSpan::operator +=

Effectue une addition sur un objet `CFileTimeSpan` et assigne le résultat à l’objet actuel.

```cpp
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parameters

*span*\
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet `CFileTimeSpan` mis à jour qui contient la somme des deux intervalles de temps.

## <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;

Compare deux objets `CFileTimeSpan` pour déterminer le plus petit.

```cpp
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

*span*\
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est inférieur (c’est-à-dire, représente une période plus petite) que le second, sinon FALSe.

## <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=

Compare deux objets `CFileTimeSpan` pour déterminer l’égalité ou le plus petit.

```cpp
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

*span*\
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est inférieur à (autrement dit, représente une période de temps plus petite) ou s’il est égal au second, sinon FALSe.

## <a name="operator_eq"></a>  CFileTimeSpan::operator =

Opérateur d’assignation.

```cpp
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Parameters

*span*\
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet `CFileTimeSpan` mis à jour.

## <a name="operator_-_eq"></a>  CFileTimeSpan::operator -=

Effectue une soustraction sur un objet `CFileTimeSpan` et assigne le résultat à l’objet actuel.

```cpp
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parameters

*span*\
Objet `CFileTimeSpan`.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet `CFileTimeSpan` mis à jour.

## <a name="operator_eq_eq"></a>  CFileTimeSpan::operator ==

Compare deux objets `CFileTimeSpan` pour déterminer s’ils sont égaux.

```cpp
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

*span*\
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les objets sont égaux, sinon FALSe.

## <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;

Compare deux objets `CFileTimeSpan` pour déterminer le plus grand.

```cpp
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

*span*\
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est supérieur à (ce qui représente une période plus longue) que le deuxième, sinon FALSe.

## <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=

Compare deux objets `CFileTimeSpan` pour déterminer l’égalité ou le plus grand.

```cpp
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameters

*span*\
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le premier objet est supérieur à (c’est-à-dire qu’il s’agit d’un délai plus long) ou s’il est égal au second, sinon FALSe.

## <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan

Appelez cette méthode pour définir l’intervalle de temps de l’objet `CFileTimeSpan`.

```cpp
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parameters

*nSpan*\
Nouvelle valeur pour l’intervalle de temps en unités FILETIME de 100 nanosecondes. Pour plus d’informations, consultez [CFileTime](cfiletime-class.md).

## <a name="see-also"></a>Voir aussi

\ [fileTime](/windows/win32/api/minwinbase/ns-minwinbase-filetime)
\ de la [classe CFileTime](cfiletime-class.md)
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)\
[Classes partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
