---
title: Ftmbase::GetMarshalSizeMax, méthode | Documents Microsoft
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
ms.openlocfilehash: 5a298e63bc67dadf33a5e653d0eecf165a530d82
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873792"
---
# <a name="ftmbasegetmarshalsizemax-method"></a>FtmBase::GetMarshalSizeMax, méthode
Obtenir la limite supérieure du nombre d’octets nécessaire pour marshaler le pointeur d’interface spécifié sur l’objet spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHODIMP GetMarshalSizeMax(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out DWORD *pSize  
) override;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `riid`  
 Référence à l’identificateur de l’interface pour être marshalés.  
  
 `pv`  
 Pointeur d’interface pour être marshalés ; peut être NULL.  
  
 `dwDestContext`  
 Contexte de destination où l’interface spécifiée doit être démarshalée.  
  
 Spécifiez une ou plusieurs valeurs d’énumération MSHCTX.  
  
 Actuellement, unmarshaling peut se produire dans un autre cloisonnement du processus actuel (MSHCTX_INPROC) ou dans un autre processus sur le même ordinateur que le processus en cours (MSHCTX_LOCAL).  
  
 `pvDestContext`  
 Réservé à un usage ultérieur ; doit être NULL.  
  
 `mshlflags`  
 Indicateur qui indique si les données doivent être marshalées doit être transmis au processus client, le cas par défaut, ou écrites sur une table globale, où il peut être récupéré par plusieurs clients. Spécifiez une ou plusieurs valeurs d’énumération MSHLFLAGS.  
  
 `pSize`  
 Lorsque cette opération se termine, pointeur vers la limite supérieure de la quantité de données à écrire dans le flux de marshaling.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, E_FAIL ou sur E_NOINTERFACE.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** ftm.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [FtmBase, classe](../windows/ftmbase-class.md)