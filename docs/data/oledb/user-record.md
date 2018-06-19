---
title: Enregistrement d’utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5c58807dac8ae320ee69c8e1a372fff5b9d3db02
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111053"
---
# <a name="user-record"></a>Enregistrement utilisateur
L’enregistrement utilisateur fournit la code et structure de données qui représente les données de colonne pour un ensemble de lignes. Un enregistrement d’utilisateur peut être créé au moment de la compilation ou au moment de l’exécution. Lorsque vous créez un fournisseur à l’aide de l’Assistant fournisseur OLE DB ATL, l’Assistant crée un enregistrement d’utilisateur par défaut qui ressemble à ceci (en supposant que vous avez spécifié un nom de fournisseur [nom court] « MyProvider ») :  
  
```  
class CWindowsFile:  
   public WIN32_FIND_DATA  
{  
public:  
  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)  
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)  
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)  
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)  
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)  
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)  
END_PROVIDER_COLUMN_MAP()  
  
};  
```  
  
 Les modèles du fournisseur OLE DB gèrent toutes les particularités OLE DB concernant les interactions avec le client. Pour obtenir les données des colonnes nécessaires pour une réponse, le fournisseur appelle la `GetColumnInfo` (fonction), que vous devez placer dans l’enregistrement utilisateur. Vous pouvez substituer explicitement `GetColumnInfo` dans l’enregistrement d’utilisateur, par exemple, en la déclarant dans le fichier .h comme illustré ici :  
  
```  
template <class T>  
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)   
```  
  
 Ceci équivaut à :  
  
```  
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)  
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)  
```  
  
 Vous devez également implémenter `GetColumnInfo` dans le fichier .cpp de l’enregistrement utilisateur.  
  
 Les macros PROVIDER_COLUMN_MAP faciliter la création d’un `GetColumnInfo` (fonction) :  
  
-   BEGIN_PROVIDER_COLUMN_MAP définit le prototype de fonction et un tableau statique de **ATLCOLUMNINFO** structures.  
  
-   PROVIDER_COLUMN_ENTRY définit et initialise un seul **ATLCOLUMNINFO**.  
  
-   END_PROVIDER_COLUMN_MAP ferme le tableau et la fonction. Il permet également de placer le nombre d’éléments de tableau dans le `pcCols` paramètre.  
  
 Lorsqu’un enregistrement d’utilisateur est créé au moment de l’exécution **GetColumnInfo** utilise le `pThis` paramètre pour recevoir un pointeur vers une instance de l’ensemble de lignes ou de la commande. Commandes et des ensembles de lignes doit prendre en charge la `IColumnsInfo` interface, les informations de colonne peuvent être obtenues à partir de ce pointeur.  
  
 **CommandClass** et **RowsetClass** sont command et rowset qui utilisent l’enregistrement utilisateur.  
  
 Pour obtenir un exemple plus détaillé de la procédure de remplacement `GetColumnInfo` dans un enregistrement d’utilisateur, consultez [déterminer dynamiquement les colonnes retournées au consommateur](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)