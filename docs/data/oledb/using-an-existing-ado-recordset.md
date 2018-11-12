---
title: Utilisation d'un recordset ADO existant
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: 62e56b818a766bf3b7efddf9243ffd47ad2cb46f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610598"
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