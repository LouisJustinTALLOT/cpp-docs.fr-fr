---
title: EnableIf (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
ms.openlocfilehash: 7b65b11b9a67ba69ca546e9bf5c169f3f2b61765
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784571"
---
# <a name="enableif-structure"></a>EnableIf (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <bool b, typename T = void>
struct EnableIf;

template <typename T>
struct EnableIf<true, T>;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type.

*b*<br/>
Expression booléenne.

## <a name="remarks"></a>Notes

Définit un membre de données du type spécifié par le deuxième paramètre de modèle si le premier paramètre de modèle prend la valeur **true**.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`type`|Si le paramètre de modèle *b* prend la valeur **true**, la spécialisation partielle définit le membre de données `type` soit de type `T`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`EnableIf`

## <a name="requirements"></a>Configuration requise

**En-tête :** internal.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)