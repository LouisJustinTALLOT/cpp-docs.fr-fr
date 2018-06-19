---
title: CCommand::Close | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CCommand.Close
- CCommand::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 4da9c02c-7082-4e47-a0fa-78b546f0f7d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5723c358e0af7cf9b92952bfd843ba90577333e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089762"
---
# <a name="ccommandclose"></a>CCommand::Close
Libère l’ensemble de lignes accesseur associé à la commande.  
  
## <a name="syntax"></a>Syntaxe

```cpp
void Close();  
```  
  
## <a name="remarks"></a>Notes  
 Une commande utilise un ensemble de lignes de résultat d’accesseur set et (éventuellement) un accesseur de paramètre (contrairement aux tables qui ne prennent pas en charge les paramètres et n’avez pas besoin d’un accesseur de paramètre).  
  
 Lorsque vous exécutez une commande, vous devez appeler à la fois `Close` et [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) après la commande.  
  
 Lorsque vous souhaitez exécuter la même commande plusieurs fois, vous devez libérer chaque accesseur de jeu de résultats en appelant `Close` avant d’appeler `Execute`. À la fin de la série, vous devez libérer de l’accesseur de paramètre en appelant `ReleaseCommand`. Un autre scénario courant appelle une procédure stockée qui a des paramètres de sortie. De nombreux fournisseurs (par exemple, le fournisseur OLE DB pour SQL Server) les valeurs de paramètre de sortie ne seront plus accessibles jusqu'à la fermeture de l’accesseur set de résultat. Appelez `Close` pour fermer l’ensemble de lignes retournée et accesseur de jeu de résultats, mais pas l’accesseur de paramètre, ce qui permet de récupérer les valeurs de paramètre de sortie.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment vous pouvez appeler `Close` et `ReleaseCommand` lorsque vous exécutez la même commande de façon répétée.  
  
 [!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CCommand (classe)](../../data/oledb/ccommand-class.md)   
 [CCommand::ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)