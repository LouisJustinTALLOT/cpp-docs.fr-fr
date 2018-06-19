---
title: DEFINE_COMMAND | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- DEFINE_COMMAND
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND macro
ms.assetid: 9d724968-e242-413c-9a13-e7175fccf9b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51f975b0477d29fbb35880c796f52612456c32c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101469"
---
# <a name="definecommand"></a>DEFINE_COMMAND
Spécifie la commande permettant de créer l’ensemble de lignes lors de l’utilisation du [CCommand](../../data/oledb/ccommand-class.md) classe. Accepte uniquement les types de chaîne correspondant au type d’application spécifié (ANSI ou Unicode).  
  
> [!NOTE]
>  Il est recommandé d’utiliser [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) au lieu de `DEFINE_COMMAND`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
DEFINE_COMMAND(x, szCommand)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *x*  
 [in] Le nom de la classe d’enregistrement (commande) utilisateur.  
  
 `szCommand`  
 [in] La chaîne de commande permettant de créer l’ensemble de lignes lors de l’utilisation [CCommand](../../data/oledb/ccommand-class.md).  
  
## <a name="remarks"></a>Notes  
 La chaîne de commande que vous spécifiez sera être utilisée en tant que la valeur par défaut si vous ne spécifiez pas de texte de la commande dans le [CCommand::Open](../../data/oledb/ccommand-open.md) (méthode).  
  
 Cette macro accepte des chaînes ANSI si vous générez votre application comme ANSI ou des chaînes Unicode, si vous générez votre application au format Unicode. Il est recommandé d’utiliser [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) au lieu de `DEFINE_COMMAND`, car ce dernier accepte les chaînes Unicode, quel que soit le type d’application ANSI ou Unicode.  
  
## <a name="example"></a>Exemple  
 Consultez [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)