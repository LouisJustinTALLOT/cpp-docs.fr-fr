---
title: InterfaceList (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: 70565081338f953abb65d2cdc7c5f1eb869f75e5
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784455"
---
# <a name="interfacelist-structure"></a>InterfaceList (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Un nom d’interface ; la première interface dans la liste récursive.

*U*<br/>
Un nom d’interface ; les interfaces restantes dans la liste récursive.

## <a name="remarks"></a>Notes

Utilisé pour créer une liste récursive des interfaces.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`FirstT`|Synonyme du paramètre modèle *T*.|
|`RestT`|Synonyme du paramètre modèle *U*.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`InterfaceList`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)