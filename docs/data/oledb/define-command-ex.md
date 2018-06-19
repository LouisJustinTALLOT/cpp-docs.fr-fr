---
title: DEFINE_COMMAND_EX | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- DEFINE_COMMAND_EX
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND_EX macro
ms.assetid: d3e2ef20-1455-46d2-8499-8ab84bbb90a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b2a77fa0d6655edeee88df3c7c45e1936a766b40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101040"
---
# <a name="definecommandex"></a>DEFINE_COMMAND_EX
Spécifie la commande permettant de créer l’ensemble de lignes lors de l’utilisation du [CCommand](../../data/oledb/ccommand-class.md) classe. Prend en charge les applications Unicode et ANSI.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
DEFINE_COMMAND_EX(x, wszCommand)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *x*  
 [in] Le nom de la classe d’enregistrement (commande) utilisateur.  
  
 `wszCommand`  
 [in] La chaîne de commande permettant de créer l’ensemble de lignes lors de l’utilisation [CCommand](../../data/oledb/ccommand-class.md).  
  
## <a name="remarks"></a>Notes  
 La chaîne de commande que vous spécifiez sera être utilisée en tant que la valeur par défaut si vous ne spécifiez pas de texte de la commande dans le [CCommand::Open](../../data/oledb/ccommand-open.md) (méthode).  
  
 Cette macro accepte des chaînes Unicode, quel que soit le type d’application. Cette macro est préférée sur [DEFINE_COMMAND](../../data/oledb/define-command.md) , car il prend en charge Unicode, ainsi que les applications ANSI.  
  
## <a name="example"></a>Exemple  
 Consultez [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)