---
title: Ftmbase::GetUnmarshalClass, méthode | Documents Microsoft
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
ms.openlocfilehash: 09afd9f977dbc779eb1dc10e9553d2ca88538fcc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873301"
---
# <a name="ftmbasegetunmarshalclass-method"></a>FtmBase::GetUnmarshalClass, méthode
Obtient le CLSID COM utilise pour rechercher la DLL qui contient le code pour le proxy correspondant. COM charge cette DLL pour créer une instance non initialisée du proxy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHODIMP GetUnmarshalClass(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out CLSID *pCid  
) override;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `riid`  
 Référence à l’identificateur de l’interface pour être marshalés.  
  
 `pv`  
 Pointeur vers l’interface pour être marshalés ; peut d’être NULL si l’appelant n’a pas un pointeur vers l’interface souhaitée.  
  
 `dwDestContext`  
 Contexte de destination où l’interface spécifiée doit être démarshalée.  
  
 Spécifiez une ou plusieurs valeurs d’énumération MSHCTX.  
  
 Unmarshaling peut se produire dans un autre cloisonnement du processus actuel (MSHCTX_INPROC) ou dans un autre processus sur le même ordinateur que le processus en cours (MSHCTX_LOCAL).  
  
 `pvDestContext`  
 Réservé à un usage ultérieur ; doit être NULL.  
  
 `mshlflags`  
 Lorsque cette opération se termine, pointeur vers le CLSID à utiliser pour créer un proxy dans le processus client.  
  
 `pCid`  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, S_FALSE.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** ftm.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [FtmBase, classe](../windows/ftmbase-class.md)