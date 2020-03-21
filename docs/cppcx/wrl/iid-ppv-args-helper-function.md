---
title: IID_PPV_ARGS_Helper (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: 68dbd0b5b2e9d4fc04821a7e7e0193840b55e312
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077128"
---
# <a name="iid_ppv_args_helper-function"></a>IID_PPV_ARGS_Helper (fonction)

Vérifie que le type de l’argument spécifié est dérivé de l’interface `IUnknown`.

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

## <a name="return-value"></a>Valeur de retour

L’argument *pp* est casté en pointeur vers un pointeur vers **void**.

## <a name="remarks"></a>Notes

Une erreur de compilation est générée si le paramètre de modèle *T* ne dérive pas de `IUnknown`.

## <a name="requirements"></a>Spécifications

**En-tête :** client.h
