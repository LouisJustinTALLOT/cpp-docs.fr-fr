---
title: CAtlFileMapping, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: 7516349e4ec54d8cb90fa6ff23b0ded954aa043b
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168122"
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping, classe

Cette classe représente un fichier mappé en mémoire, en ajoutant un opérateur de cast aux méthodes de [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données utilisé pour l’opérateur de conversion.

## <a name="members"></a>Membres

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlFileMapping :: Operator T *](#operator_t_star)|Autorise la conversion implicite `CAtlFileMapping` d' `T*`objets en.|

## <a name="remarks"></a>Notes

Cette classe ajoute un opérateur de cast unique pour permettre la conversion `CAtlFileMapping` implicite `T*`d’objets en. Les autres membres sont fournis par la classe de base, [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>Spécifications

**En-tête :** atlfile. h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFileMapping :: Operator T *

Autorise la conversion implicite `CAtlFileMapping` d' `T*`objets en.

```cpp
operator T*() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un `T*` pointeur vers le début du fichier mappé en mémoire.

### <a name="remarks"></a>Notes

Appelle [CAtlFileMappingBase :: GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) et réinterprète le pointeur retourné comme un `T*` où *T* est le type utilisé comme paramètre de modèle de cette classe.

## <a name="see-also"></a>Voir aussi

[CAtlFileMappingBase, classe](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
