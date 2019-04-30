---
title: Utilisation des signets
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: 579e67151858904e877a34bf30467e3cb97fe2c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388954"
---
# <a name="using-bookmarks"></a>Utilisation des signets

Avant d’ouvrir l’ensemble de lignes, vous devez indiquer au fournisseur que vous souhaitez utiliser des signets. Pour ce faire, définissez la `DBPROP_BOOKMARKS` propriété **true** dans votre jeu. Le fournisseur récupère les signets en tant que colonne zéro, vous devez donc utiliser la macro spéciale BOOKMARK_ENTRY et `CBookmark` classe si vous utilisez un accesseur statique. `CBookmark` est une classe de modèle où l’argument est la longueur en octets de la mémoire tampon de signet. La longueur de la mémoire tampon requise pour un signet dépend du fournisseur. Si vous utilisez le fournisseur OLE DB pour ODBC, comme indiqué dans l’exemple suivant, la mémoire tampon doit être de 4 octets.

```cpp
class CProducts
{
public:
   CBookmark<4> bookmark;

   BEGIN_COLUMN_MAP(CProducts)
      BOOKMARK_ENTRY(bookmark)
   END_COLUMN_MAP()
};
```

Ensuite, il est utilisé par le code suivant :

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_BOOKMARKS, true);

CTable<CAccessor<CProducts>> product;
CSession session;
product.Open(session, "Products", &propset);
```

Si vous utilisez `CDynamicAccessor`, la mémoire tampon est définie dynamiquement au moment de l’exécution. Dans ce cas, vous pouvez utiliser une version spécialisée de `CBookmark` pour laquelle vous ne spécifiez pas une longueur de la mémoire tampon. Utilisez la fonction `GetBookmark` pour récupérer le signet de l’enregistrement en cours, comme illustré dans cet exemple de code :

```cpp
CTable<CDynamicAccessor> product;
CBookmark<> bookmark;
CDBPropSet propset(DBPROPSET_ROWSET);
CSession session;

propset.AddProperty(DBPROP_BOOKMARKS, true);
product.Open(session, "Products", &propset);
product.MoveNext();
product.GetBookmark(&bookmark);
```

Pour plus d’informations sur la prise en charge des signets dans les fournisseurs, consultez [prise en charge de fournisseur de signets](../../data/oledb/provider-support-for-bookmarks.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)