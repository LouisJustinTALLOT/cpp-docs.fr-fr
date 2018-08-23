---
title: Ftmbase::UnmarshalInterface, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- UnmarshalInterface method
ms.assetid: 6850a621-e9a6-4001-bc1e-bd5d1b121adc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ef462ae884aad4160ffbae1883485ac7e06d3aa5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610699"
---
# <a name="ftmbaseunmarshalinterface-method"></a>FtmBase::UnmarshalInterface, méthode

Initialise un proxy nouvellement créé et retourne un pointeur d’interface au proxy.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>Paramètres

*pStm*  
Pointeur vers le flux à partir duquel le pointeur d’interface doit être marshalé.

*riid*  
Référence à l’identificateur de l’interface pour être marshalé.

*PPV*  
Lorsque cette opération se termine, l’adresse d’une variable pointeur qui reçoit le pointeur d’interface demandé dans *riid*. Si cette opération est réussie, **ppv* contient le pointeur d’interface requis de l’interface pour être marshalé.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_NOINTERFACE ou E_FAIL.

## <a name="requirements"></a>Configuration requise

**En-tête :** ftm.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[FtmBase, classe](../windows/ftmbase-class.md)