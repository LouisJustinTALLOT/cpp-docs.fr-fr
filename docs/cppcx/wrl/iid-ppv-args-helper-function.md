---
description: 'En savoir plus sur : fonction IID_PPV_ARGS_Helper'
title: IID_PPV_ARGS_Helper (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: 7003a3270a6fdb2070055e0059b106f55324c63e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229143"
---
# <a name="iid_ppv_args_helper-function"></a>IID_PPV_ARGS_Helper (fonction)

Vérifie que le type de l’argument spécifié est dérivé de l' `IUnknown` interface.

> [!IMPORTANT]
> Cette spécialisation de modèle prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement à partir de votre code. Utilisez à la place [IID_PPV_ARGS](/windows/win32/api/combaseapi/nf-combaseapi-iid_ppv_args) .

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type d’argument *pp*.

*p*<br/>
Pointeur doublement indirect.

## <a name="return-value"></a>Valeur renvoyée

Argument *pp* casté en pointeur vers un pointeur vers **`void`** .

## <a name="remarks"></a>Notes

Une erreur de compilation est générée si le paramètre de modèle *T* ne dérive pas de `IUnknown` .

## <a name="requirements"></a>Spécifications

**En-tête :** client.h
