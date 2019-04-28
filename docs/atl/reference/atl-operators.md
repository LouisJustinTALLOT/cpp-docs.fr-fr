---
title: Opérateurs ATL
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: 6f1bd4f88b8d3a37f051a208a887c5264f61955a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260907"
---
# <a name="atl-operators"></a>Opérateurs ATL

Cette section contient les rubriques de référence pour les opérateurs globaux ATL.

|Opérateur|Description|
|--------------|-----------------|
|[operator ==](#operator_eq_eq)|Compare deux `CSid` objets ou `SID` structures sont égales.|
|[operator !=](#operator_neq)|Compare deux `CSid` objets ou `SID` inégalité des structures.|
|[opérateur <](#operator_lt)|Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est inférieur au `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).|
|[opérateur >](#operator_gt)|Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est supérieur à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).|
|[operator <=](#operator_lt__eq)|Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est inférieur ou égal à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).|
|[operator >=](#operator_gt__eq)|Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est supérieur ou égal à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsecurity.h.

##  <a name="operator_eq_eq"></a>  operator ==

Compare `CSid` objets ou `SID` égalité des structures (identificateur de sécurité).

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*lhs*<br/>
La première `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
La seconde `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les objets sont égaux, FALSE si elles ne sont pas égales.

##  <a name="operator_neq"></a>  opérateur ! =

Compare `CSid` objets ou `SID` inégalité des structures (identificateur de sécurité).

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*lhs*<br/>
La première `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
La seconde `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les objets ne sont pas identiques, FALSE si elles sont égales.

##  <a name="operator_lt"></a>  opérateur <

Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est inférieur au `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*lhs*<br/>
La première `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
La seconde `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’adresse de la *lhs* objet est inférieur à l’adresse de la *rhs* de l’objet, FALSE sinon.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de la `CSid` objet ou `SID` structure et est implémenté pour assurer une compatibilité avec les classes de collection de bibliothèque C++ Standard.

##  <a name="operator_gt"></a>  operator >

Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est supérieur à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*lhs*<br/>
La première `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
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

*lhs*<br/>
La première `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
La seconde `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’adresse de la *lhs* est inférieur ou égal à l’adresse de la *rhs*, FALSE sinon.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de la `CSid` objet ou `SID` structure et est implémenté pour assurer une compatibilité avec les classes de collection de bibliothèque C++ Standard.

##  <a name="operator_gt__eq"></a>  operator >=

Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est supérieur ou égal à la `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*lhs*<br/>
La première `CSid` objet ou `SID` structure à comparer.

*rhs*<br/>
La seconde `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’adresse de la *lhs* est supérieur ou égal à l’adresse de la *rhs*, FALSE sinon.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de la `CSid` objet ou `SID` structure et est implémenté pour assurer une compatibilité avec les classes de collection de bibliothèque C++ Standard.
