---
title: TerminateMap, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 2aa4d6733d2a4e458ff8abff192778d52a4522b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233494"
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

*Nom du serveur*<br/>
Nom d’un sous-ensemble de fabriques de classes dans le module spécifié par le *module*de paramètre.

*forceTerminate*<br/>
**`true`** pour arrêter les fabriques de classes indépendamment de leur activité ; **`false`** pour ne pas terminer les fabriques de classe si une fabrique est active.

## <a name="return-value"></a>Valeur de retour

**`true`** Si toutes les fabriques de classes ont été arrêtées ; Sinon, **`false`** .

## <a name="remarks"></a>Notes

Arrête les fabriques de classes dans le module spécifié.

## <a name="requirements"></a>Spécifications

**En-tête :** module. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL ::D espace de noms étails](microsoft-wrl-details-namespace.md)
