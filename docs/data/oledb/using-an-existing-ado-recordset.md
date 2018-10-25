---
title: À l’aide d’un Recordset ADO existant | Microsoft Docs
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
ms.openlocfilehash: 1433b51a6dfe6f558b98360812e694d42ebfb9f5
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50051951"
---
# <a name="using-an-existing-ado-recordset"></a>Utilisation d'un recordset ADO existant

Pour combiner des modèles du consommateur OLE DB et Active Data Objects (ADO), utilisez ADO pour ouvrir un jeu d’enregistrements (correspondant à un ensemble de lignes dans les modèles du consommateur OLE DB). Lorsque vous avez un jeu d’enregistrements, procédez comme suit pour vous connecter à un ensemble de lignes OLE DB :

1. Appelez `QueryInterface` pour le `IRowset` et `IAccessor` des pointeurs.

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk* pointe vers le `IUnknown` objet de l’objet recordset ADO.

1. Attachez l’accesseur et un ensemble de lignes à leurs classes de modèles du consommateur OLE DB appropriés.

    ```cpp
    CRowset rs;
    CAccessor accessor;

    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>
    rs.SetAccessor(accessor);
    ```

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)