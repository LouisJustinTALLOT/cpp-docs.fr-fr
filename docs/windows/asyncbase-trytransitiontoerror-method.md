---
title: Asyncbase::trytransitiontoerror, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
dev_langs:
- C++
helpviewer_keywords:
- TryTransitionToError method
ms.assetid: f6d11c25-1ce3-43f9-af1c-97c4dc0f6f0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a6e21f89b5f1beb035b2dd87b2d0ad1d55bc3f8f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418051"
---
# <a name="asyncbasetrytransitiontoerror-method"></a>AsyncBase::TryTransitionToError, méthode

Indique si le code d’erreur spécifié peut modifier l’état d’erreur interne.

## <a name="syntax"></a>Syntaxe

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Paramètres

*Erreur*<br/>
Une erreur HRESULT.

## <a name="return-value"></a>Valeur de retour

**true** si l’état d’erreur interne a été modifié ; sinon, **false**.

## <a name="remarks"></a>Notes

Cette opération modifie l’état d’erreur uniquement si l’état d’erreur est déjà définie à S_OK. Cette opération n’a aucun effet si l’état d’erreur est déjà erreur, annulé, terminé ou fermé.

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[AsyncBase, classe](../windows/asyncbase-class.md)