---
title: Stockage de chaînes dans le fournisseur OLE DB | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a5ba289e7e53ba1bcaca550ba84c2d871d215306
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106984"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Stockage de chaînes dans le fournisseur OLE DB
Dans MyProviderRS.h, l’Assistant fournisseur OLE DB ATL crée un enregistrement d’utilisateur par défaut appelé `CWindowsFile`. Pour gérer les deux chaînes, vous devez soit modifier `CWindowsFile` ou ajoutez votre propre enregistrement utilisateur comme indiqué dans le code suivant :  
  
```cpp
////////////////////////////////////////////////////////////////////////  
class CAgentMan:   
   public WIN32_FIND_DATA  
   DWORD dwBookmark;              // Add this  
   TCHAR szCommand[256];          // Add this  
   TCHAR szText[256];             // Add this  
   TCHAR szCommand2[256];         // Add this  
   TCHAR szText2[256];            // Add this  
  
{  
public:  
BEGIN_PROVIDER_COLUMN_MAP()  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command"), 1, 256, GUID_NULL, CAgentMan, szCommand)  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text"), 2, 256, GUID_NULL, CAgentMan, szText)   
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command2"), 3, 256, GUID_NULL, CAgentMan, szCommand2)  
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text2"),4, 256, GUID_NULL, CAgentMan, szText2)  
END_PROVIDER_COLUMN_MAP()  
   bool operator==(const CAgentMan& am) // This is optional   
   {  
      return (lstrcmpi(cFileName, wf.cFileName) == 0);  
   }  
};  
```  
  
 Les membres de données `szCommand` et `szText` représentent les deux chaînes, avec `szCommand2` et `szText2` fournissant des colonnes supplémentaires si nécessaire. Le membre de données `dwBookmark` n’est pas nécessaire pour ce fournisseur en lecture seule simple mais est utilisée ultérieurement pour ajouter une `IRowsetLocate` interface ; consultez [amélioration en lecture uniquement fournisseur Simple](../../data/oledb/enhancing-the-simple-read-only-provider.md). Le `==` opérateur compare des instances (l’implémentation de cet opérateur est facultative).  
  
 Dans ce cas, votre fournisseur doit être prêt à compiler et exécuter. Pour tester le fournisseur, vous avez besoin d’un consommateur avec la fonctionnalité de correspondance. [Implémentation d’un consommateur Simple](../../data/oledb/implementing-a-simple-consumer.md) montre comment créer un tel consommateur de test. Exécutez le consommateur de test avec le fournisseur. Vérifiez que le consommateur de test récupère les chaînes appropriées à partir du fournisseur lorsque vous cliquez sur le **exécuter** situé dans le **consommateur de Test** boîte de dialogue.  
  
 Lorsque vous avez testé avec succès votre fournisseur, vous souhaiterez peut-être améliorer ses fonctionnalités en implémentant des interfaces supplémentaires. Voici un exemple dans [amélioration du fournisseur Simple accessible en lecture seule](../../data/oledb/enhancing-the-simple-read-only-provider.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un fournisseur simple accessible en lecture seule](../../data/oledb/implementing-the-simple-read-only-provider.md)