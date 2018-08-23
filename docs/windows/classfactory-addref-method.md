---
title: ClassFactory::AddRef, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method
ms.assetid: 5b091785-dea4-42b6-a502-0db5fc7a5a2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aeab6c448818d9d54ca96832a8c7875ebaa97091
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611357"
---
# <a name="classfactoryaddref-method"></a>ClassFactory::AddRef, méthode

Incrémente le décompte de références pour actuel **ClassFactory** objet.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

## <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[ClassFactory, classe](../windows/classfactory-class.md)