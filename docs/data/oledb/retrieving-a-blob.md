---
title: Récupération d'un BLOB
ms.date: 10/24/2018
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
ms.openlocfilehash: 352841595e8b197407ccb52a22c8b0502d314c98
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509507"
---
# <a name="retrieving-a-blob"></a>Récupération d'un BLOB

Vous pouvez récupérer un objet BLOB (Binary Large Object) de différentes façons. Vous pouvez utiliser `DBTYPE_BYTES` pour récupérer l’objet blob sous la forme d’une séquence d’octets ou utiliser une interface comme `ISequentialStream` . Pour plus d’informations, consultez [objets BLOB et OLE](/previous-versions/windows/desktop/ms711511(v=vs.85)) dans le **Guide de référence du programmeur OLE DB**.

Le code suivant montre comment récupérer un objet BLOB à l’aide de `ISequentialStream` . La [BLOB_ENTRY](./macros-and-global-functions-for-ole-db-consumer-templates.md#blob_entry) macro vous permet de spécifier l’interface et les indicateurs utilisés pour l’interface. Après l’ouverture de la table, le code appelle à `Read` plusieurs reprises `ISequentialStream` pour lire les octets de l’objet BLOB. Le code appelle la `Release` méthode de suppression du pointeur d’interface avant `MoveNext` d’appeler pour récupérer l’enregistrement suivant.

```cpp
class CCategories
{
public:
   ISequentialStream* pPicture;

BEGIN_COLUMN_MAP(CCategories)
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)
END_COLUMN_MAP()
};
```

Ensuite, utilisé par le code suivant :

```cpp
CTable<CAccessor<CCategories>> categories;
ULONG cb;
BYTE myBuffer[65536];

categories.Open(session, "Categories");

while (categories.MoveNext() == S_OK)
{
   do
   {
      categories.pPicture->Read(myBuffer, 65536, &cb);
      // Do something with the buffer
   } while (cb > 0);
   categories.pPicture->Release();
}
```

Pour plus d’informations sur les macros qui gèrent les données BLOB, consultez **macros de mappage de colonnes** dans les [macros et fonctions globales pour OLE DB les modèles de consommateur](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)<br/>
[Macros et fonctions globales pour les modèles de consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
