---
title: CFileTimeSpan, classe
description: La classe Active Template Library (ATL) et Microsoft Foundation Classes (MFC) CFileTimeSpan gère les intervalles de temps dans les unités FILETIME.
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
ms.openlocfilehash: 87737ea1c778660a68510b484bcdfa3a4670e8ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317855"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan, classe

Ce cours fournit des méthodes pour gérer les valeurs relatives de date et d’heure associées à un fichier.

## <a name="syntax"></a>Syntaxe

```cpp
class CFileTimeSpan
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|Constructeur.|

### <a name="public-methods"></a>Méthodes publiques

|Nom|Description|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Appelez cette méthode pour récupérer `CFileTimeSpan` la durée de l’objet.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Appelez cette méthode pour définir `CFileTimeSpan` la durée de l’objet.|

### <a name="public-operators"></a>Opérateurs publics

|Nom|Description|
|----------|-----------------|
|[CFileTimeSpan::opérateur -](#operator_-)|Effectue la soustraction `CFileTimeSpan` sur un objet.|
|[CFileTimeSpan::opérateur !](#operator_neq)|Compare deux objets `CFileTimeSpan` pour déterminer s'ils sont différents.|
|[CFileTimeSpan::opérateur](#operator_add)|Effectue l’addition `CFileTimeSpan` sur un objet.|
|[CFileTimeSpan::opérateur](#operator_add_eq)|Effectue l’ajout `CFileTimeSpan` sur un objet et attribue le résultat à l’objet actuel.|
|[CFileTimeSpan::opérateur&lt;](#operator_lt)|Compare deux `CFileTimeSpan` objets pour déterminer le moindre.|
|[CFileTimeSpan::opérateur&lt;=](#operator_lt_eq)|Compare deux `CFileTimeSpan` objets pour déterminer l’égalité ou le moindre.|
|[CFileTimeSpan::opérateur](#operator_eq)|L’opérateur de l’affectation.|
|[CFileTimeSpan::opérateur -MD](#operator_-_eq)|Effectue la soustraction `CFileTimeSpan` sur un objet et attribue le résultat à l’objet actuel.|
|[CFileTimeSpan::opérateur](#operator_eq_eq)|Compare deux objets `CFileTimeSpan` pour déterminer s’ils sont égaux.|
|[CFileTimeSpan::opérateur&gt;](#operator_gt)|Compare deux `CFileTimeSpan` objets pour déterminer le plus grand.|
|[CFileTimeSpan::opérateur&gt;=](#operator_gt_eq)|Compare deux `CFileTimeSpan` objets pour déterminer l’égalité ou le plus grand.|

## <a name="remarks"></a>Notes

La `CFileTimeSpan` classe fournit des méthodes pour gérer les périodes de temps relatives dans les unités que le système de fichiers utilise. Ces unités sont souvent utilisées dans les opérations de fichiers, comme lorsqu’un fichier a été créé, accessible pour la dernière fois ou modifié pour la dernière fois. Les méthodes de cette classe sont fréquemment utilisées en conjonction avec des objets [de classe CFileTime.](../../atl-mfc-shared/reference/cfiletime-class.md)

## <a name="example"></a>Exemple

Voir l’exemple pour [CFileTime:Milliseconde](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Spécifications

**En-tête:** atltime.h

## <a name="cfiletimespancfiletimespan"></a><a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

Constructeur.

```cpp
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Paramètres

*Span*\
Objet `CFileTimeSpan` existant.

*nSpan (en anglais)*\
Une période de temps dans les unités FILETIME.

### <a name="remarks"></a>Notes

L’objet `CFileTimeSpan` peut être `CFileTimeSpan` créé à l’aide d’un objet existant, ou exprimé comme une valeur 64 bits en unités FILETIME de 100 nanosecondes. Pour plus d’informations, voir [CFileTime](cfiletime-class.md). Le constructeur par défaut fixe la durée à 0.

## <a name="cfiletimespangettimespan"></a><a name="gettimespan"></a>CFileTimeSpan::GetTimeSpan

Appelez cette méthode pour récupérer `CFileTimeSpan` la durée de l’objet.

```cpp
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Valeur retournée

Retourne la durée en unités FILETIME de 100 nanosecondes. Pour plus d’informations, voir [CFileTime](cfiletime-class.md).

## <a name="cfiletimespanoperator--"></a><a name="operator_-"></a>CFileTimeSpan::opérateur -

Effectue la soustraction `CFileTimeSpan` sur un objet.

```cpp
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*Span*\
Objet `CFileTimeSpan` .

### <a name="return-value"></a>Valeur retournée

Retourne `CFileTimeSpan` un objet représentant le résultat de la différence entre deux périodes.

## <a name="cfiletimespanoperator-"></a><a name="operator_neq"></a>CFileTimeSpan::opérateur !

Compare deux objets `CFileTimeSpan` pour déterminer s'ils sont différents.

```cpp
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*Span*\
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur retournée

Retourne VRAI si l’élément comparé n’est pas égal à l’objet; `CFileTimeSpan` autrement FALSE.

## <a name="cfiletimespanoperator-"></a><a name="operator_add"></a>CFileTimeSpan::opérateur

Effectue l’addition `CFileTimeSpan` sur un objet.

```cpp
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*Span*\
Objet `CFileTimeSpan` .

### <a name="return-value"></a>Valeur retournée

Retourne `CFileTimeSpan` un objet contenant la somme des deux périodes.

## <a name="cfiletimespanoperator-"></a><a name="operator_add_eq"></a>CFileTimeSpan::opérateur

Effectue l’addition `CFileTimeSpan` sur un objet et attribue le résultat à l’objet actuel.

```cpp
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*Span*\
Objet `CFileTimeSpan` .

### <a name="return-value"></a>Valeur retournée

Retourne l’objet mis à jour `CFileTimeSpan` contenant la somme des deux périodes.

## <a name="cfiletimespanoperator-lt"></a><a name="operator_lt"></a>CFileTimeSpan::opérateur&lt;

Compare deux `CFileTimeSpan` objets pour déterminer le moindre.

```cpp
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*Span*\
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur retournée

Retourne VRAI si le premier objet est moins (c’est-à-dire, représente une période de temps plus courte) que le second, sinon FALSE.

## <a name="cfiletimespanoperator-lt"></a><a name="operator_lt_eq"></a>CFileTimeSpan::opérateur&lt;=

Compare deux `CFileTimeSpan` objets pour déterminer l’égalité ou le moindre.

```cpp
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*Span*\
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur retournée

Retourne VRAI si le premier objet est inférieur à (c’est-à-dire, représente une période de temps plus courte) ou égal au second, sinon FALSE.

## <a name="cfiletimespanoperator-"></a><a name="operator_eq"></a>CFileTimeSpan::opérateur

L’opérateur de l’affectation.

```cpp
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Paramètres

*Span*\
Objet `CFileTimeSpan` .

### <a name="return-value"></a>Valeur retournée

Retourne l’objet mis à jour. `CFileTimeSpan`

## <a name="cfiletimespanoperator--"></a><a name="operator_-_eq"></a>CFileTimeSpan::opérateur -MD

Effectue la soustraction `CFileTimeSpan` sur un objet et attribue le résultat à l’objet actuel.

```cpp
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Paramètres

*Span*\
Objet `CFileTimeSpan` .

### <a name="return-value"></a>Valeur retournée

Retourne l’objet mis à jour. `CFileTimeSpan`

## <a name="cfiletimespanoperator-"></a><a name="operator_eq_eq"></a>CFileTimeSpan::opérateur

Compare deux objets `CFileTimeSpan` pour déterminer s’ils sont égaux.

```cpp
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*Span*\
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur retournée

Retourne VRAI si les objets sont égaux, sinon FALSE.

## <a name="cfiletimespanoperator-gt"></a><a name="operator_gt"></a>CFileTimeSpan::opérateur&gt;

Compare deux `CFileTimeSpan` objets pour déterminer le plus grand.

```cpp
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*Span*\
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur retournée

Retourne VRAI si le premier objet est plus grand que (c’est-à-dire, représente une période de temps plus longue) que le second, sinon FALSE.

## <a name="cfiletimespanoperator-gt"></a><a name="operator_gt_eq"></a>CFileTimeSpan::opérateur&gt;=

Compare deux `CFileTimeSpan` objets pour déterminer l’égalité ou le plus grand.

```cpp
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Paramètres

*Span*\
Objet `CFileTimeSpan` à comparer.

### <a name="return-value"></a>Valeur retournée

Retourne VRAI si le premier objet est plus grand que (c’est-à-dire, représente une période de temps plus longue) ou égal à la seconde, sinon FALSE.

## <a name="cfiletimespansettimespan"></a><a name="settimespan"></a>CFileTimeSpan::SetTimeSpan

Appelez cette méthode pour définir `CFileTimeSpan` la durée de l’objet.

```cpp
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Paramètres

*nSpan (en anglais)*\
La nouvelle valeur pour la durée en unités FILETIME de 100 nanosecondes. Pour plus d’informations, voir [CFileTime](cfiletime-class.md).

## <a name="see-also"></a>Voir aussi

[TEMPS DE FICHIER](/windows/win32/api/minwinbase/ns-minwinbase-filetime)\
[Classe CFileTime](cfiletime-class.md)\
[Graphique de hiérarchie](../../mfc/hierarchy-chart.md)\
[Cours partagés ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
