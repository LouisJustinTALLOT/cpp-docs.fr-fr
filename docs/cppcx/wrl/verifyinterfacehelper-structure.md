---
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
ms.openlocfilehash: 09c2cc7e08e2dc0e8df42c64d285c37627c5925a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374244"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper (structure)

Prend en charge l’infrastructure windows Runtime CMD Template Library et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <bool isWinRTInterface, typename I>
struct VerifyInterfaceHelper;

template <typename I>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>Paramètres

*Ⅰ*<br/>
Une interface à vérifier.

*isWinRTInterface*

## <a name="remarks"></a>Notes

Vérifie que l’interface spécifiée par le paramètre du modèle répond à certaines exigences.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                            | Description
----------------------------------------------- | ---------------------------------------------------------------------------------------------------
[VerifyInterfaceHelper::Verify, méthode](#verify) | Vérifie que l’interface spécifiée par le paramètre du modèle actuel répond à certaines exigences.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`VerifyInterfaceHelper`

## <a name="requirements"></a>Spécifications

**En-tête:** implements.h

**Espace nom:** Microsoft::WRL::Details

## <a name="verifyinterfacehelperverify"></a><a name="verify"></a>VerifyInterfaceHelper::Vérifier

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
static void Verify();
```

### <a name="remarks"></a>Notes

Vérifie que l’interface spécifiée par le paramètre du modèle actuel répond à certaines exigences.
