---
description: 'En savoir plus sur : structure Enableif ('
title: EnableIf (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
ms.openlocfilehash: 098dd5fdc7e37a7754d7124eba3e146575c127be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272849"
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

Définit un membre de données du type spécifié par le deuxième paramètre de modèle si le premier paramètre de modèle prend la valeur **`true`** .

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`type`|Si le paramètre de modèle *b* prend **`true`** la valeur, la spécialisation partielle définit le membre `type` de données comme étant de type `T` .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`EnableIf`

## <a name="requirements"></a>Spécifications

**En-tête :** Internal. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL ::D espace de noms étails](microsoft-wrl-details-namespace.md)
