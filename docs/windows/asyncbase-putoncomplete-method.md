---
title: Asyncbase::putoncomplete, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::PutOnComplete
dev_langs:
- C++
helpviewer_keywords:
- PutOnComplete method
ms.assetid: 1c469ff9-b2df-4637-bf05-01a617043149
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c62119b87183fe6a60c0ed4d987cbd12788d8a0d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602684"
---
# <a name="asyncbaseputoncomplete-method"></a>AsyncBase::PutOnComplete, méthode

Définit l’adresse du Gestionnaire d’événements de saisie semi-automatique à la valeur spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Paramètres

*completeHandler*  
L’adresse à laquelle le Gestionnaire d’événements de saisie semi-automatique est défini.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[AsyncBase, classe](../windows/asyncbase-class.md)