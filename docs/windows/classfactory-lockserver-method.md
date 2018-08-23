---
title: ClassFactory::lockserver, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5ea76974359da2002178a342ab7d9b5523c52889
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584136"
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer, méthode

Incrémente ou décrémente le nombre de sous-jacent objets qui sont suivis par le **ClassFactory** objet.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>Paramètres

*Troupeau*  
**true** pour incrémenter le nombre d’objets suivis. **false** pour décrémenter le nombre d’objets suivis.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_FAIL.

## <a name="remarks"></a>Notes

**ClassFactory** effectue le suivi des objets dans une instance sous-jacente de la [Module](../windows/module-class.md) classe.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[ClassFactory, classe](../windows/classfactory-class.md)