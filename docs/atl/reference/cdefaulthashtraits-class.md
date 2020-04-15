---
title: Classe CDefaultHashTraits
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: 43932092621d44cfc8b07270df92e2765665f23f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327083"
---
# <a name="cdefaulthashtraits-class"></a>Classe CDefaultHashTraits

Cette classe fournit une fonction statique pour calculer les valeurs de hachage.

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

Cette classe contient une seule fonction statique qui renvoie une valeur de hachage pour un élément donné. Cette classe est utilisée par la [classe CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md).

Pour plus d’informations, voir [cours de collecte ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="cdefaulthashtraitshash"></a><a name="hash"></a>CDefaultHashTraits::Hash

Appelez cette fonction pour calculer une valeur de hachage pour un élément donné.

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>Paramètres

*Élément*<br/>
Élément.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur du hachage.

### <a name="remarks"></a>Notes

L’algorithme de hachage par défaut est très simple : la valeur de retour est le numéro d’élément. Remplacer cette fonction si un algorithme plus compliqué est nécessaire.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
