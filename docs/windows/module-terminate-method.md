---
title: Module::Terminate, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Terminate
dev_langs:
- C++
helpviewer_keywords:
- Terminate method
ms.assetid: cf358117-45dc-43c7-ac1e-1e1eedc59e41
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7f89922fb107c1454ec81dfd8a9ac213608da962
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610841"
---
# <a name="moduleterminate-method"></a>Module::Terminate, méthode

Provoque toutes les fabriques instanciés par le module à arrêter.

## <a name="syntax"></a>Syntaxe

```cpp
void Terminate();
```

## <a name="remarks"></a>Notes

Libère les fabriques dans le cache.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi
[Module, classe](../windows/module-class.md)