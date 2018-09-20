---
title: Chaininterfaces::cancastto, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 752c3598a38117506154b0a2b7d7d3e578bf3c3e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417642"
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo, méthode

Indique si l’ID d’interface spécifié peut être casté à chacune des spécialisations définies par les paramètres du modèle de celle par défaut.

## <a name="syntax"></a>Syntaxe

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
ID d’interface.

*PPV*<br/>
Pointeur vers le dernier ID d’interface qui a été converti avec succès.

## <a name="return-value"></a>Valeur de retour

**true** si toutes les opérations de cast a réussi ; sinon, **false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[ChainInterfaces, structure](../windows/chaininterfaces-structure.md)