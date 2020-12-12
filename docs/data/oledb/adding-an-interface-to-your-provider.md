---
description: 'En savoir plus sur : ajout d’une interface à votre fournisseur'
title: Ajout d'une interface à votre fournisseur
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: 0514f57489fd0a5d97f659fc5695cc7e0f8e03e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246069"
---
# <a name="adding-an-interface-to-your-provider"></a>Ajout d'une interface à votre fournisseur

> [!NOTE]
> L’Assistant Fournisseur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et versions ultérieures.

Déterminez à quel objet vous souhaitez ajouter l’interface (généralement des objets de source de données, d’ensemble de lignes, de commande ou de session créés par l’**Assistant Fournisseur OLE DB**). Il est possible que l’objet auquel vous devez ajouter l’interface ne soit pas pris en charge actuellement par votre fournisseur. Dans ce cas, exécutez l’**Assistant Fournisseur OLE DB ATL** pour créer l’objet. Cliquez avec le bouton droit sur le projet dans **Affichage de classes**, cliquez sur **Ajouter** > **Nouvel élément** dans le menu, sélectionnez **Installé** > **Visual C++** > **ATL**, puis cliquez sur **Fournisseur OLE DB ATL**. Nous vous conseillons de placer le code d’interface dans un répertoire séparé, puis de copier les fichiers dans votre projet fournisseur.

Si vous avez créé une nouvelle classe pour prendre en charge l’interface, faites en sorte que l’objet hérite de cette classe. Par exemple, vous pouvez ajouter la classe `IRowsetIndexImpl` à un objet d’ensemble de lignes :

```cpp
template <class Creator>
class CCustomRowset :
    public CRowsetImpl< CCustomRowset<Creator>, CCustomWindowsFile, Creator>,
    public IRowsetIndexImpl< ... >
```

Ajoutez l’interface à COM_MAP dans l’objet en utilisant la macro COM_INTERFACE_ENTRY. S’il n’existe aucun mappage, créez-le. Par exemple :

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

Pour l’objet d’ensemble de lignes, chaînez le mappage de son objet parent afin que l’objet puisse déléguer à la classe parente. Dans cet exemple, ajoutez la macro COM_INTERFACE_ENTRY_CHAIN au mappage :

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>Voir aussi

[Utilisation des modèles de fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
