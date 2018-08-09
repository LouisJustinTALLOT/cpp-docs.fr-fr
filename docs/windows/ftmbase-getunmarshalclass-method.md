---
title: Ftmbase::GetUnmarshalClass, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
dev_langs:
- C++
helpviewer_keywords:
- GetUnmarshalClass method
ms.assetid: 535fc539-5b97-4967-b158-f7568f13d341
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 167ad8537a11a0118c15b588b353f33775b5ab3a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644997"
---
# <a name="ftmbasegetunmarshalclass-method"></a>FtmBase::GetUnmarshalClass, méthode
Obtient le CLSID COM utilise pour localiser la DLL contenant le code pour le proxy correspondant. COM charge cette DLL pour créer une instance non initialisée du proxy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHODIMP GetUnmarshalClass(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out CLSID *pCid  
) override;  
```  
  
### <a name="parameters"></a>Paramètres  
 *riid*  
 Référence à l’identificateur de l’interface doivent être marshalées.  
  
 *PV*  
 Pointeur vers l’interface doivent être marshalées ; peut d’être NULL si l’appelant n’a pas un pointeur vers l’interface souhaitée.  
  
 *dwDestContext*  
 Contexte de destination où l’interface spécifiée doit être marshalé.  
  
 Spécifiez une ou plusieurs valeurs d’énumération MSHCTX.  
  
 Unmarshaling peut se produire dans un autre cloisonnement du processus en cours (MSHCTX_INPROC) ou dans un autre processus sur le même ordinateur que le processus en cours (MSHCTX_LOCAL).  
  
 *pvDestContext*  
 Réservé pour une utilisation ultérieure ; doit être NULL.  
  
 *mshlflags*  
 Lorsque cette opération se termine, pointeur vers le CLSID à utiliser pour créer un proxy dans le processus client.  
  
 *pCid*  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, S_FALSE.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ftm.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [FtmBase, classe](../windows/ftmbase-class.md)