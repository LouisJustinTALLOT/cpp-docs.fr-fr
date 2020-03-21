---
title: Enregistrement utilisateur
ms.date: 05/09/2019
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
ms.openlocfilehash: 4a8fb6c9eeee3736501a04a095bdd763de16de7d
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079004"
---
# <a name="user-record"></a>Enregistrement utilisateur

> [!NOTE]
> L’Assistant Fournisseur OLE DB ATL n’est pas disponible dans Visual Studio 2019 et les versions ultérieures.

L’enregistrement utilisateur fournit la structure de code et de données qui représente les données de colonne pour un ensemble de lignes. Un enregistrement d’utilisateur peut être créé au moment de la compilation ou au moment de l’exécution. Lorsque vous créez un fournisseur à l’aide de l’**Assistant Fournisseur OLE DB ATL**, l’Assistant crée un enregistrement utilisateur par défaut qui ressemble à ceci (en supposant que vous avez spécifié un nom de fournisseur [nom court] de *MyProvider*) :

```cpp
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

Les modèles du fournisseur OLE DB gèrent toutes les particularités de OLE DB sur les interactions avec le client. Pour acquérir les données de colonne nécessaires pour une réponse, le fournisseur appelle la fonction `GetColumnInfo` que vous devez placer dans l’enregistrement utilisateur. Vous pouvez remplacer explicitement `GetColumnInfo` dans l’enregistrement utilisateur, par exemple, en le déclarant dans le fichier .h comme illustré ici :

```cpp
template <class T>
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)
```

Cela équivaut à :

```cpp
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)
```

Ensuite, implémentez `GetColumnInfo` dans le fichier .cpp de l’enregistrement utilisateur.

Les macros PROVIDER_COLUMN_MAP facilitent la création d’une fonction `GetColumnInfo` :

- BEGIN_PROVIDER_COLUMN_MAP définit le prototype de fonction et un tableau statique de structures `ATLCOLUMNINFO`.

- PROVIDER_COLUMN_ENTRY définit et initialise un seul `ATLCOLUMNINFO`.

- END_PROVIDER_COLUMN_MAP ferme le tableau et la fonction. Il place également le nombre d’éléments de tableau dans le paramètre *pcCols*.

Lorsqu’un enregistrement utilisateur est créé au moment de l’exécution, `GetColumnInfo` utilise le paramètre *pCe* pour recevoir un pointeur vers une instance de l’ensemble de lignes ou de la commande. Les commandes et les ensembles de lignes doivent prendre en charge l’interface `IColumnsInfo` afin que les informations de colonne puissent être prises à partir de ce pointeur.

`CommandClass` et `RowsetClass` sont la commande et l’ensemble de lignes qui utilisent l’enregistrement utilisateur.

Pour obtenir un exemple plus détaillé concernant le remplacement de `GetColumnInfo` dans un enregistrement utilisateur, consultez [Déterminer de manière dynamique des colonnes retournées au consommateur](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Voir aussi

[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
