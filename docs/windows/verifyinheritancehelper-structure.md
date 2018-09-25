---
title: VerifyInheritanceHelper (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInheritanceHelper structure
- Microsoft::WRL::Details::VerifyInheritanceHelper::Verify method
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6231345b837cae8f36e8441173300d804c0ea167
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169631"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename I,
   typename Base
>
struct VerifyInheritanceHelper;
template <
   typename I
>
struct VerifyInheritanceHelper<I, Nil>;
```

### <a name="parameters"></a>Paramètres

*I*<br/>
Type.

*base de*<br/>
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

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="verify"></a>VerifyInheritanceHelper::Verify

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
static void Verify();
```

### <a name="remarks"></a>Notes

Teste les deux interfaces spécifiées par les paramètres de modèle actuelle et détermine si une interface est dérivée de l’autre.

Une erreur est générée si une interface n’est pas dérivée de l’autre.
