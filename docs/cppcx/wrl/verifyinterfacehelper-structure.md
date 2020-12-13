---
description: 'En savoir plus sur : structure VerifyInterfaceHelper'
title: VerifyInterfaceHelper (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
ms.openlocfilehash: a9b51eac55666d15b8362fc070d0feb731e9674d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135029"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper (structure)

Prend en charge l’infrastructure de la bibliothèque de modèles C++ Windows Runtime et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <bool isWinRTInterface, typename I>
struct VerifyInterfaceHelper;

template <typename I>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>Paramètres

*Cliqu*<br/>
Interface à vérifier.

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

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="verifyinterfacehelperverify"></a><a name="verify"></a> VerifyInterfaceHelper :: Verify

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
static void Verify();
```

### <a name="remarks"></a>Notes

Vérifie que l’interface spécifiée par le paramètre de modèle actuel répond à certaines exigences.
