---
title: CDataConnection::CDataConnection | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
dev_langs:
- C++
helpviewer_keywords:
- CDataConnection class, constructor
ms.assetid: ac25c9a0-44d3-4083-b13f-76c07772e12d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 267341f88886f3ff94a6b828034e8acbaa2dc0c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093322"
---
# <a name="cdataconnectioncdataconnection"></a>CDataConnection::CDataConnection
Instancie et initialise un `CDataConnection` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      CDataConnection();   

CDataConnection(const CDataConnection &ds);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ds`  
 [in] Une référence à une connexion de données existante.  
  
## <a name="remarks"></a>Notes  
 La première substitution crée un nouveau `CDataConnection` objet avec les paramètres par défaut.  
  
 La deuxième substitution crée un nouveau `CDataConnection` objet avec les paramètres équivalents à l’objet de connexion de données vous spécifiez.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDataConnection, classe](../../data/oledb/cdataconnection-class.md)