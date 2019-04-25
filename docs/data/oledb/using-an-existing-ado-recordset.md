---
title: Utilisation d'un recordset ADO existant
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: eb558bb319bb5ddb61d0383846099d708f99c627
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389006"
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