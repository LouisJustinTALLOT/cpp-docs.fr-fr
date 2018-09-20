---
title: IID_PPV_ARGS_Helper (fonction) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
dev_langs:
- C++
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c3964ce5257a6b2398571c9ed3ba5792b5bd9cca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384479"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper (fonction)

Vérifie que le type de l’argument spécifié dérive le `IUnknown` interface.

> [!IMPORTANT]
> Cette spécialisation de modèle prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code. Utilisez [IID_PPV_ARGS](https://msdn.microsoft.com/library/windows/desktop/ee330727.aspx) à la place.

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

*PP*<br/>
Pointeur doublement indirect.

## <a name="return-value"></a>Valeur de retour

Argument *pp* à un pointeur-à-un-pointeur pour **void**.

## <a name="remarks"></a>Notes

Une erreur de compilation est générée si le paramètre de modèle *T* ne dérive pas de `IUnknown`.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

