---
description: 'En savoir plus sur : fonction Terminatemap,'
title: TerminateMap, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 919759d0b4b7f67cf3aff83c3e83678860d0badc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135061"
---
# <a name="terminatemap-function"></a>TerminateMap, fonction

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
inline bool TerminateMap(
   _In_ ModuleBase *module,
   _In_opt_z_ const wchar_t *serverName,
    bool forceTerminate) throw()
```

### <a name="parameters"></a>Paramètres

*modules*<br/>
[Module](module-class.md).

*serverName*<br/>
Nom d’un sous-ensemble de fabriques de classes dans le module spécifié par le *module* de paramètre.

*forceTerminate*<br/>
**`true`** pour arrêter les fabriques de classes indépendamment de leur activité ; **`false`** pour ne pas terminer les fabriques de classe si une fabrique est active.

## <a name="return-value"></a>Valeur renvoyée

**`true`** Si toutes les fabriques de classes ont été arrêtées ; Sinon, **`false`** .

## <a name="remarks"></a>Notes

Arrête les fabriques de classes dans le module spécifié.

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL ::D espace de noms étails](microsoft-wrl-details-namespace.md)
