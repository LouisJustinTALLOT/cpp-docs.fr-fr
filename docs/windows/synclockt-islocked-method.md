---
title: Synclockt::IsLocked, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
dev_langs:
- C++
helpviewer_keywords:
- IsLocked method
ms.assetid: a81fea43-f99a-4708-812a-7fd6af500d3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ca4391539e4f6987431e8b9b036053db02218007
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593053"
---
# <a name="synclocktislocked-method"></a>SyncLockT::IsLocked, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
bool IsLocked() const;
```

## <a name="return-value"></a>Valeur de retour

**true** si le **SyncLockT** objet est verrouillé ; sinon, **false**.

## <a name="remarks"></a>Notes

Indique si l’actuel **SyncLockT** objet possède une ressource, c'est-à-dire, le **SyncLockT** objet est *verrouillé*.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Voir aussi

[SyncLockT, classe](../windows/synclockt-class.md)