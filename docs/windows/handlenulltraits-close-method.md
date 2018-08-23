---
title: Handlenulltraits::Close, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 6fb2fa0d-df20-45dc-856f-f78497f8bdf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 155fb5a07f747e4107e630b0db65d321ee726e2c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602214"
---
# <a name="handlenulltraitsclose-method"></a>HANDLENullTraits::Close, méthode

Ferme le handle spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>Paramètres

*h*  
Le handle à fermer.

## <a name="return-value"></a>Valeur de retour

**true** si gérer *h* fermé avec succès ; sinon, **false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>Voir aussi

[HANDLENullTraits, structure](../windows/handlenulltraits-structure.md)