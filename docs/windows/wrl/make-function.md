---
title: Make, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
ms.openlocfilehash: cab261724399107c57b36a9020906a96697f7eca
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336060"
---
# <a name="make-function"></a>Make, fonction

Initialise la classe Windows Runtime spécifiée. Utilisez cette fonction pour instancier un composant qui est défini dans le même module.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8,
   typename TArg9
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8,
   TArg9 &&arg9
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3
);
template <
   typename T,
   typename TArg1,
   typename TArg2
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2
);
template <
   typename T,
   typename TArg1
>
ComPtr<T> Make(
   TArg1 &&arg1
);
template <
   typename T
>
ComPtr<T> Make();
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

Un `ComPtr<T>` objet en cas de réussite ; sinon, `nullptr`.

## <a name="remarks"></a>Notes

Voir [Guide pratique pour Instancier les composants WRL directement](how-to-instantiate-wrl-components-directly.md) pour découvrir les différences entre cette fonction et [Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md)et pour obtenir un exemple.

## <a name="requirements"></a>Spécifications

**En-tête :** implements.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)