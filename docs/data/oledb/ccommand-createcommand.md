---
title: CCommand::CreateCommand | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CCommand.CreateCommand
- CreateCommand
- CCommand::CreateCommand
dev_langs:
- C++
helpviewer_keywords:
- CreateCommand method
ms.assetid: 3652a313-07a1-40ec-82d6-fc7182f2a6f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ea3e83c860688d206fae69462b8cb25fb215d8ec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093785"
---
# <a name="ccommandcreatecommand"></a>CCommand::CreateCommand
Crée une nouvelle commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `session`  
 [in] A `CSession` objet à associer à la nouvelle commande.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard.  
  
## <a name="remarks"></a>Notes  
 Cette méthode crée une commande à l’aide de l’objet de session spécifié.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CCommand, classe](../../data/oledb/ccommand-class.md)