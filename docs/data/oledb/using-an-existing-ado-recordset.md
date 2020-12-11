---
description: 'En savoir plus sur : utilisation d’un jeu d’enregistrements ADO existant'
title: Utilisation d'un recordset ADO existant
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: 4b5c3b5f621f3cbdba6f2d42fd95436495a5661e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160946"
---
# <a name="using-an-existing-ado-recordset"></a>Utilisation d'un recordset ADO existant

Pour mélanger OLE DB modèles de consommateur et ADO (Active Data Objects), utilisez ADO pour ouvrir un Recordset (correspondant à un ensemble de lignes dans les modèles de consommateur OLE DB). Lorsque vous disposez d’un jeu d’enregistrements, procédez comme suit pour vous connecter à un ensemble de lignes OLE DB :

1. Appelez `QueryInterface` pour les `IRowset` `IAccessor` pointeurs et.

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk* pointe vers l' `IUnknown` objet de l’objet Recordset ADO.

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
