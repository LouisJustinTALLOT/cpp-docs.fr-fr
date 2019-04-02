---
title: IID_PPV_ARGS_Helper (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: 5ef4dd6c9db2d19e0c8a4143c5b4ed3f0ac75f6a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784244"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper (fonction)

Vérifie que le type de l’argument spécifié dérive le `IUnknown` interface.

> [!IMPORTANT]
> Cette spécialisation de modèle prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code. Utilisez [IID_PPV_ARGS](/windows/desktop/api/combaseapi/nf-combaseapi-iid_ppv_args) à la place.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type d’argument *pp*.

*pp*<br/>
Pointeur doublement indirect.

## <a name="return-value"></a>Valeur de retour

Argument *pp* à un pointeur-à-un-pointeur pour **void**.

## <a name="remarks"></a>Notes

Une erreur de compilation est générée si le paramètre de modèle *T* ne dérive pas de `IUnknown`.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

