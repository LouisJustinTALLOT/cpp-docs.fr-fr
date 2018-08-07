---
title: Ftmbase::MarshalInterface, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- MarshalInterface method
ms.assetid: fc8421b4-06e4-4925-b908-c285fe4790d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ff0c1a5e41dfe46f2d88aeeb3093dbc9ee4d4005
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570055"
---
# <a name="ftmbasemarshalinterface-method"></a>FtmBase::MarshalInterface, méthode
Écrit dans un flux les données requises pour initialiser l’objet proxy dans un processus client.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHODIMP MarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags  
) override;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pStm*  
 Pointeur vers le flux à utiliser pendant le marshaling.  
  
 *riid*  
 Référence à l’identificateur de l’interface doivent être marshalées. Cette interface doit être dérivée du `IUnknown` interface.  
  
 *PV*  
 Pointeur vers le pointeur d’interface doivent être marshalées ; peut d’être NULL si l’appelant n’a pas un pointeur vers l’interface souhaitée.  
  
 *dwDestContext*  
 Contexte de destination où l’interface spécifiée doit être marshalé.  
  
 Spécifiez une ou plusieurs valeurs d’énumération MSHCTX.  
  
 Unmarshaling peut se produire dans un autre cloisonnement du processus en cours (MSHCTX_INPROC) ou dans un autre processus sur le même ordinateur que le processus en cours (MSHCTX_LOCAL).  
  
 *pvDestContext*  
 Réservé pour une future utilisation ; doit être nul.  
  
 *mshlflags*  
 Spécifie si les données doivent être marshalées doit être transmise au processus client, le cas par défaut, ou écrites dans une table globale, où il peut être extrait par plusieurs clients.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Le pointeur d’interface a été marshalé avec succès.  
  
 E_NOINTERFACE  
 L’interface spécifiée n’est pas pris en charge.  
  
 STG_E_MEDIUMFULL  
 Le flux de données est plein.  
  
 E_FAIL  
 L'opération a échoué.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ftm.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [FtmBase, classe](../windows/ftmbase-class.md)