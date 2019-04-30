---
title: TerminateMap, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 2a451bf68bfb543ee5e82a9a48097cac7e8a9821
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398119"
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
Un [module](module-class.md).

*serverName*<br/>
Le nom d’un sous-ensemble des fabriques de classes dans le module spécifié par le paramètre *module*.

*forceTerminate*<br/>
**true** pour mettre fin à la classe fabriques, quel que soit ils sont actifs ; **false** à se termine ne pas les fabriques de classe si n’importe quel factory est active.

## <a name="return-value"></a>Valeur de retour

**true** si toutes les fabriques de classe ont été terminées ; sinon, **false**.

## <a name="remarks"></a>Notes

Arrête les fabriques de classe dans le module spécifié.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)