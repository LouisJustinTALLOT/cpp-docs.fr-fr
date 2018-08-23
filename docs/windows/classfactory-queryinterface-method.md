---
title: ClassFactory::QueryInterface, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method
ms.assetid: 9593881f-4585-4d70-8ca6-b328918d4d6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 80c369d5ccbcc9f83d0f3ff90769a3df5d7ec177
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603410"
---
# <a name="classfactoryqueryinterface-method"></a>ClassFactory::QueryInterface, méthode

Récupère un pointeur vers l’interface spécifiée par le paramètre.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Paramètres

*riid*  
ID d’interface.

*ppvObject*  
Lorsque cette opération se termine, un pointeur vers l’interface spécifiée par le paramètre *riid*.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[ClassFactory, classe](../windows/classfactory-class.md)