---
title: CloakedIid (structure)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: 7340032e91a9b30b72099477b55b88740b3eb68f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535302"
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

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)