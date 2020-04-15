---
title: Classe CDefaultCompareTraits
ms.date: 11/04/2016
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
ms.openlocfilehash: 8262800ef613424c37c53931d97dd4b1b1a71321
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327076"
---
# <a name="cdefaultcomparetraits-class"></a>Classe CDefaultCompareTraits

Cette classe fournit des fonctions de comparaison d’éléments par défaut.

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
|[CDefaultCompareTraits::CompareElements](#compareelements)|(Statique) Appelez cette fonction pour comparer deux éléments pour l’égalité.|
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|(Statique) Appelez cette fonction pour déterminer l’élément le plus grand et le moindre.|

## <a name="remarks"></a>Notes

Cette classe contient deux fonctions statiques pour comparer les éléments stockés dans un objet de classe de collection. Cette classe est utilisée par la [classe CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md).

Pour plus d’informations, voir [cours de collecte ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="cdefaultcomparetraitscompareelements"></a><a name="compareelements"></a>CDefaultCompareTraits::CompareElements

Appelez cette fonction pour comparer deux éléments pour l’égalité.

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>Paramètres

*élément1*<br/>
Premier élément.

*élément2*<br/>
Le deuxième élément.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si les éléments sont égaux, faux autrement.

### <a name="remarks"></a>Notes

La mise en œuvre**==** par défaut de cette fonction est l’égalité () opérateur. Pour les objets autres que les types de données simples, cette fonction peut devoir être remplacée.

## <a name="cdefaultcomparetraitscompareelementsordered"></a><a name="compareelementsordered"></a>CDefaultCompareTraits::CompareElementsOrdered

Appelez cette fonction pour déterminer l’élément le plus grand et le moindre.

```
static int CompareElementsOrdered(const T& element1, const T& element2);
```

### <a name="parameters"></a>Paramètres

*élément1*<br/>
Premier élément.

*élément2*<br/>
Le deuxième élément.

### <a name="return-value"></a>Valeur de retour

Retourne un intégrant en fonction du tableau suivant :

|Condition|Valeur retournée|
|---------------|------------------|
|*élément12* < *element2*|<0|
|*élément12* == *element2*|0|
|*élément12* > *element2*|>0|

### <a name="remarks"></a>Notes

La mise en œuvre **\<** par **>** défaut de cette fonction utilise le **==**, , et les opérateurs. Pour les objets autres que les types de données simples, cette fonction peut devoir être remplacée.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
