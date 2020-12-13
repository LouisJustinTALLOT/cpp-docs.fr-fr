---
description: 'En savoir plus sur : classe CAtlFileMapping'
title: CAtlFileMapping, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: 875979d47ad4cb5b9c59047eff1f50acd35d1251
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147418"
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
|[CAtlFileMapping :: Operator T *](#operator_t_star)|Autorise la conversion implicite d' `CAtlFileMapping` objets en `T*` .|

## <a name="remarks"></a>Notes

Cette classe ajoute un opérateur de cast unique pour permettre la conversion implicite d' `CAtlFileMapping` objets en `T*` . Les autres membres sont fournis par la classe de base, [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>Spécifications

**En-tête :** atlfile. h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a> CAtlFileMapping :: Operator T *

Autorise la conversion implicite d' `CAtlFileMapping` objets en `T*` .

```cpp
operator T*() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un `T*` pointeur vers le début du fichier mappé en mémoire.

### <a name="remarks"></a>Notes

Appelle [CAtlFileMappingBase :: GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) et réinterprète le pointeur retourné comme un `T*` où *T* est le type utilisé comme paramètre de modèle de cette classe.

## <a name="see-also"></a>Voir aussi

[CAtlFileMappingBase, classe](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
