---
title: Ftmbase::GetMarshalSizeMax, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
dev_langs:
- C++
helpviewer_keywords:
- GetMarshalSizeMax method
ms.assetid: b416b1bf-c73e-45d5-abb8-04921c1a0c94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c7976d0ea22a0bf6f59b020f892d407c4721b9a7
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652355"
---
# <a name="ftmbasegetmarshalsizemax-method"></a>FtmBase::GetMarshalSizeMax, méthode
Obtenir la limite supérieure sur le nombre d’octets nécessaires pour marshaler le pointeur d’interface spécifié sur l’objet spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHODIMP GetMarshalSizeMax(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out DWORD *pSize  
) override;  
```  
  
### <a name="parameters"></a>Paramètres  
 *riid*  
 Référence à l’identificateur de l’interface doivent être marshalées.  
  
 *PV*  
 Pointeur d’interface doivent être marshalées ; peut être NULL.  
  
 *dwDestContext*  
 Contexte de destination où l’interface spécifiée doit être marshalé.  
  
 Spécifiez une ou plusieurs valeurs d’énumération MSHCTX.  
  
 Actuellement, unmarshaling peut se produire dans un autre cloisonnement du processus en cours (MSHCTX_INPROC) ou dans un autre processus sur le même ordinateur que le processus en cours (MSHCTX_LOCAL).  
  
 *pvDestContext*  
 Réservé pour une utilisation ultérieure ; doit être NULL.  
  
 *mshlflags*  
 Indicateur qui spécifie si les données doivent être marshalées doit être transmise au processus client, le cas par défaut, ou écrites dans une table globale, où il peut être extrait par plusieurs clients. Spécifiez une ou plusieurs valeurs d’énumération MSHLFLAGS.  
  
 *pSize*  
 Lorsque cette opération se termine, pointeur vers la limite supérieure de la quantité de données à écrire dans le flux de marshaling.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, E_FAIL ou E_NOINTERFACE.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ftm.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [FtmBase, classe](../windows/ftmbase-class.md)