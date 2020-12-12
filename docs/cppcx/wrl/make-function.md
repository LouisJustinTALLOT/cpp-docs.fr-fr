---
description: 'En savoir plus sur : Make, fonction'
title: Make, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
ms.openlocfilehash: bb83c6c163440f911bc625a8646d1758442b25f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298901"
---
# <a name="make-function"></a>Make, fonction

Initialise la classe de Windows Runtime spécifiée. Utilisez cette fonction pour instancier un composant qui est défini dans le même module.

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
Classe spécifiée par l’utilisateur qui hérite de `WRL::RuntimeClass` .

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

*arg1*<br/>
Argument 1 passé à la classe d’exécution spécifiée.

*arg2*<br/>
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

## <a name="return-value"></a>Valeur renvoyée

`ComPtr<T>`Objet en cas de réussite ; sinon, **`nullptr`** .

## <a name="remarks"></a>Notes

Consultez [Comment : instancier des composants WRL directement](how-to-instantiate-wrl-components-directly.md) pour connaître les différences entre cette fonction et [Microsoft :: WRL ::D étails :: MakeAndInitialize](makeandinitialize-function.md), et pour obtenir un exemple.

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
