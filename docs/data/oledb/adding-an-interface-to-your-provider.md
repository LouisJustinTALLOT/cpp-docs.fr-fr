---
title: Ajout d’une Interface à votre fournisseur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f50459550c91f07c12f6f18b3fbbaa5622ab7408
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032391"
---
# <a name="adding-an-interface-to-your-provider"></a>Ajout d'une interface à votre fournisseur

Déterminer quel objet que vous souhaitez ajouter l’interface (généralement, des objets data source, ensemble de lignes, commande ou session créés par l’Assistant fournisseur OLE DB). Il est possible que l’objet que vous devez ajouter l’interface est par votre fournisseur ne prend pas en charge actuellement. Dans ce cas, exécutez l’Assistant fournisseur OLE DB ATL pour créer l’objet. Cliquez sur le projet dans l’affichage de classes, cliquez sur **ajouter une classe** à partir de la **ajouter** menu, puis sur **fournisseur OLE DB ATL**. Vous souhaiterez peut-être placer le code d’interface dans un répertoire séparé et puis copiez les fichiers à votre projet de fournisseur.  
  
Si vous avez créé une nouvelle classe pour prendre en charge l’interface, faites en sorte que l’objet hérite de cette classe. Par exemple, vous pouvez ajouter la classe **IRowsetIndexImpl** à un objet d’ensemble de lignes :  
  
```cpp  
template <class Creator>  
class CAgentRowset :   
    public CRowsetImpl< CAgentRowset<Creator>, CAgentMan, Creator>,  
    public IRowsetIndexImpl< ... >   
```  
  
Ajouter l’interface **COM_MAP** dans l’objet en utilisant la macro COM_INTERFACE_ENTRY. S’il n’existe aucun mappage, créez-le. Exemple :  
  
```cpp  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
END_COM_MAP()  
```  
  
Pour l’objet rowset, chaînez le mappage de son parent de l’objet afin que l’objet puisse déléguer à la classe parente. Dans cet exemple, ajoutez la macro COM_INTERFACE_ENTRY_CHAIN au mappage :  
  
```cpp  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)  
END_COM_MAP()  
```  
  
## <a name="see-also"></a>Voir aussi  

[Utilisation des modèles du fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)