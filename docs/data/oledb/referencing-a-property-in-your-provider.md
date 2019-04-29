---
title: Référencement d'une propriété dans votre fournisseur
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
ms.openlocfilehash: c3e620cd760aa04df7d7d2209ef009a606675276
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282918"
---
# <a name="referencing-a-property-in-your-provider"></a>Référencement d'une propriété dans votre fournisseur

Recherchez le groupe de propriétés et l’ID de propriété pour la propriété qui que vous intéresse. Pour plus d’informations, consultez [propriétés OLE DB](/previous-versions/windows/desktop/ms722734(v=vs.85)) dans le **de référence du programmeur OLE DB**.

L’exemple suivant suppose que vous tentez d’obtenir une propriété à partir de l’ensemble de lignes. Le code pour l’utilisation de la session ou la commande est similaire, mais utilise une interface différente.

Créer un [CDBPropSet](../../data/oledb/cdbpropset-class.md) utilisant le groupe de propriétés comme paramètre au constructeur de l’objet. Exemple :

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
```

Appelez [AddProperty](../../data/oledb/cdbpropset-addproperty.md), en lui passant l’ID de propriété et une valeur à assigner à la propriété. Le type de la valeur dépend de la propriété que vous utilisez.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);

propset.AddProperty(DBPROP_IRowsetChange, true);

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);
```

Utilisez le `IRowset` interface à appeler `GetProperties`. Passez la propriété est définie en tant que paramètre. Voici le code final :

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

[Utilisation des modèles du fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)