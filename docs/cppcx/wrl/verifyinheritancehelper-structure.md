---
description: 'En savoir plus sur : structure VerifyInheritanceHelper'
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
ms.openlocfilehash: 672455482a2d21cb695124cad31740b6325c377d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135042"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename I, typename Base>
struct VerifyInheritanceHelper;

template <typename I>
struct VerifyInheritanceHelper<I, Nil>;
```

### <a name="parameters"></a>Paramètres

*Cliqu*<br/>
Type.

*Base*<br/>
Autre type.

## <a name="remarks"></a>Notes

Teste si une interface est dérivée d’une autre interface.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                       | Description
------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------
[VerifyInheritanceHelper :: Verify](#verify) | Teste les deux interfaces spécifiées par les paramètres de modèle actuels et détermine si une interface est dérivée de l’autre.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`VerifyInheritanceHelper`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="verifyinheritancehelperverify"></a><a name="verify"></a> VerifyInheritanceHelper :: Verify

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
static void Verify();
```

### <a name="remarks"></a>Notes

Teste les deux interfaces spécifiées par les paramètres de modèle actuels et détermine si une interface est dérivée de l’autre.

Une erreur est émise si une interface n’est pas dérivée de l’autre.
