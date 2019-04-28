---
title: Cdefaultcomparetraits, classe
ms.date: 11/04/2016
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
ms.openlocfilehash: c5f4ab3737838af11501c4a0f2037b57087939c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245910"
---
# <a name="cdefaultcomparetraits-class"></a>Cdefaultcomparetraits, classe

Cette classe fournit des fonctions de comparaison élément par défaut.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CDefaultCompareTraits
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
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

*element1*<br/>
Premier élément.

*element2*<br/>
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

*element1*<br/>
Premier élément.

*element2*<br/>
Le deuxième élément.

### <a name="return-value"></a>Valeur de retour

Retourne un entier basé sur le tableau suivant :

|Condition|Valeur de retour|
|---------------|------------------|
|*element1* < *element2*|<0|
|*element1* == *element2*|0|
|*element1* > *element2*|>0|

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction utilise le **==**, **\<**, et **>** opérateurs. Pour les objets autres que les types de données simples, cette fonction deviez être substituée.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
