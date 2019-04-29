---
title: Variables globales ATL
ms.date: 12/06/2017
f1_keywords:
- ATLBASE/_pAtlModule
helpviewer_keywords:
- global variables, ATL
- _pAtlModule
ms.assetid: e881a319-99ca-4f5d-8a0b-34b3dcd0f37f
ms.openlocfilehash: 4f98b31d2454b7c6e903e5b5b87bceb4ddcb6961
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248158"
---
# <a name="atl-global-variables"></a>Variables globales ATL

## <a name="patlmodule"></a>_pAtlModule

Une variable globale stocker un pointeur vers le module actuel.

```cpp
__declspec(selectany) CAtlModule * _pAtlModule
```

### <a name="remarks"></a>Notes

Méthodes sur cette variable globale peuvent être utilisés pour fournir les fonctionnalités fournie par la classe (obsolète) CComModule dans Visual C++ 6.0.

### <a name="example"></a>Exemple

```cpp
LONG lLocks = _pAtlModule->GetLockCount();
```

### <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h
