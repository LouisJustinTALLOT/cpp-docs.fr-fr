---
title: RaiseException (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: 3270057bf5b1b27a98bef1ab236291eab15d27ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213627"
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

*h*<br/>
Code d’exception de l’exception levée ; autrement dit, HRESULT d’une opération ayant échoué.

*dwExceptionFlags*<br/>
Indicateur qui signale une exception continue (la valeur de l’indicateur est zéro) ou une exception non continuable (la valeur de l’indicateur est différente de zéro). Par défaut, l’exception n’est pas continue.

## <a name="remarks"></a>Notes

Lève une exception dans le thread appelant.

Pour plus d’informations, consultez la fonction Windows `RaiseException`.

## <a name="requirements"></a>Spécifications

**En-tête :** Internal. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)
