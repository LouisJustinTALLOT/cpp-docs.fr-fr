---
title: MakeAndInitialize, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
ms.openlocfilehash: 28d9e586a766a131e7ab6280859845810c1d9814
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213796"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize, fonction

Initialise la classe de Windows Runtime spécifiée. Utilisez cette fonction pour instancier un composant qui est défini dans le même module.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename T,
    typename I,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9>
HRESULT MakeAndInitialize(
    _Outptr_result_nullonfailure_ I** ppvObject,
    TArg1 &&arg1,
    TArg2 &&arg2,
    TArg3 &&arg3,
    TArg4 &&arg4,
    TArg5 &&arg5,
    TArg6 &&arg6,
    TArg7 &&arg7,
    TArg8 &&arg8,
    TArg9 &&arg9) throw()
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe spécifiée par l’utilisateur qui hérite de `WRL::RuntimeClass`.

*TArg1*<br/>
Type d’argument 1 passé à la classe d’exécution spécifiée.

*TArg2*<br/>
Type d’argument 2 passé à la classe d’exécution spécifiée.

*TArg3*<br/>
Type d’argument 3 passé à la classe d’exécution spécifiée.

*TArg4*<br/>
Type d’argument 4 passé à la classe d’exécution spécifiée.

*TArg5*<br/>
Type d’argument 5 passé à la classe d’exécution spécifiée.

*TArg6*<br/>
Type d’argument 6 qui est passé à la classe d’exécution spécifiée.

*TArg7*<br/>
Type d’argument 7 passé à la classe d’exécution spécifiée.

*TArg8*<br/>
Type d’argument 8 passé à la classe d’exécution spécifiée.

*TArg9*<br/>
Type d’argument 9 passé à la classe d’exécution spécifiée.

*Arg1*<br/>
Argument 1 passé à la classe d’exécution spécifiée.

*Arg2*<br/>
Argument 2 passé à la classe d’exécution spécifiée.

*Arg3*<br/>
Argument 3 passé à la classe d’exécution spécifiée.

*Arg4*<br/>
Argument 4 passé à la classe d’exécution spécifiée.

*Arg5*<br/>
Argument 5 qui est passé à la classe d’exécution spécifiée.

*arg6*<br/>
Argument 6 qui est passé à la classe d’exécution spécifiée.

*arg7*<br/>
Argument 7 passé à la classe d’exécution spécifiée.

*arg8*<br/>
Argument 8 qui est passé à la classe d’exécution spécifiée.

*arg9*<br/>
Argument 9 passé à la classe d’exécution spécifiée.

## <a name="return-value"></a>Valeur de retour

Valeur HRESULT.

## <a name="remarks"></a>Notes

Consultez [Comment : instancier des composants WRL directement](how-to-instantiate-wrl-components-directly.md) pour découvrir les différences entre cette fonction et [Microsoft :: WRL :: Make](make-function.md), et pour obtenir un exemple.

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)
