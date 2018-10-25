---
title: Terminatemap, fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
dev_langs:
- C++
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bc5aec34177572552d119df967c9d25571b6cb63
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066030"
---
# <a name="terminatemap-function"></a>TerminateMap, fonction

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
inline bool TerminateMap(
   _In_ ModuleBase *module,
   _In_opt_z_ const wchar_t *serverName,
    bool forceTerminate) throw()
```

### <a name="parameters"></a>Paramètres

*module*<br/>
Un [module](../windows/module-class.md).

*Nom du serveur*<br/>
Le nom d’un sous-ensemble des fabriques de classes dans le module spécifié par le paramètre *module*.

*forceTerminate*<br/>
**true** pour mettre fin à la classe fabriques, quel que soit ils sont actifs ; **false** à se termine ne pas les fabriques de classe si n’importe quel factory est active.

## <a name="return-value"></a>Valeur de retour

**true** si toutes les fabriques de classe ont été terminées ; sinon, **false**.

## <a name="remarks"></a>Notes

Arrête les fabriques de classe dans le module spécifié.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)