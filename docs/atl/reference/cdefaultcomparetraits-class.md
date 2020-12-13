---
description: 'En savoir plus sur : classe CDefaultCompareTraits'
title: CDefaultCompareTraits, classe
ms.date: 11/04/2016
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
ms.openlocfilehash: dcb366cdcd99a6eed2b641be290ccc4913a81476
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141906"
---
# <a name="cdefaultcomparetraits-class"></a>CDefaultCompareTraits, classe

Cette classe fournit des fonctions de comparaison d’éléments par défaut.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CDefaultCompareTraits
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données à stocker dans la collection.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDefaultCompareTraits::CompareElements](#compareelements)|Statique Appelez cette fonction pour comparer deux éléments d’égalité.|
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|Statique Appelez cette fonction pour déterminer l’élément supérieur et le plus petit.|

## <a name="remarks"></a>Notes

Cette classe contient deux fonctions statiques pour comparer des éléments stockés dans un objet de classe de collection. Cette classe est utilisée par la [classe CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md).

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="cdefaultcomparetraitscompareelements"></a><a name="compareelements"></a> CDefaultCompareTraits::CompareElements

Appelez cette fonction pour comparer deux éléments d’égalité.

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>Paramètres

*Élément1*<br/>
Premier élément.

*élément2*<br/>
Deuxième élément.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si les éléments sont égaux, sinon false.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est l’opérateur d’égalité ( **==** ). Pour les objets autres que les types de données simples, cette fonction doit être substituée.

## <a name="cdefaultcomparetraitscompareelementsordered"></a><a name="compareelementsordered"></a> CDefaultCompareTraits::CompareElementsOrdered

Appelez cette fonction pour déterminer l’élément supérieur et le plus petit.

```
static int CompareElementsOrdered(const T& element1, const T& element2);
```

### <a name="parameters"></a>Paramètres

*Élément1*<br/>
Premier élément.

*élément2*<br/>
Deuxième élément.

### <a name="return-value"></a>Valeur renvoyée

Retourne un entier basé sur le tableau suivant :

|Condition|Valeur retournée|
|---------------|------------------|
|*element1*  <  *élément2*|<0|
|*element1*  ==  *élément2*|0|
|*element1*  >  *élément2*|>0|

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction utilise **==** les **\<**, and **>** opérateurs,. Pour les objets autres que les types de données simples, cette fonction doit être substituée.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
