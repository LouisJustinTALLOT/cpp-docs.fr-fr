---
title: VerifyInheritanceHelper (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInheritanceHelper structure
- Microsoft::WRL::Details::VerifyInheritanceHelper::Verify method
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
ms.openlocfilehash: c37a0eb74fd65b3d349d5b8b7c792fbaf7d1ac9a
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336404"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename I, typename Base>
struct VerifyInheritanceHelper;

template <typename I>
struct VerifyInheritanceHelper<I, Nil>;
```

### <a name="parameters"></a>Paramètres

*I*<br/>
Type.

*Base*<br/>
Un autre type.

## <a name="remarks"></a>Notes

Teste si une interface est dérivée d’une autre interface.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                       | Description
------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------
[VerifyInheritanceHelper::Verify](#verify) | Teste les deux interfaces spécifiées par les paramètres de modèle actuelle et détermine si une interface est dérivée de l’autre.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`VerifyInheritanceHelper`

## <a name="requirements"></a>Spécifications

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="verify"></a>VerifyInheritanceHelper::Verify

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
static void Verify();
```

### <a name="remarks"></a>Notes

Teste les deux interfaces spécifiées par les paramètres de modèle actuelle et détermine si une interface est dérivée de l’autre.

Une erreur est générée si une interface n’est pas dérivée de l’autre.
