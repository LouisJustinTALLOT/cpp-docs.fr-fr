---
title: Utilisation de signets
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: 5a4a2d65ba7367b5568603b5f08a07c6d85cc4a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209311"
---
# <a name="using-bookmarks"></a>Utilisation de signets

Avant d’ouvrir l’ensemble de lignes, vous devez indiquer au fournisseur que vous souhaitez utiliser des signets. Pour ce faire, affectez à la propriété `DBPROP_BOOKMARKS` la **valeur true** dans votre jeu de propriétés. Le fournisseur récupère les signets en tant que colonne zéro. vous devez donc utiliser la macro spéciale BOOKMARK_ENTRY et la classe `CBookmark` si vous utilisez un accesseur statique. `CBookmark` est une classe de modèle dans laquelle l’argument est la longueur en octets de la mémoire tampon du signet. La longueur de la mémoire tampon requise pour un signet dépend du fournisseur. Si vous utilisez le fournisseur de OLE DB ODBC, comme indiqué dans l’exemple suivant, la mémoire tampon doit être de 4 octets.

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

Ensuite, utilisé par le code suivant :

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_BOOKMARKS, true);

CTable<CAccessor<CProducts>> product;
CSession session;
product.Open(session, "Products", &propset);
```

Si vous utilisez `CDynamicAccessor`, la mémoire tampon est définie dynamiquement au moment de l’exécution. Dans ce cas, vous pouvez utiliser une version spécialisée de `CBookmark` pour laquelle vous ne spécifiez pas de longueur de mémoire tampon. Utilisez la fonction `GetBookmark` pour récupérer le signet de l’enregistrement actif, comme illustré dans cet exemple de code :

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

Pour plus d’informations sur la prise en charge des signets dans les fournisseurs, consultez [prise en charge des signets par le fournisseur](../../data/oledb/provider-support-for-bookmarks.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)
