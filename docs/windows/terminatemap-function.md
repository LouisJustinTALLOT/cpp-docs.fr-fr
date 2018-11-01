---
title: TerminateMap, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: efee7edfc1085288b3220698024cb0deeb4e71af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643220"
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