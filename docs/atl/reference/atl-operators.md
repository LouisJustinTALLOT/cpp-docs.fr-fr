---
title: Opérateurs ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f5027fa4b84d84bf07766c7ac4e75f140706f0c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103701"
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

*LHS*  
La première `CSid` objet ou `SID` structure à comparer.

*terme de droite*  
La seconde `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les objets sont égaux, FALSE si elles ne sont pas égales.

##  <a name="operator_neq"></a>  opérateur ! =

Compare `CSid` objets ou `SID` inégalité des structures (identificateur de sécurité).

```   
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*  
La première `CSid` objet ou `SID` structure à comparer.

*terme de droite*  
La seconde `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les objets ne sont pas identiques, FALSE si elles sont égales.

##  <a name="operator_lt"></a>  opérateur <

Teste si le `CSid` objet ou `SID` structure sur le côté gauche de l’opérateur est inférieur au `CSid` objet ou `SID` structure sur le côté droit (pour la compatibilité de la bibliothèque C++ Standard).

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Paramètres

*LHS*  
La première `CSid` objet ou `SID` structure à comparer.

*terme de droite*  
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

*LHS*  
La première `CSid` objet ou `SID` structure à comparer.

*terme de droite*  
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

*LHS*  
La première `CSid` objet ou `SID` structure à comparer.

*terme de droite*  
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

*LHS*  
La première `CSid` objet ou `SID` structure à comparer.

*terme de droite*  
La seconde `CSid` objet ou `SID` structure à comparer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’adresse de la *lhs* est supérieur ou égal à l’adresse de la *rhs*, FALSE sinon.

### <a name="remarks"></a>Notes

Cet opérateur agit sur l’adresse de la `CSid` objet ou `SID` structure et est implémenté pour assurer une compatibilité avec les classes de collection de bibliothèque C++ Standard.

