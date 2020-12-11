---
description: 'En savoir plus sur : variables globales ATL'
title: Variables globales ATL
ms.date: 12/06/2017
f1_keywords:
- ATLBASE/_pAtlModule
helpviewer_keywords:
- global variables, ATL
- _pAtlModule
ms.assetid: e881a319-99ca-4f5d-8a0b-34b3dcd0f37f
ms.openlocfilehash: 8d0544651e32f5e569973466af8ce04af1433766
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158775"
---
# <a name="atl-global-variables"></a>Variables globales ATL

## <a name="_patlmodule"></a>_pAtlModule

Variable globale qui stocke un pointeur vers le module en cours.

```cpp
__declspec(selectany) CAtlModule * _pAtlModule
```

### <a name="remarks"></a>Notes

Les méthodes de cette variable globale peuvent être utilisées pour fournir les fonctionnalités de la classe (désormais obsolète) CComModule fournies dans Visual C++ 6,0.

### <a name="example"></a>Exemple

```cpp
LONG lLocks = _pAtlModule->GetLockCount();
```

### <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h
