---
title: Ajout d'une interface à votre fournisseur
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: c0452ca74509b65de3787af93bff41b3cb399c99
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384970"
---
# <a name="adding-an-interface-to-your-provider"></a>Ajout d'une interface à votre fournisseur

Déterminer des objets que vous souhaitez ajouter l’interface (généralement les objets de données source, ensemble de lignes, commande ou session créés par le **Assistant fournisseur OLE DB**). Il est possible que l’objet que vous devez ajouter l’interface est par votre fournisseur ne prend actuellement en charge. Dans ce cas, exécutez le **Assistant fournisseur OLE DB ATL** pour créer l’objet. Cliquez sur le projet dans **affichage de classes**, cliquez sur **ajouter** > **un nouvel élément** dans le menu, sélectionnez **installé**  >  **Visual C++** > **ATL**, puis cliquez sur **fournisseur d’OLEDB ATL**. Vous souhaiterez peut-être placer le code d’interface dans un répertoire séparé et puis copiez les fichiers à votre projet de fournisseur.

Si vous avez créé une nouvelle classe pour prendre en charge l’interface, faites en sorte que l’objet hérite de cette classe. Par exemple, vous pouvez ajouter la classe `IRowsetIndexImpl` à un objet d’ensemble de lignes :

```cpp
template <class Creator>
class CCustomRowset :
    public CRowsetImpl< CCustomRowset<Creator>, CCustomWindowsFile, Creator>,
    public IRowsetIndexImpl< ... >
```

Ajoutez l’interface à COM_MAP dans l’objet en utilisant la macro COM_INTERFACE_ENTRY. S’il n’existe aucun mappage, créez-le. Exemple :

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

Pour l’objet rowset, chaînez le mappage de son parent de l’objet afin que l’objet puisse déléguer à la classe parente. Dans cet exemple, ajoutez la macro COM_INTERFACE_ENTRY_CHAIN au mappage :

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles du fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)