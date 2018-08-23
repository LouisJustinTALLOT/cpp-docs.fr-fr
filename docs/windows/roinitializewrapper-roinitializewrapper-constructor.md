---
title: Roinitializewrapper::roinitializewrapper, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: c6f7fb07-14af-4574-9135-cea164607f30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 528c66da24c4cbf6c22af5b1b5f8dd3afffff64f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604644"
---
# <a name="roinitializewrapperroinitializewrapper-constructor"></a>RoInitializeWrapper::RoInitializeWrapper, constructeur

Initialise une nouvelle instance de la **RoInitializeWrapper** classe.

## <a name="syntax"></a>Syntaxe

```cpp
RoInitializeWrapper(   RO_INIT_TYPE flags)  
```

### <a name="parameters"></a>Paramètres

*flags*  
Une des énumérations RO_INIT_TYPE, qui spécifie la prise en charge fournie par le Runtime de Windows.

## <a name="remarks"></a>Notes

Le **RoInitializeWrapper** classe appelle `Windows::Foundation::Initialize(flags)`.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HandleT, classe](../windows/handlet-class.md)