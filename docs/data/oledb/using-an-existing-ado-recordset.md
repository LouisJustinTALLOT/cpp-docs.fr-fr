---
title: Utilisation d'un recordset ADO existant
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: 48f6eb3bac34b37f495b9492e19b4197ed69cca3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209350"
---
# <a name="using-an-existing-ado-recordset"></a>Utilisation d'un recordset ADO existant

Pour mélanger OLE DB modèles de consommateur et ADO (Active Data Objects), utilisez ADO pour ouvrir un Recordset (correspondant à un ensemble de lignes dans les modèles de consommateur OLE DB). Lorsque vous disposez d’un jeu d’enregistrements, procédez comme suit pour vous connecter à un ensemble de lignes OLE DB :

1. Appelez `QueryInterface` pour les pointeurs de `IRowset` et de `IAccessor`.

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk* pointe vers l’objet `IUnknown` de l’objet Recordset ADO.

1. Attachez l’accesseur et l’ensemble de lignes à leurs classes de modèle de consommateur OLE DB appropriées.

    ```cpp
    CRowset rs;
    CAccessor accessor;

    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>
    rs.SetAccessor(accessor);
    ```

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)
