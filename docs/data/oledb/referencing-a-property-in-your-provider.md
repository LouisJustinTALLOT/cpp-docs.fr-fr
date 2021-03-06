---
description: 'En savoir plus sur : référencement d’une propriété dans votre fournisseur'
title: Référencement d'une propriété dans votre fournisseur
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
ms.openlocfilehash: dfc3b06820b98477a033b450d42feca52c5c7a72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286616"
---
# <a name="referencing-a-property-in-your-provider"></a>Référencement d'une propriété dans votre fournisseur

Recherchez le groupe de propriétés et l’ID de propriété de la propriété souhaitée. Pour plus d’informations, consultez [OLE DB Properties](/previous-versions/windows/desktop/ms722734(v=vs.85)) dans le **Guide de référence du programmeur OLE DB**.

L’exemple suivant suppose que vous essayez d’obtenir une propriété à partir de l’ensemble de lignes. Le code d’utilisation de la session ou de la commande est similaire, mais utilise une interface différente.

Créez un objet [CDBPropSet](../../data/oledb/cdbpropset-class.md) à l’aide du groupe de propriétés en tant que paramètre du constructeur. Par exemple :

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
```

Appelez [AddProperty](./cdbpropset-class.md#addproperty), en lui transmettant l’ID de propriété et une valeur à assigner à la propriété. Le type de la valeur dépend de la propriété que vous utilisez.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);

propset.AddProperty(DBPROP_IRowsetChange, true);

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);
```

Utilisez l' `IRowset` interface pour appeler `GetProperties` . Transmettez la propriété définie en tant que paramètre. Voici le code final :

```cpp
CAgentRowset<CCustomCommand>* pRowset = (CAgentRowset<CCustomCommand>*) pThis;

CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;

DBPROPIDSET set;
set.AddPropertyID(DBPROP_BOOKMARKS);

DBPROPSET* pPropSet = NULL;
ULONG ulPropSet = 0;

HRESULT hr;

if (spRowsetProps)
   hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);

if (pPropSet)
{
   CComVariant var = pPropSet->rgProperties[0].vValue;
   CoTaskMemFree(pPropSet->rgProperties);
   CoTaskMemFree(pPropSet);

   if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))
   {
      ...  // Use property here
   }
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles de fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
