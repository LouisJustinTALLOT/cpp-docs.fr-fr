---
title: Cdefaulthashtraits, classe
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: a51b4460d7fcdf778fce24b6e404b75190f598f6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257295"
---
# <a name="cdefaulthashtraits-class"></a>Cdefaulthashtraits, classe

Cette classe fournit une fonction statique pour le calcul des valeurs de hachage.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CDefaultHashTraits
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données à stocker dans la collection.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDefaultHashTraits::Hash](#hash)|(Statique) Appelez cette fonction pour calculer une valeur de hachage pour un élément donné.|

## <a name="remarks"></a>Notes

Cette classe contient une seule fonction statique qui retourne une valeur de hachage pour un élément donné. Cette classe est utilisée par le [cdefaultelementtraits, classe](../../atl/reference/cdefaultelementtraits-class.md).

Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll.h

##  <a name="hash"></a>  CDefaultHashTraits::Hash

Appelez cette fonction pour calculer une valeur de hachage pour un élément donné.

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>Paramètres

*element*<br/>
Élément.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de hachage.

### <a name="remarks"></a>Notes

L’algorithme de hachage par défaut est très simple : la valeur de retour est le numéro d’élément. Remplacez cette fonction si un algorithme plus complexe est nécessaire.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
