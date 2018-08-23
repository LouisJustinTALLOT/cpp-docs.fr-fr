---
title: Module::registerobjects, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterObjects
dev_langs:
- C++
helpviewer_keywords:
- RegisterObjects method
ms.assetid: db4077b7-068d-4534-aaa5-41b5444ccb49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c9a44fed853fe2f4dcd3196e926b3848566ab4e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597024"
---
# <a name="moduleregisterobjects-method"></a>Module::RegisterObjects, méthode

Enregistre les objets COM ou Windows Runtime pour d’autres applications peuvent se connecter à leur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Paramètres

*module*  
Un tableau d’objets COM ou Windows Runtime.

*Nom du serveur*  
Nom du serveur qui a créé les objets.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, un HRESULT qui indique la raison pour laquelle l’opération a échoué.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Module, classe](../windows/module-class.md)