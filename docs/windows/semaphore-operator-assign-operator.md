---
title: Semaphore::operator =, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: ea19839f-91f0-4b00-a35b-5728fcba4981
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fbce88be7f7b83c22964438bc4ea7a783754fb63
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609006"
---
# <a name="semaphoreoperator-operator"></a>Semaphore::operator=, opérateur

Déplace le handle spécifié à partir d’un **sémaphore** objet actuel **sémaphore** objet.

## <a name="syntax"></a>Syntaxe

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Paramètres

*h*  
Référence rvalue à un **sémaphore** objet.

## <a name="return-value"></a>Valeur de retour

Une référence à l’actuel **sémaphore** objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi
[Semaphore, classe](../windows/semaphore-class.md)