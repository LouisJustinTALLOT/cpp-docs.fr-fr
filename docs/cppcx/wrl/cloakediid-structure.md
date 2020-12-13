---
description: 'En savoir plus sur : structure Cloakediid,'
title: CloakedIid (structure)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: 06bddded27882ae1216064aafc311364a8d2fd9f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338787"
---
# <a name="cloakediid-structure"></a>CloakedIid (structure)

Indique aux `RuntimeClass` modèles, `Implements` et `ChainInterfaces` que l’interface spécifiée n’est pas accessible dans la liste iid.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
struct CloakedIid : T;
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Interface masquée (masquée).

## <a name="remarks"></a>Notes

Voici un exemple d’utilisation de **cloakediid,** : `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}` .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`T`

`CloakedIid`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
