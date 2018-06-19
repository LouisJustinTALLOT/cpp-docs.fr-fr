---
title: Ftmbase::UnmarshalInterface, méthode | Documents Microsoft
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
ms.openlocfilehash: 964ce5cc33b51c54446874522317814279cdd960
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877717"
---
# <a name="ftmbaseunmarshalinterface-method"></a>FtmBase::UnmarshalInterface, méthode
Initialise un proxy nouvellement créé et retourne un pointeur d’interface au proxy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHODIMP UnmarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __deref_out void **ppv  
) override;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pStm`  
 Pointeur vers le flux à partir duquel le pointeur d’interface doit être démarshalée.  
  
 `riid`  
 Référence à l’identificateur de l’interface sont démarshalées.  
  
 `ppv`  
 Lorsque cette opération est terminée, l’adresse d’une variable pointeur qui reçoit le pointeur d’interface demandé dans `riid`. Si cette opération est réussie, *`ppv` contient le pointeur d’interface demandé de l’interface sont démarshalées.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, d’E_NOINTERFACE ou E_FAIL.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** ftm.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [FtmBase, classe](../windows/ftmbase-class.md)