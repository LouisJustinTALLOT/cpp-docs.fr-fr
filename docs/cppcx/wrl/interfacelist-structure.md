---
title: InterfaceList (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: 7fd06f71bc4d8097366dc0e87d7ff92c5a12a790
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213861"
---
# <a name="interfacelist-structure"></a>InterfaceList (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Nom de l’interface ; première interface de la liste récursive.

*U*<br/>
Nom de l’interface ; interfaces restantes dans la liste récursive.

## <a name="remarks"></a>Notes

Utilisé pour créer une liste récursive d’interfaces.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`FirstT`|Synonyme du paramètre de modèle *T*.|
|`RestT`|Synonyme du paramètre de modèle *U*.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`InterfaceList`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)
