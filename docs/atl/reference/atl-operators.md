---
title: Opérateurs ATL
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: 361b0316e27ee06c64b3ed5e11c6aab10210596f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476256"
---
# <a name="atl-operators"></a>Opérateurs ATL

Cette section contient les rubriques de référence pour les opérateurs globaux ATL.

|Opérateur|Description|
|--------------|-----------------|
|[opérateur ==](#operator_eq_eq)|Compare deux `CSid` objets ou `SID` structures sont égales.|
|[opérateur ! =](#operator_neq)|Compare deux `CSid` objets ou `SID` inégalité des structures.|
|[opérateur <](#operator_lt)|Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est inférieur au `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).|
|[opérateur >](#operator_gt)|Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est supérieur à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).|
|[opérateur < =](#operator_lt__eq)|Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est inférieur ou égal à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).|
|[opérateur > =](#operator_gt__eq)|Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est supérieur ou égal à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsecurity.h.

##  <a name="operator_eq_eq"></a>  opérateur ==

Compare `CSid` objets ou `SID` égalité des structures (identificateur de sécurité).

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
La première `CSid` objet ou `SID` structure à comparer.

*terme de droite*<br/>
La seconde `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les objets sont égaux, FALSE si elles ne sont pas égales.

##  <a name="operator_neq"></a>  opérateur ! =

Compare `CSid` objets ou `SID` inégalité des structures (identificateur de sécurité).

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
La première `CSid` objet ou `SID` structure à comparer.

*terme de droite*<br/>
La seconde `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les objets ne sont pas identiques, FALSE si elles sont égales.

##  <a name="operator_lt"></a>  opérateur <

Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est inférieur au `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
La première `CSid` objet ou `SID` structure à comparer.

*terme de droite*<br/>
La seconde `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’adresse de la *lhs* objet est inférieur à l’adresse de la *rhs* de l’objet, FALSE sinon.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de la `CSid` objet ou `SID` structure et est implémenté pour assurer une compatibilité avec les classes de collection de bibliothèque C++ Standard.

##  <a name="operator_gt"></a>  opérateur >

Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est supérieur à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
La première `CSid` objet ou `SID` structure à comparer.

*terme de droite*<br/>
La seconde `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’adresse de la *lhs* est supérieure à l’adresse de la *rhs*, FALSE sinon.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de la `CSid` objet ou `SID` structure et est implémenté pour assurer une compatibilité avec les classes de collection de bibliothèque C++ Standard.

##  <a name="operator_lt__eq"></a>  opérateur < =

Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est inférieur ou égal à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
La première `CSid` objet ou `SID` structure à comparer.

*terme de droite*<br/>
La seconde `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’adresse de la *lhs* est inférieur ou égal à l’adresse de la *rhs*, FALSE sinon.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de la `CSid` objet ou `SID` structure et est implémenté pour assurer une compatibilité avec les classes de collection de bibliothèque C++ Standard.

##  <a name="operator_gt__eq"></a>  opérateur > =

Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est supérieur ou égal à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*<br/>
La première `CSid` objet ou `SID` structure à comparer.

*terme de droite*<br/>
La seconde `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’adresse de la *lhs* est supérieur ou égal à l’adresse de la *rhs*, FALSE sinon.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de la `CSid` objet ou `SID` structure et est implémenté pour assurer une compatibilité avec les classes de collection de bibliothèque C++ Standard.

