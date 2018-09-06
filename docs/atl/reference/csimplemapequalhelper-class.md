---
title: Csimplemapequalhelper, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1670ff7ed53d05b1dfc09e6953650892b0335f61
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761467"
---
# <a name="csimplemapequalhelper-class"></a>Csimplemapequalhelper, classe

Cette classe est une application d’assistance pour la [CSimpleMap](../../atl/reference/csimplemap-class.md) classe.

## <a name="syntax"></a>Syntaxe

```
template <class TKey, class TVal>  
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>Paramètres

*TKey*  
L’élément clé.

*TVal*  
L’élément de valeur.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Statique) Teste l’égalité de deux clés.|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Statique) Teste l’égalité de deux valeurs.|

## <a name="remarks"></a>Notes

Cette classe de traits constitue un supplément pour le `CSimpleMap` classe. Il fournit des méthodes pour la comparaison de deux `CSimpleMap` éléments (plus précisément, les composants clé et valeur) pour l’égalité de l’objet. Par défaut, les clés et valeurs sont comparées à l’aide de **Operator == ()**, mais si le mappage contient des types de données complexes qui ne disposent pas de leur propre opérateur d’égalité, cette classe peut être substituée pour fournir la fonctionnalité supplémentaire requise.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsimpcoll.h

##  <a name="isequalkey"></a>  CSimpleMapEqualHelper::IsEqualKey

Teste l’égalité de deux clés.

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>Paramètres

*K1*  
La première clé.

*K2*  
La deuxième clé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si les clés sont égales, sinon false.

##  <a name="isequalvalue"></a>  CSimpleMapEqualHelper::IsEqualValue

Teste l’égalité de deux valeurs.

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>Paramètres

*V1*  
Première valeur.

*v2*  
Seconde valeur.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si les valeurs sont égales, sinon false.

## <a name="see-also"></a>Voir aussi

[Csimplemapequalhelperfalse, classe](../../atl/reference/csimplemapequalhelperfalse-class.md)   
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
