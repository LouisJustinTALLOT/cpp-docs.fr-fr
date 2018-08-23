---
title: Asyncbase::checkvalidstateforresultscall, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
dev_langs:
- C++
helpviewer_keywords:
- CheckValidStateForResultsCall method
ms.assetid: 87ca6805-bff1-4063-b855-6dd26132deff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 398f46d5f8eb15d961d80b9a7a20b758fffd09c3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584234"
---
# <a name="asyncbasecheckvalidstateforresultscall-method"></a>AsyncBase::CheckValidStateForResultsCall, méthode

Teste si les résultats d’une opération asynchrone peuvent être collectées dans l’état asynchrone actuelle.

## <a name="syntax"></a>Syntaxe

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

## <a name="return-value"></a>Valeur de retour

S_OK si les résultats peuvent être collectés ; Sinon, E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[AsyncBase, classe](../windows/asyncbase-class.md)