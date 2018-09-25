---
title: VerifyInterfaceHelper (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e7aa7d796fb30a30a100f5f914feec57909407e5
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169760"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper (structure)

Prend en charge l’infrastructure de la bibliothèque de modèles Windows Runtime C++ et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   bool isWinRTInterface,
   typename I
>
struct VerifyInterfaceHelper;

template <
   typename I
>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>Paramètres

*I*<br/>
Une interface à vérifier.

*isWinRTInterface*

## <a name="remarks"></a>Notes

Vérifie que l’interface spécifiée par le paramètre de modèle répond à certaines exigences.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                            | Description
----------------------------------------------- | ---------------------------------------------------------------------------------------------------
[VerifyInterfaceHelper::Verify, méthode](#verify) | Vérifie que l’interface spécifiée par le paramètre de modèle actuel répond à certaines exigences.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`VerifyInterfaceHelper`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="verify"></a>VerifyInterfaceHelper::Verify

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
static void Verify();
```

### <a name="remarks"></a>Notes

Vérifie que l’interface spécifiée par le paramètre de modèle actuel répond à certaines exigences.
