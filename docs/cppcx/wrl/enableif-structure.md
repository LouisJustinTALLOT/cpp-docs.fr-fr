---
title: EnableIf (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
ms.openlocfilehash: 44c6293b56e9e03c23d0d8cebf2a112e6fcf3664
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214030"
---
# <a name="enableif-structure"></a>EnableIf (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

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

Définit un membre de données du type spécifié par le deuxième paramètre de modèle si le premier paramètre de modèle prend la **valeur true**.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|`type`|Si le paramètre de modèle *b* prend la **valeur true**, la spécialisation partielle définit le membre de données `type` être de type `T`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`EnableIf`

## <a name="requirements"></a>Spécifications

**En-tête :** Internal. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)
