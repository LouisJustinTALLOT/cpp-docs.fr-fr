---
title: Ftmbase::disconnectobject, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
dev_langs:
- C++
helpviewer_keywords:
- DisconnectObject method
ms.assetid: 33253eec-3a65-4e72-8525-0249245a4790
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b467162d2f5cc5b04bc43a6d31019eb08e17e750
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595404"
---
# <a name="ftmbasedisconnectobject-method"></a>FtmBase::DisconnectObject, méthode

Force libère toutes les connexions externes à un objet. Serveur de l’objet appelle l’implémentation de l’objet de cette méthode avant d’arrêter.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>Paramètres

*dwReserved*  
Réservé pour une future utilisation ; doit être nul.

## <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="requirements"></a>Configuration requise

**En-tête :** ftm.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[FtmBase, classe](../windows/ftmbase-class.md)