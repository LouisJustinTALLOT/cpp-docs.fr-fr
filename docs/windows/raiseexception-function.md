---
title: RaiseException (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: af0b35e1014f79c7907711b95200c241d31b6117
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594751"
---
# <a name="raiseexception-function"></a>RaiseException (fonction)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
inline void __declspec(noreturn)   RaiseException(
      HRESULT hr,
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);
```

### <a name="parameters"></a>Paramètres

*ressources humaines*<br/>
Le code d’exception de l’exception est levée ; Autrement dit, la valeur HRESULT d’échec d’une opération.

*dwExceptionFlags*<br/>
Un indicateur qui indique une exception non bloquantes (la valeur de l’indicateur est égal à zéro), ou une exception noncontinuable (la valeur de l’indicateur est différent de zéro). Par défaut, l’exception est qui empêchait celle-ci.

## <a name="remarks"></a>Notes

Lève une exception dans le thread appelant.

Pour plus d’informations, consultez le Windows `RaiseException` (fonction).

## <a name="requirements"></a>Configuration requise

**En-tête :** internal.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)