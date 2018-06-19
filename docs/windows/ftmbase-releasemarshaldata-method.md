---
title: Ftmbase::releasemarshaldata, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData
dev_langs:
- C++
helpviewer_keywords:
- ReleaseMarshalData method
ms.assetid: a94f9940-183a-4fde-8504-d223f346a0a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5d56bc92e11d458a1872975f5a81a19c96566d59
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873649"
---
# <a name="ftmbasereleasemarshaldata-method"></a>FtmBase::ReleaseMarshalData, méthode
Détruit un paquet de données marshalé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHODIMP ReleaseMarshalData(  
   __in IStream *pStm  
) override;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pStm`  
 Pointeur vers un flux qui contient le paquet de données d’être détruites.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** ftm.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [FtmBase, classe](../windows/ftmbase-class.md)