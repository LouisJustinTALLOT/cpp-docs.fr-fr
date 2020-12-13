---
description: 'En savoir plus sur : classe CDefaultHashTraits'
title: CDefaultHashTraits, classe
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: 85cc881466be03931d435d91a48548456d74305b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141880"
---
# <a name="cdefaulthashtraits-class"></a>CDefaultHashTraits, classe

Cette classe fournit une fonction statique pour le calcul des valeurs de hachage.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CDefaultHashTraits
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données à stocker dans la collection.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDefaultHashTraits :: Hash](#hash)|Statique Appelez cette fonction pour calculer une valeur de hachage pour un élément donné.|

## <a name="remarks"></a>Notes

Cette classe contient une fonction statique unique qui retourne une valeur de hachage pour un élément donné. Cette classe est utilisée par la [classe CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md).

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="cdefaulthashtraitshash"></a><a name="hash"></a> CDefaultHashTraits :: Hash

Appelez cette fonction pour calculer une valeur de hachage pour un élément donné.

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>Paramètres

*appartient*<br/>
Élément.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur de hachage.

### <a name="remarks"></a>Notes

L’algorithme de hachage par défaut est très simple : la valeur de retour est le numéro de l’élément. Substituez cette fonction si un algorithme plus complexe est requis.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
