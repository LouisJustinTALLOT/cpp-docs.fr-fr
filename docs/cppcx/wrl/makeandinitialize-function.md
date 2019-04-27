---
title: MakeAndInitialize, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
ms.openlocfilehash: 14ae5117194748748ceecf97ac83fc8813bba2d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223100"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize, fonction

Initialise la classe Windows Runtime spécifiée. Utilisez cette fonction pour instancier un composant qui est défini dans le même module.

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
Une classe spécifiée par l’utilisateur qui hérite de `WRL::RuntimeClass`.

*TArg1*<br/>
Type d’argument 1 qui est passé à la classe runtime spécifié.

*TArg2*<br/>
Type d’argument 2 qui est passé à la classe runtime spécifié.

*TArg3*<br/>
Type d’argument 3 est passée à la classe runtime spécifié.

*TArg4*<br/>
Type d’argument 4 qui est passé à la classe runtime spécifié.

*TArg5*<br/>
Type d’argument 5 est passé à la classe runtime spécifié.

*TArg6*<br/>
Type d’argument 6 est passée à la classe runtime spécifié.

*TArg7*<br/>
Type d’argument 7 est passé à la classe runtime spécifié.

*TArg8*<br/>
Type d’argument 8 est passé à la classe runtime spécifié.

*TArg9*<br/>
Type d’argument 9 est passé à la classe runtime spécifié.

*arg1*<br/>
Argument 1 qui est passé à la classe runtime spécifié.

*arg2*<br/>
Argument 2 qui est passé à la classe runtime spécifié.

*arg3*<br/>
Argument 3 qui est passé à la classe runtime spécifié.

*arg4*<br/>
Argument 4 qui est passé à la classe runtime spécifié.

*arg5*<br/>
Argument 5 qui est passé à la classe runtime spécifié.

*arg6*<br/>
Argument 6 est passée à la classe runtime spécifié.

*arg7*<br/>
Argument 7 qui est passé à la classe runtime spécifié.

*arg8*<br/>
Argument 8 qui est passé à la classe runtime spécifié.

*arg9*<br/>
Argument 9 qui est passé à la classe runtime spécifié.

## <a name="return-value"></a>Valeur de retour

Valeur HRESULT.

## <a name="remarks"></a>Notes

Voir [Guide pratique pour Instancier les composants WRL directement](how-to-instantiate-wrl-components-directly.md) pour découvrir les différences entre cette fonction et [Microsoft::wrl :: Make](make-function.md)et pour obtenir un exemple.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)