---
title: Microsoft::WRL::Wrappers::Details, espace de noms
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details
- internal/Microsoft::WRL::Details
- async/Microsoft::WRL::Details
- corewrappers/Microsoft::WRL::Wrappers::Details
- client/Microsoft::WRL::Details
- module/Microsoft::WRL::Details
- event/Microsoft::WRL::Details
helpviewer_keywords:
- Details namespace
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
ms.openlocfilehash: d02b19863ffa14e0edb3b1a96dceb936037743d3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784575"
---
# <a name="microsoftwrlwrappersdetails-namespace"></a>Microsoft::WRL::Wrappers::Details, espace de noms

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Wrappers::Details;
```

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|Nom|Description|
|----------|-----------------|
|[SyncLockT, classe](synclockt-class.md)|Représente un type qui peut prendre exclusif ou la propriété d’une ressource partagée.|
|[SyncLockWithStatusT, classe](synclockwithstatust-class.md)|Représente un type qui peut prendre exclusif ou la propriété d’une ressource partagée.|

### <a name="methods"></a>Méthodes

|Nom|Description|
|----------|-----------------|
|[CompareStringOrdinal, méthode](comparestringordinal-method.md)|Compare deux spécifié `HSTRING` objets et retourne un entier qui indique leur position relative dans un ordre de tri.|

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers, espace de noms](microsoft-wrl-wrappers-namespace.md)