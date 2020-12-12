---
description: 'En savoir plus sur : structure Interfacelist ('
title: InterfaceList (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: 660ae5137b7ff41129ce3866f0d289045f7dee9c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124577"
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

|Nom|Description|
|----------|-----------------|
|`FirstT`|Synonyme du paramètre de modèle *T*.|
|`RestT`|Synonyme du paramètre de modèle *U*.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`InterfaceList`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL ::D espace de noms étails](microsoft-wrl-details-namespace.md)
