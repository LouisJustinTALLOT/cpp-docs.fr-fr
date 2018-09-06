---
title: Cdefaultcomparetraits, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4983984c8bf1cad2996818625091b60cdb732a9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758555"
---
# <a name="cdefaultcomparetraits-class"></a>Cdefaultcomparetraits, classe

Cette classe fournit des fonctions de comparaison élément par défaut.

## <a name="syntax"></a>Syntaxe

```
template<typename T>  
class CDefaultCompareTraits
```

#### <a name="parameters"></a>Paramètres

*T*  
Le type de données à stocker dans la collection.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDefaultCompareTraits::CompareElements](#compareelements)|(Statique) Appelez cette fonction pour comparer deux éléments sont égaux.|
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|(Statique) Appelez cette fonction pour déterminer l’élément supérieur et inférieur.|

## <a name="remarks"></a>Notes

Cette classe contient deux fonctions statiques pour la comparaison d’éléments stockés dans un objet de classe de collection. Cette classe est utilisée par le [cdefaultelementtraits, classe](../../atl/reference/cdefaultelementtraits-class.md).

Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

##  <a name="compareelements"></a>  CDefaultCompareTraits::CompareElements

Appelez cette fonction pour comparer deux éléments sont égaux.

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>Paramètres

*Element1*  
Premier élément.

*élément2*  
Le deuxième élément.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si les éléments sont égaux, sinon false.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est l’égalité (**==**) opérateur. Pour les objets autres que les types de données simples, cette fonction deviez être substituée.

##  <a name="compareelementsordered"></a>  CDefaultCompareTraits::CompareElementsOrdered

Appelez cette fonction pour déterminer l’élément supérieur et inférieur.

```
static int CompareElementsOrdered(const T& element1, const T& element2);
```

### <a name="parameters"></a>Paramètres

*Element1*  
Premier élément.

*élément2*  
Le deuxième élément.

### <a name="return-value"></a>Valeur de retour

Retourne un entier basé sur le tableau suivant :

|Condition|Valeur de retour|
|---------------|------------------|
|*Element1* < *élément2*|<0|
|*Element1* == *élément2*|0|
|*Element1* > *élément2*|>0|

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction utilise le **==**, **\<**, et **>** opérateurs. Pour les objets autres que les types de données simples, cette fonction deviez être substituée.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
