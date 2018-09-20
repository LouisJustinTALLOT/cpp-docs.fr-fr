---
title: Makeandinitialize, fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
dev_langs:
- C++
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05f577ce8845b85cdb3a263aaea1e8c2cdb0f240
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409179"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize, fonction

Initialise la classe Windows Runtime spécifiée. Utilisez cette fonction pour instancier un composant qui est défini dans le même module.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T, typename I,
typename TArg1,
typename TArg2,
typename TArg3,
typename TArg4,
typename TArg5,
typename TArg6,
typename TArg7,
typename TArg8,
typename TArg9> HRESULT MakeAndInitialize(_Outptr_result_nullonfailure_ I** ppvObject, TArg1 &&arg1, TArg2 &&arg2, TArg3 &&arg3, TArg4 &&arg4, TArg5 &&arg5, TArg6 &&arg6, TArg7 &&arg7, TArg8 &&arg8, TArg9 &&arg9) throw()  
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

*Arg2*<br/>
Argument 2 qui est passé à la classe runtime spécifié.

*Arg3*<br/>
Argument 3 qui est passé à la classe runtime spécifié.

*Arg4*<br/>
Argument 4 qui est passé à la classe runtime spécifié.

*Arg5*<br/>
Argument 5 qui est passé à la classe runtime spécifié.

*Arg6*<br/>
Argument 6 est passée à la classe runtime spécifié.

*Arg7*<br/>
Argument 7 qui est passé à la classe runtime spécifié.

*Arg8*<br/>
Argument 8 qui est passé à la classe runtime spécifié.

*Arg9*<br/>
Argument 9 qui est passé à la classe runtime spécifié.

## <a name="return-value"></a>Valeur de retour

Valeur HRESULT.

## <a name="remarks"></a>Notes

Consultez [Comment : instancier directement les composants de WRL](../windows/how-to-instantiate-wrl-components-directly.md) pour découvrir les différences entre cette fonction et [Microsoft::wrl :: Make](../windows/make-function.md)et pour obtenir un exemple.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)