---
title: Asyncbase::get_errorcode, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- get_ErrorCode method
ms.assetid: 50b4f8a2-9a21-4ea0-bb5d-7ff524d62aea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8e1e9355b6063ae67a40373828f394e3e6334f7d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613420"
---
# <a name="asyncbasegeterrorcode-method"></a>AsyncBase::get_ErrorCode, méthode

Récupère le code d’erreur pour l’opération asynchrone actuelle.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>Paramètres

*code d’erreur*  
L’emplacement où se trouve le code d’erreur actuel.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL si l’opération asynchrone en cours est fermée.

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[AsyncBase, classe](../windows/asyncbase-class.md)