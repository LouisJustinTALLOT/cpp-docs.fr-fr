---
title: CDataConnection::OpenNewSession | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
dev_langs:
- C++
helpviewer_keywords:
- OpenNewSession method
ms.assetid: 0a70e573-9498-4ca7-b524-45666dc7b0a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f20f66ec6cc494c14e99c50de4824ba68d27264d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094320"
---
# <a name="cdataconnectionopennewsession"></a>CDataConnection::OpenNewSession
Ouvre une nouvelle session à l’aide de la source de données de l’objet de connexion en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OpenNewSession(CSession & session) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `session`  
 [entrée/sortie] Une référence à l’objet de la nouvelle session.  
  
 **Remarques**  
 La nouvelle session utilise un objet de source de données de contenu de l’objet de connexion en cours en tant que son parent et peut accéder à tous les mêmes informations que la source de données.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDataConnection, classe](../../data/oledb/cdataconnection-class.md)