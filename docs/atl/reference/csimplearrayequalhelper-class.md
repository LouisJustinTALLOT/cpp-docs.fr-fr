---
title: Csimplearrayequalhelper, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87b23ba46ee4a8e25c15b4d9e51b87c444da67f1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758213"
---
# <a name="csimplearrayequalhelper-class"></a>Csimplearrayequalhelper, classe

Cette classe est une application d’assistance pour la [CSimpleArray](../../atl/reference/csimplearray-class.md) classe.

## <a name="syntax"></a>Syntaxe

```
template <class T>  
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>Paramètres

`T`  
Une classe dérivée.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Statique) Teste si deux `CSimpleArray` éléments pour l’égalité de l’objet.|

## <a name="remarks"></a>Notes

Cette classe de traits constitue un supplément pour le `CSimpleArray` classe. Il fournit une méthode de comparaison de deux éléments stockés dans un `CSimpleArray` objet. Par défaut, les éléments sont comparés à l’aide de **operator=()**, mais si le tableau contient les types de données complexes qui ne disposent pas de leur propre opérateur d’égalité, vous devez substituer cette classe.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsimpcoll.h

##  <a name="isequal"></a>  CSimpleArrayEqualHelper::IsEqual

Teste si deux `CSimpleArray` éléments pour l’égalité de l’objet.

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>Paramètres

*T1*  
Un objet de type T.

*T2*  
Un objet de type T.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si les éléments sont égaux, sinon false.

## <a name="see-also"></a>Voir aussi

[CSimpleArray, classe](../../atl/reference/csimplearray-class.md)   
[Csimplearrayequalhelperfalse, classe](../../atl/reference/csimplearrayequalhelperfalse-class.md)   
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
