---
title: À l’aide d’un Recordset ADO existant | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 36c74ec0d17c296707334930736d0cf237ecfe7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103562"
---
# <a name="using-an-existing-ado-recordset"></a>Utilisation d'un recordset ADO existant
Pour combiner des modèles du consommateur OLE DB et Active Data Objects (ADO), utilisez ADO pour ouvrir un jeu d’enregistrements (correspondant à un ensemble de lignes dans les modèles du consommateur OLE DB). Lorsque vous disposez d’un jeu d’enregistrements, procédez comme suit pour vous connecter à un ensemble de lignes OLE DB :  
  
1.  Appelez `QueryInterface` pour le `IRowset` et `IAccessor` des pointeurs.  
  
    ```  
    IRowset* lpRowset = NULL;  
    IAccessor* lpAccessor = NULL;  
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);  
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);  
    ```  
  
    > [!NOTE]
    >  *lpUnk* pointe vers le **IUnknown** objet de l’ensemble d’enregistrements ADO.  
  
2.  Attachez l’accesseur et un ensemble de lignes à leurs classes de modèles du consommateur OLE DB appropriées.  
  
    ```  
    CRowset rs;  
    CAccessor accessor;  
  
    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor  
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>  
    rs.SetAccessor(accessor);  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des accesseurs](../../data/oledb/using-accessors.md)