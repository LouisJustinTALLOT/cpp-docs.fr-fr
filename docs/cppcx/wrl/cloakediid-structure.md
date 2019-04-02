---
title: CloakedIid (structure)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: a47b9e5fdb4a6e7f49b9704244b4e62e3647a04e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784690"
---
# <a name="cloakediid-structure"></a>CloakedIid (structure)

Indique à la `RuntimeClass`, `Implements` et `ChainInterfaces` modèles que l’interface spécifiée n’est pas accessible dans la liste des IID.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
struct CloakedIid : T;
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
L’interface qui est masquée (masqué).

## <a name="remarks"></a>Notes

Voici un exemple illustrant **CloakedIid** est utilisé : `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`T`

`CloakedIid`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)