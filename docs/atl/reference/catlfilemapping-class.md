---
title: Classe CAtlFileMapping
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: ca46ccdacf5ea24f1de26cdc75bf808c4ecfaa40
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318957"
---
# <a name="catlfilemapping-class"></a>Classe CAtlFileMapping

Cette classe représente un fichier cartographié par la mémoire, ajoutant un opérateur de distribution aux méthodes de [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données utilisées pour l’opérateur de distribution.

## <a name="members"></a>Membres

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlFileMapping::opérateur T](#operator_t_star)|Permet la `CAtlFileMapping` conversion `T*`implicite des objets en .|

## <a name="remarks"></a>Notes

Cette classe ajoute un seul opérateur `CAtlFileMapping` de `T*`distribution pour permettre la conversion implicite des objets en . D’autres membres sont fournis par la classe de base, [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>Spécifications

**En-tête:** atlfile.h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFileMapping::opérateur T

Permet la `CAtlFileMapping` conversion `T*`implicite des objets en .

```
operator T*() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne `T*` un pointeur au début du fichier cartographié par la mémoire.

### <a name="remarks"></a>Notes

Appels [CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) et réinterprète le `T*` pointeur retourné comme un où *T* est le type utilisé comme paramètre de modèle de cette classe.

## <a name="see-also"></a>Voir aussi

[Classe CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
