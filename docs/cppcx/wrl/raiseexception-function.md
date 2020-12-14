---
description: 'En savoir plus sur : fonction RaiseException'
title: RaiseException (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: b5353757ff04ab12c0fc61da6b2e98b2df835ef0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198438"
---
# <a name="raiseexception-function"></a>RaiseException (fonction)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
inline void __declspec(noreturn)   RaiseException(
      HRESULT hr,
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);
```

### <a name="parameters"></a>Paramètres

*heure(s)*<br/>
Code d’exception de l’exception levée ; autrement dit, HRESULT d’une opération ayant échoué.

*dwExceptionFlags*<br/>
Indicateur qui signale une exception continue (la valeur de l’indicateur est zéro) ou une exception non continuable (la valeur de l’indicateur est différente de zéro). Par défaut, l’exception n’est pas continue.

## <a name="remarks"></a>Notes

Lève une exception dans le thread appelant.

Pour plus d’informations, consultez la `RaiseException` fonction Windows.

## <a name="requirements"></a>Spécifications

**En-tête :** Internal. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL ::D espace de noms étails](microsoft-wrl-details-namespace.md)
