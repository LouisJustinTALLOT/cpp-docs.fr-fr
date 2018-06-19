---
title: Ftmbase::createglobalinterfacetable, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable
dev_langs:
- C++
helpviewer_keywords:
- CreateGlobalInterfaceTable method
ms.assetid: bb82a0c5-22b9-4844-9204-7922033d8b07
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6b17749d5f20007e05f181de8f4e069d3fc736f0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872391"
---
# <a name="ftmbasecreateglobalinterfacetable-method"></a>FtmBase::CreateGlobalInterfaceTable, méthode
Crée un tableau global d’interface (GIT).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static HRESULT CreateGlobalInterfaceTable(  
   __out IGlobalInterfaceTable **git  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `git`  
 Lorsque cette opération est terminée, un pointeur vers un tableau global d’interface.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez la rubrique « IGlobalInterfaceTable » dans la sous-rubrique « Interfaces COM » de la rubrique « Référence COM » dans MSDN Library.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** ftm.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [FtmBase, classe](../windows/ftmbase-class.md)