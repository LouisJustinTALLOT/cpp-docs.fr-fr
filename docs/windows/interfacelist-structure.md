---
title: InterfaceList (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
dev_langs:
- C++
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d9cbc1dfb31d744086e7a138521ae24f58e693f
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788654"
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

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)