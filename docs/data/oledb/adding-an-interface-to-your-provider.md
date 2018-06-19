---
title: Ajout d’une Interface à votre fournisseur | Documents Microsoft
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
ms.openlocfilehash: 3d6bc5d1b6c47d2ffa26bffa98d47b930d6ed193
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093544"
---
# <a name="adding-an-interface-to-your-provider"></a>Ajout d'une interface à votre fournisseur
Déterminez l’objet auquel vous souhaitez ajouter l’interface (généralement, des objets data source, ensemble de lignes, commandes ou session créés par l’Assistant fournisseur OLE DB). Il est possible que l’objet que vous devez ajouter l’interface est par votre fournisseur ne prend pas en charge actuellement. Dans ce cas, exécutez l’Assistant fournisseur OLE DB ATL pour créer l’objet. Cliquez sur le projet dans l’affichage de classes, cliquez sur **ajouter une classe** à partir de la **ajouter** menu, puis sur **fournisseur OLE DB ATL**. Vous pouvez souhaiter placer le code d’interface dans un répertoire différent, puis copiez les fichiers à votre projet de fournisseur.  
  
 Si vous avez créé une nouvelle classe pour prendre en charge l’interface, faites en sorte que l’objet hérite de cette classe. Par exemple, vous pouvez ajouter la classe **IRowsetIndexImpl** à un objet d’ensemble de lignes :  
  
```cpp  
template <class Creator>  
class CAgentRowset :   
    public CRowsetImpl< CAgentRowset<Creator>, CAgentMan, Creator>,  
    public IRowsetIndexImpl< ... >   
```  
  
 Ajouter l’interface **COM_MAP** dans l’objet à l’aide de la macro COM_INTERFACE_ENTRY. Si aucun mappage n’existe, créez-en un. Par exemple :  
  
```cpp  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
END_COM_MAP()  
```  
  
 Pour l’objet rowset, chaînez le mappage de son parent de l’objet afin que l’objet peut déléguer à la classe parente. Dans cet exemple, ajoutez la macro COM_INTERFACE_ENTRY_CHAIN au mappage :  
  
```cpp  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)  
END_COM_MAP()  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des modèles du fournisseur OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)