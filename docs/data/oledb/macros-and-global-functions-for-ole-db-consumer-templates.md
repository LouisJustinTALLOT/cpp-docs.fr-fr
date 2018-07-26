---
title: Macros et fonctions globales pour les modèles du consommateur OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
- BEGIN_ACCESSOR
- BEGIN_ACCESSOR_MAP
- END_ACCESSOR
- END_ACCESSOR_MAP
- BEGIN_COLUMN_MAP
- BLOB_ENTRY
- BLOB_ENTRY_LENGTH
- BLOB_ENTRY_LENGTH_STATUS
- BLOB_ENTRY_STATUS
- BLOB_NAME
- BLOB_NAME_LENGTH
- BLOB_NAME_LENGTH_STATUS
- BLOB_NAME_STATUS
- BOOKMARK_ENTRY
- COLUMN_ENTRY
- COLUMN_ENTRY_EX
- COLUMN_ENTRY_LENGTH
- COLUMN_ENTRY_LENGTH_STATUS
- COLUMN_ENTRY_PS
- COLUMN_ENTRY_PS_LENGTH
- COLUMN_ENTRY_PS_LENGTH_STATUS
- COLUMN_ENTRY_PS_STATUS
- COLUMN_ENTRY_STATUS
- COLUMN_ENTRY_TYPE
- COLUMN_ENTRY_TYPE_SIZE
- COLUMN_NAME
- COLUMN_NAME_EX
- COLUMN_NAME_LENGTH
- COLUMN_NAME_LENGTH_STATUS
- COLUMN_NAME_PS
- COLUMN_NAME_PS_LENGTH
- COLUMN_NAME_PS_LENGTH_STATUS
- COLUMN_NAME_PS_STATUS
- COLUMN_NAME_STATUS
- COLUMN_NAME_TYPE
- COLUMN_NAME_TYPE_PS
- COLUMN_NAME_TYPE_SIZE
- COLUMN_NAME_TYPE_STATUS
- END_COLUMN_MAP
- DEFINE_COMMAND
- DEFINE_COMMAND_EX
- BEGIN_PARAM_MAP
- END_PARAM_MAP
- SET_PARAM_TYPE
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
- AtlTraceErrorRecords function
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR_MAP macro
- END_ACCESSOR macro
- END_ACCESSOR_MAP macro
- BEGIN_COLUMN_MAP macro
- BLOB_ENTRY macro
- BLOB_ENTRY_LENGTH macro
- BLOB_ENTRY_LENGTH_STATUS macro
- BLOB_ENTRY_STATUS macro
- BLOB_NAME macro
- BLOB_NAME_LENGTH macro
- BLOB_NAME_LENGTH_STATUS macro
- BLOB_NAME_STATUS macro
- BOOKMARK_ENTRY macro
- COLUMN_ENTRY macro
- COLUMN_ENTRY_EX macro
- COLUMN_ENTRY_LENGTH macro
- COLUMN_ENTRY_LENGTH_STATUS macro
- COLUMN_ENTRY_PS macro
- COLUMN_ENTRY_PS_LENGTH macro
- COLUMN_ENTRY_PS_LENGTH_STATUS macro
- COLUMN_ENTRY_PS_STATUS macro
- COLUMN_ENTRY_STATUS macro
- COLUMN_ENTRY_TYPE macro
- COLUMN_ENTRY_TYPE_SIZE macro
- COLUMN_NAME macro
- COLUMN_NAME_EX macro
- COLUMN_NAME_LENGTH macro
- COLUMN_NAME_LENGTH_STATUS macro
- COLUMN_NAME_PS macro
- COLUMN_NAME_PS_LENGTH macro
- COLUMN_NAME_PS_LENGTH_STATUS macro
- COLUMN_NAME_PS_STATUS macro
- COLUMN_NAME_STATUS macro
- COLUMN_NAME_TYPE macro
- COLUMN_NAME_TYPE_PS macro
- COLUMN_NAME_TYPE_SIZE macro
- COLUMN_NAME_TYPE_STATUS macro
- END_COLUMN_MAP macro
- DEFINE_COMMAND macro
- DEFINE_COMMAND_EX macro
- BEGIN_PARAM_MAP macro
- END_PARAM_MAP macro
- SET_PARAM_TYPE macro
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e5d9105492af55547794023c3574fb626d470828
ms.sourcegitcommit: 0bf5f6634d66ed92fffb32291ad9f854d9895b17
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39250665"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Macros et fonctions globales pour les modèles du consommateur OLE DB
Les modèles du consommateur OLE DB incluent les macros suivantes et les fonctions globales :  
  
## <a name="global-functions"></a>Fonctions globales  
  
|||  
|-|-|  
|[AtlTraceErrorRecords](#atltraceerrorrecords)|Exporte les informations d’enregistrement d’erreur OLE DB à l’unité de vidage si une erreur est retournée.|  
  
## <a name="accessor-map-macros"></a>Macros de mappage d’accesseur  
  
|||  
|-|-|  
|[BEGIN_ACCESSOR](#begin_accessor)|Marque le début d’une entrée de l’accesseur.|  
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|Marque le début des entrées de mappage d’accesseur.|  
|[END_ACCESSOR](#end_accessor)|Marque la fin d’une entrée de l’accesseur.|  
|[END_ACCESSOR_MAP](#end_accessor_map)|Marque la fin des entrées de mappage d’accesseur.|  
  
## <a name="column-map-macros"></a>Macros de mappage de colonne  
  
|||  
|-|-|  
|[BEGIN_COLUMN_MAP](#begin_column_map)|Marque le début des entrées de mappage de colonne dans la classe d’enregistrement utilisateur.|  
|[BLOB_ENTRY](#blob_entry)|Utilisé pour lier un objet binaire volumineux (BLOB).|  
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|Indique la longueur de la colonne de données BLOB.|  
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|Indique la longueur et l’état de la colonne de données BLOB.|  
|[BLOB_ENTRY_STATUS](#blob_entry_status)|Signale l’état de la colonne de données BLOB.|  
|[BLOB_NAME](#blob_name)|Utilisé pour lier un objet binaire volumineux par le nom de colonne.|  
|[BLOB_NAME_LENGTH](#blob_name_length)|Indique la longueur de la colonne de données BLOB.|  
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|Indique la longueur et l’état de la colonne de données BLOB.|  
|[BLOB_NAME_STATUS](#blob_name_status)|Signale l’état de la colonne de données BLOB.|  
|[BOOKMARK_ENTRY](#bookmark_entry)|Représente une entrée de signet sur l’ensemble de lignes. Une entrée de signet est un type spécial d’entrée de la colonne.|  
|[COLUMN_ENTRY](#column_entry)|Représente une liaison à une colonne spécifique dans la base de données.|  
|[COLUMN_ENTRY_EX](#column_entry_ex)|Représente une liaison à la colonne dans la base de données. Prend en charge *type*, *longueur*, *précision*, *mise à l’échelle*, et *état* paramètres.|  
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|Représente une liaison à la colonne dans la base de données. Prend en charge la *longueur* variable.|  
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|Représente une liaison à la colonne dans la base de données. Prend en charge *état* et *longueur* paramètres.|  
|[COLUMN_ENTRY_PS](#column_entry_ps)|Représente une liaison à la colonne dans la base de données. Prend en charge *précision* et *mise à l’échelle* paramètres.|  
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|Représente une liaison à la colonne dans la base de données. Prend en charge la *longueur* variable, *précision* et *mise à l’échelle* paramètres.|  
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|Représente une liaison à la colonne dans la base de données. Prend en charge *état* et *longueur* variables, *précision* et *mise à l’échelle* paramètres.|  
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|Représente une liaison à la colonne dans la base de données. Prend en charge la *état* variable, *précision* et *mise à l’échelle* paramètres.|  
|[COLUMN_ENTRY_STATUS](#column_entry_status)|Représente une liaison à la colonne dans la base de données. Prend en charge la *état* variable.|  
|[COLUMN_ENTRY_TYPE](#column_entry_type)|Représente une liaison à une colonne spécifique dans la base de données. Prend en charge *type* paramètre.|  
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|Représente une liaison à la colonne dans la base de données. Prend en charge *type* et *taille* paramètres.|  
|[COLUMN_NAME](#column_name)|Représente une liaison à une colonne spécifique dans la base de données par nom.|  
|[COLUMN_NAME_EX](#column_name_ex)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de type de données, taille, précision, échelle, longueur de colonne et l’état de la colonne.|  
|[COLUMN_NAME_LENGTH](#column_name_length)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de longueur de colonne.|  
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de longueur de colonne et l’état.|  
|[COLUMN_NAME_PS](#column_name_ps)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de précision et d’échelle.|  
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de longueur de précision, échelle et de colonne.|  
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de précision, échelle, longueur de colonne et état de la colonne.|  
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de précision, échelle et colonne État.|  
|[COLUMN_NAME_STATUS](#column_name_status)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de l’état de la colonne.|  
|[COLUMN_NAME_TYPE](#column_name_type)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification du type de données.|  
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de type de données, précision et échelle.|  
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de type de données et la taille.|  
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|Représente une liaison à une colonne spécifique dans la base de données par nom. Prend en charge la spécification de l’état de type et à la colonne de données.|  
|[END_COLUMN_MAP](#end_column_map)|Marque la fin des entrées de mappage de colonne.|  
  
## <a name="command-macros"></a>Macros de commande  
  
|||  
|-|-|  
|[DEFINE_COMMAND](#define_command)|Spécifie la commande permettant de créer l’ensemble de lignes lorsque vous utilisez le [CCommand](../../data/oledb/ccommand-class.md) classe. Accepte uniquement les types de chaîne correspondant au type d’application spécifiée (ANSI ou Unicode). Il est recommandé d’utiliser [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) au lieu de DEFINE_COMMAND.|  
|[DEFINE_COMMAND_EX](#define_command_ex)|Spécifie la commande permettant de créer l’ensemble de lignes lorsque vous utilisez le [CCommand](../../data/oledb/ccommand-class.md) classe. Prend en charge les applications ANSI et Unicode.|  
  
## <a name="parameter-map-macros"></a>Macros de mappage de paramètre  
  
|||  
|-|-|  
|[BEGIN_PARAM_MAP](#begin_param_map)|Marque le début des entrées de mappage de paramètre dans la classe d’enregistrement utilisateur.|  
|[END_PARAM_MAP](#end_param_map)|Marque la fin des entrées de mappage de paramètre.|  
|[SET_PARAM_TYPE](#set_param_type)|Spécifie les macros COLUMN_ENTRY qui suivent le set_param_type (macro) en tant qu’entrée, sortie ou d’entrée/sortie.|  

### <a name="atltraceerrorrecords"></a> AtlTraceErrorRecords
Exporte les informations d’enregistrement d’erreur OLE DB à l’unité de vidage si une erreur est retournée.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
      inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *hErr*  
 [in] HRESULT retourné par une fonction membre de modèle du consommateur OLE DB.  
  
#### <a name="remarks"></a>Notes  
 Si *hErr* n’est pas S_OK, `AtlTraceErrorRecords` exporte les informations de l’enregistrement d’erreur OLE DB à l’unité de vidage (le **déboguer** onglet de la fenêtre Sortie ou un fichier). Les informations de l’enregistrement d’erreur, qui sont obtenues à partir du fournisseur, incluent le numéro de ligne source, description, fichier d’aide, contexte et GUID pour chaque entrée d’enregistrement erreur. `AtlTraceErrorRecords` exporte ces informations uniquement dans les versions debug. Dans les versions release, il est un stub vide qui est optimisé out.  
  
#### <a name="see-also"></a>Voir aussi    
 [CDBErrorInfo, classe](../../data/oledb/cdberrorinfo-class.md)

### <a name="begin_accessor"></a> BEGIN_ACCESSOR
Marque le début d’une entrée de l’accesseur.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp  
BEGIN_ACCESSOR(num, bAuto)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *num*  
 [in] Le nombre de décalage de zéro pour l’accesseur dans ce mappage d’accesseur.  
  
 *bAuto*  
 [in] Spécifie si cet accesseur est un accesseur automatique ou un accesseur manuel. Si **true**, l’accesseur est automatique ; si **false**, l’accesseur est manuel. Un accesseur automatique signifie que les données sont extraites pour vous sur les opérations de déplacement.  
  
#### <a name="remarks"></a>Notes  
 Dans le cas de plusieurs accesseurs dans un ensemble de lignes, vous devez spécifier BEGIN_ACCESSOR_MAP et utiliser la macro BEGIN_ACCESSOR pour chaque accesseur individuel. La macro BEGIN_ACCESSOR s’est terminée avec l’END_ACCESSOR (macro). La macro BEGIN_ACCESSOR_MAP s’est terminée avec l’end_accessor_map (macro).  
  
#### <a name="example"></a>Exemple  
 Consultez [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  

### <a name="begin_accessor_map"></a> BEGIN_ACCESSOR_MAP
Marque le début des entrées de mappage d’accesseur.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp  
BEGIN_ACCESSOR_MAP(x, num)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *x*  
 [in] Nom de la classe d’enregistrement utilisateur.  
  
 *num*  
 [in] Nombre d’accesseurs contenus dans ce mappage d’accesseur.  
  
#### <a name="remarks"></a>Notes  
 Dans le cas de plusieurs accesseurs dans un ensemble de lignes, vous devez spécifier BEGIN_ACCESSOR_MAP au début et utiliser la macro BEGIN_ACCESSOR pour chaque accesseur individuel. La macro BEGIN_ACCESSOR s’est terminée avec l’END_ACCESSOR (macro). Le mappage d’accesseur est terminé avec l’end_accessor_map (macro).  
  
 Si l’enregistrement utilisateur ne comprend qu’un seul accesseur, utilisez la macro [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).  
  
#### <a name="example"></a>Exemple  

 ```cpp  
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
 ```

### <a name="end_accessor"></a> END_ACCESSOR
Marque la fin d’une entrée de l’accesseur.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
END_ACCESSOR()  
  
```  
  
#### <a name="remarks"></a>Notes  
 Pour les accesseurs multiples sur un ensemble de lignes, vous devez spécifier BEGIN_ACCESSOR_MAP et utiliser la macro BEGIN_ACCESSOR pour chaque accesseur individuel. La macro BEGIN_ACCESSOR s’est terminée avec l’END_ACCESSOR (macro). La macro BEGIN_ACCESSOR_MAP s’est terminée avec l’end_accessor_map (macro).  
  
#### <a name="example"></a>Exemple  
 Consultez [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  

### <a name="end_accessor_map"></a> END_ACCESSOR_MAP
Marque la fin des entrées de mappage d’accesseur.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
END_ACCESSOR_MAP()  
  
```  
  
#### <a name="remarks"></a>Notes  
 Pour les accesseurs multiples sur un ensemble de lignes, vous devez spécifier BEGIN_ACCESSOR_MAP et utiliser la macro BEGIN_ACCESSOR pour chaque accesseur individuel. La macro BEGIN_ACCESSOR s’est terminée avec l’END_ACCESSOR (macro). La macro BEGIN_ACCESSOR_MAP s’est terminée avec l’end_accessor_map (macro).  
  
#### <a name="example"></a>Exemple  
 Consultez [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  

### <a name="begin_column_map"></a> BEGIN_COLUMN_MAP
Marque le début d’une entrée de mappage de colonnes.  
  
#### <a name="syntax"></a>Syntaxe  
  
```  
BEGIN_COLUMN_MAP(x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *x*  
 [in] Nom de la classe d’enregistrement utilisateur dérivée de `CAccessor`.  
  
#### <a name="remarks"></a>Notes  
 Cette macro est utilisée dans le cas d’un seul accesseur sur un ensemble de lignes. Si vous avez plusieurs accesseurs sur un ensemble de lignes, utilisez [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  
  
 La macro BEGIN_COLUMN_MAP s’est terminée avec l’END_COLUMN_MAP (macro). Cette macro est utilisée quand un seul accesseur est obligatoire dans l’enregistrement utilisateur.  
  
 Les colonnes correspondent aux champs de l’ensemble de lignes à lier.  
  
#### <a name="example"></a>Exemple  
 Voici un exemple de mappage de colonnes et de paramètres :  
  
 <!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a> BLOB_ENTRY
Permet de lier un objet binaire volumineux avec BEGIN_COLUMN_MAP et END_COLUMN_MAP ([BLOB](https://msdn.microsoft.com/library/ms711511.aspx)).  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nOrdinal*  
 [in] Le numéro de colonne.  
  
 *IID*  
 [in] Interface, GUID, tels que `IDD_ISequentialStream`, utilisé pour récupérer l’objet BLOB.  
  
 *flags*  
 [in] Indicateurs de mode de stockage tel que défini par le modèle de stockage structuré OLE (par exemple, `STGM_READ`).  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
#### <a name="example"></a>Exemple  
 Consultez [comment récupérer un objet BLOB ?](../../data/oledb/retrieving-a-blob.md).  

### <a name="blob_entry_length"></a> BLOB_ENTRY_LENGTH
Permet de lier un objet binaire volumineux avec BEGIN_COLUMN_MAP et END_COLUMN_MAP ([BLOB](https://msdn.microsoft.com/library/ms711511.aspx)). Semblable à [BLOB_ENTRY](../../data/oledb/blob-entry.md), sauf que cette macro obtient également la longueur en octets de la colonne BLOB.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nOrdinal*  
 [in] Le numéro de colonne.  
  
 *IID*  
 [in] Interface, GUID, tels que `IDD_ISequentialStream`, utilisé pour récupérer l’objet BLOB.  
  
 *flags*  
 [in] Indicateurs de mode de stockage tel que défini par le modèle de stockage structuré OLE (par exemple, `STGM_READ`).  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [out] Longueur (réelle), en octets, de la colonne BLOB.  
  
#### <a name="example"></a>Exemple  
 Consultez [comment récupérer un objet BLOB ?](../../data/oledb/retrieving-a-blob.md).  

### <a name="blob_entry_length_status"></a> BLOB_ENTRY_LENGTH_STATUS
Permet de lier un objet binaire volumineux avec BEGIN_COLUMN_MAP et END_COLUMN_MAP ([BLOB](https://msdn.microsoft.com/library/ms711511.aspx)). Semblable à [BLOB_ENTRY](../../data/oledb/blob-entry.md), sauf que cette macro obtient également la longueur et l’état de la colonne BLOB.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BLOB_ENTRY_LENGTH_STATUS(  
    nOrdinal,  
    IID,  
    flags,  
    data,
    length,
    status )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nOrdinal*  
 [in] Le numéro de colonne.  
  
 *IID*  
 [in] Interface, GUID, tels que `IDD_ISequentialStream`, utilisé pour récupérer l’objet BLOB.  
  
 *flags*  
 [in] Indicateurs de mode de stockage tel que défini par le modèle de stockage structuré OLE (par exemple, `STGM_READ`).  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [out] Longueur (réelle), en octets, de la colonne BLOB.  
  
 *status*  
 [out] L’état de la colonne de données BLOB.  
  
#### <a name="example"></a>Exemple  
 Consultez [comment récupérer un objet BLOB ?](../../data/oledb/retrieving-a-blob.md).  

### <a name="blob_entry_status"></a> BLOB_ENTRY_STATUS
Permet de lier un objet binaire volumineux avec BEGIN_COLUMN_MAP ou BEGIN_ACCESSOR_MAP ([BLOB](https://msdn.microsoft.com/library/ms711511.aspx)). Semblable à [BLOB_ENTRY](../../data/oledb/blob-entry.md), sauf que cette macro obtient également l’état de la colonne BLOB.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nOrdinal*  
 [in] Le numéro de colonne.  
  
 *IID*  
 [in] Interface, GUID, tels que `IDD_ISequentialStream`, utilisé pour récupérer l’objet BLOB.  
  
 *flags*  
 [in] Indicateurs de mode de stockage tel que défini par le modèle de stockage structuré OLE (par exemple, `STGM_READ`).  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *status*  
 [out] L’état du champ BLOB.  
  
#### <a name="example"></a>Exemple  
 Consultez [comment récupérer un objet BLOB ?](../../data/oledb/retrieving-a-blob.md).  

### <a name="blob_name"></a> BLOB_NAME
Permet de lier un objet binaire volumineux avec BEGIN_COLUMN_MAP et END_COLUMN_MAP ([BLOB](https://msdn.microsoft.com/library/ms711511.aspx)). Semblable à [BLOB_ENTRY](../../data/oledb/blob-entry.md), sauf que cette macro accepte un nom de colonne au lieu d’un numéro de colonne.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BLOB_NAME(pszName, IID, flags, data )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *IID*  
 [in] Interface, GUID, tels que `IDD_ISequentialStream`, utilisé pour récupérer l’objet BLOB.  
  
 *flags*  
 [in] Indicateurs de mode de stockage tel que défini par le modèle de stockage structuré OLE (par exemple, `STGM_READ`).  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
#### <a name="example"></a>Exemple  
 Consultez [comment récupérer un objet BLOB ?](../../data/oledb/retrieving-a-blob.md).  

### <a name="blob_name_length"></a> BLOB_NAME_LENGTH
Permet de lier un objet binaire volumineux avec BEGIN_COLUMN_MAP et END_COLUMN_MAP ([BLOB](https://msdn.microsoft.com/library/ms711511.aspx)). Semblable à [nom_objet_blob](../../data/oledb/blob-name.md), sauf que cette macro obtient également la longueur en octets de la colonne de données BLOB.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *IID*  
 [in] Interface, GUID, tels que `IDD_ISequentialStream`, utilisé pour récupérer l’objet BLOB.  
  
 *flags*  
 [in] Indicateurs de mode de stockage tel que défini par le modèle de stockage structuré OLE (par exemple, `STGM_READ`).  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [out] Longueur (réelle), en octets, de la colonne BLOB.  

### <a name="blob_name_length_status"></a> BLOB_NAME_LENGTH_STATUS
Permet de lier un objet binaire volumineux avec BEGIN_COLUMN_MAP et END_COLUMN_MAP ([BLOB](https://msdn.microsoft.com/library/ms711511.aspx)). Semblable à [nom_objet_blob](../../data/oledb/blob-name.md), sauf que cette macro obtient également la longueur et l’état de la colonne de données BLOB.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *IID*  
 [in] Interface, GUID, tels que `IDD_ISequentialStream`, utilisé pour récupérer l’objet BLOB.  
  
 *flags*  
 [in] Indicateurs de mode de stockage tel que défini par le modèle de stockage structuré OLE (par exemple, `STGM_READ`).  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [out] Longueur (réelle), en octets, de la colonne BLOB.  
  
 *status*  
 [out] L’état du champ BLOB.  

### <a name="blob_name_status"></a> BLOB_NAME_STATUS
Permet de lier un objet binaire volumineux avec BEGIN_COLUMN_MAP et END_COLUMN_MAP ([BLOB](https://msdn.microsoft.com/library/ms711511.aspx)). Semblable à [nom_objet_blob](../../data/oledb/blob-name.md), sauf que cette macro obtient également l’état de la colonne de données BLOB.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *IID*  
 [in] Interface, GUID, tels que `IDD_ISequentialStream`, utilisé pour récupérer l’objet BLOB.  
  
 *flags*  
 [in] Indicateurs de mode de stockage tel que défini par le modèle de stockage structuré OLE (par exemple, `STGM_READ`).  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *status*  
 [out] L’état du champ BLOB.  
  
### <a name="bookmark_entry"></a> BOOKMARK_ENTRY
Lie la colonne de signet.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BOOKMARK_ENTRY(variable)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Variable*  
 [in] La variable doit être lié à la colonne de signet.  
  
#### <a name="example"></a>Exemple  

```cpp  
class CArtistsBookmark
{
public:
// Data Elements
   CBookmark<4> m_bookmark;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

// Output binding map
BEGIN_COLUMN_MAP(CArtistsBookmark)
   BOOKMARK_ENTRY(m_bookmark)
   COLUMN_ENTRY(1, m_nAge)
   COLUMN_ENTRY(2, m_szFirstName)
   COLUMN_ENTRY(3, m_szLastName)
END_COLUMN_MAP()

   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_BOOKMARKS, true);
   }

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsBookmark, L" \
   SELECT \
      Age, \
      FirstName, \
      LastName \
      FROM Artists")
};
```
  
#### <a name="see-also"></a>Voir aussi  
 [CBookmark, classe](../../data/oledb/cbookmark-class.md)   
 [DBPROP_BOOKMARKS](https://msdn.microsoft.com/library/ms709728.aspx)

### <a name="column_entry"></a> COLUMN_ENTRY
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY(nOrdinal, data)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) dans le *de référence du programmeur OLE DB*.  
  
 *nOrdinal*  
 [in] Le numéro de colonne.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
#### <a name="remarks"></a>Notes  
 La macro COLUMN_ENTRY sert aux emplacements suivants :  
  
-   Entre le [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.  
  
-   Entre le [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.  
  
-   Entre le [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.  
  
#### <a name="example"></a>Exemple  
 Consultez les exemples dans les rubriques de la macro, [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  

### <a name="column_entry_ex"></a> COLUMN_ENTRY_EX
Représente une liaison sur l’ensemble de lignes à la colonne dans la base de données.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) dans le *de référence du programmeur OLE DB*.  
  
 *nOrdinal*  
 [in] Le numéro de colonne.  
  
 *wType*  
 [in] Le type de données.  
  
 *nLength*  
 [in] La taille des données en octets.  
  
 *nPrecision*  
 [in] La précision maximale à utiliser lors de l’obtention des données et *wType* est `DBTYPE_NUMERIC`. Sinon, ce paramètre est ignoré.  
  
 *nScale*  
 [in] La mise à l’échelle à utiliser lors de l’obtention des données et *wType* est `DBTYPE_NUMERIC` ou `DBTYPE_DECIMAL`.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [in] La variable doit être lié à la longueur de colonne.  
  
 *status*  
 [in] La variable doit être lié à l’état de la colonne.  
  
#### <a name="remarks"></a>Notes  
 La macro COLUMN_ENTRY_EX sert aux emplacements suivants :  
  
-   Entre le [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.  
  
-   Entre le [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.  
  
-   Entre le [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.  
  
#### <a name="example"></a>Exemple  
 Consultez [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).  

### <a name="column_entry_length"></a> COLUMN_ENTRY_LENGTH
Représente une liaison sur l’ensemble de lignes à la colonne dans la base de données.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) dans le *de référence du programmeur OLE DB*.  
  
 *nOrdinal*  
 [in] Le numéro de colonne, en commençant par un. Signet correspond à la colonne zéro.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [in] La variable doit être lié à la longueur de colonne.  
  
#### <a name="remarks"></a>Notes  
 Cette macro prend en charge la *longueur* variable. Il est utilisé dans les emplacements suivants :  
  
-   Entre le [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.  
  
-   Entre le [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.  
  
-   Entre le [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.  
  
### <a name="column_entry_length_status"></a> COLUMN_ENTRY_LENGTH_STATUS
Représente une liaison sur l’ensemble de lignes à la colonne dans la base de données.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) dans le *de référence du programmeur OLE DB*.  
  
 *nOrdinal*  
 [in] Le numéro de colonne.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [in] La variable doit être lié à la longueur de colonne.  
  
 *status*  
 [in] La variable doit être lié à l’état de la colonne.  
  
#### <a name="remarks"></a>Notes  
 Utilisez cette macro, lorsque vous souhaitez prendre en charge les variables de longueur et l’état. Il est utilisé dans les emplacements suivants :  
  
-   Entre le [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.  
  
-   Entre le [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.  
  
-   Entre le [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.  

### <a name="column_entry_ps"></a> COLUMN_ENTRY_PS
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) dans le *de référence du programmeur OLE DB*.  
  
 *nOrdinal*  
 [in] Le numéro de colonne.  
  
 *nPrecision*  
 [in] La précision maximale de la colonne que vous souhaitez lier.  
  
 *nScale*  
 [in] La mise à l’échelle de la colonne que vous souhaitez lier.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
#### <a name="remarks"></a>Notes  
 Vous permet de spécifier la précision et l’échelle de la colonne que vous souhaitez lier. Il est utilisé dans les emplacements suivants :  
  
-   Entre le [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.  
  
-   Entre le [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.  
  
-   Entre le [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.  

### <a name="column_entry_ps_length"></a> COLUMN_ENTRY_PS_LENGTH
Représente une liaison sur l’ensemble de lignes à la colonne dans la base de données.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) dans le *de référence du programmeur OLE DB*.  
  
 *nOrdinal*  
 [in] Le numéro de colonne, en commençant par un. Signet correspond à la colonne zéro.  
  
 *nPrecision*  
 [in] La précision maximale de la colonne que vous souhaitez lier.  
  
 *nScale*  
 [in] La mise à l’échelle de la colonne que vous souhaitez lier.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [in] La variable doit être lié à la longueur de colonne.  
  
#### <a name="remarks"></a>Notes  
 Vous permet de spécifier la précision et l’échelle de la colonne que vous souhaitez lier. Cette macro prend en charge la *longueur* variable. Il est utilisé dans les emplacements suivants :  
  
-   Entre le [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.  
  
-   Entre le [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.  
  
-   Entre le [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.  

### <a name="column_entry_ps_length_status"></a> COLUMN_ENTRY_PS_LENGTH_STATUS
Représente une liaison sur l’ensemble de lignes à la colonne dans la base de données.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) dans le *de référence du programmeur OLE DB*.  
  
 *nOrdinal*  
 [in] Le numéro de colonne.  
  
 *nPrecision*  
 [in] La précision maximale de la colonne que vous souhaitez lier.  
  
 *nScale*  
 [in] La mise à l’échelle de la colonne que vous souhaitez lier.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [in] La variable doit être lié à la longueur de colonne.  
  
 *status*  
 [in] La variable doit être lié à l’état de la colonne.  
  
#### <a name="remarks"></a>Notes  
 Vous permet de spécifier la précision et l’échelle de la colonne que vous souhaitez lier. Utilisez cette macro, lorsque vous souhaitez prendre en charge les variables de longueur et l’état. Il est utilisé dans les emplacements suivants :  
  
-   Entre le [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.  
  
-   Entre le [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.  
  
-   Entre le [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.  

### <a name="column_entry_ps_status"></a> COLUMN_ENTRY_PS_STATUS
Représente une liaison sur l’ensemble de lignes à la colonne dans la base de données.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) dans le *de référence du programmeur OLE DB*.  
  
 *nOrdinal*  
 [in] Le numéro de colonne.  
  
 *nPrecision*  
 [in] La précision maximale de la colonne que vous souhaitez lier.  
  
 *nScale*  
 [in] La mise à l’échelle de la colonne que vous souhaitez lier.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *status*  
 [in] La variable doit être lié à l’état de la colonne.  
  
#### <a name="remarks"></a>Notes  
 Vous permet de spécifier la précision et l’échelle de la colonne que vous souhaitez lier. Cette macro prend en charge la *état* variable. Il est utilisé dans les emplacements suivants :  
  
-   Entre le [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.  
  
-   Entre le [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.  
  
-   Entre le [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.  
  
### <a name="column_entry_status"></a> COLUMN_ENTRY_STATUS
Représente une liaison sur l’ensemble de lignes à la colonne dans la base de données.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) dans le *de référence du programmeur OLE DB*.  
  
 *nOrdinal*  
 [in] Le numéro de colonne.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *status*  
 [in] La variable doit être lié à l’état de la colonne.  
  
#### <a name="remarks"></a>Notes  
 Cette macro prend en charge la *état* variable. Il est utilisé dans les emplacements suivants :  
  
-   Entre le [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.  
  
-   Entre le [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.  
  
-   Entre le [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.  

### <a name="column_entry_type"></a> COLUMN_ENTRY_TYPE
Représente une liaison à la colonne dans la base de données. Prend en charge *type* paramètre.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nOrdinal*  
 [in] Le numéro de colonne.  
  
 *wType*  
 [in] Type de données d’entrée de la colonne.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
#### <a name="remarks"></a>Notes  
 Cette macro est une variante spécialisée de la [COLUMN_ENTRY](../../data/oledb/column-entry.md) macro qui fournit un moyen de spécifier le type de données.  

### <a name="column_entry_type_size"></a> COLUMN_ENTRY_TYPE_SIZE
Représente une liaison à la colonne dans la base de données. Prend en charge *type* et *taille* paramètres.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nOrdinal*  
 [in] Le numéro de colonne.  
  
 *wType*  
 [in] Type de données d’entrée de la colonne.  
  
 *nLength*  
 [in] Taille de l’entrée de la colonne en octets.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
#### <a name="remarks"></a>Notes  
 Cette macro est une variante spécialisée de la [COLUMN_ENTRY](../../data/oledb/column-entry.md) macro qui fournit un moyen de spécifier la taille des données et type.  

### <a name="column_name"></a> COLUMN_NAME
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_ENTRY](../../data/oledb/column-entry.md), sauf que cette macro prend le nom de colonne au lieu du numéro de colonne.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME(pszName, data)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
#### <a name="remarks"></a>Notes  
 Les macros COLUMN_NAME_ * sont utilisées dans les mêmes emplacements que [COLUMN_ENTRY](../../data/oledb/column-entry.md):  
  
-   Entre le [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) et [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.  
  
-   Entre le [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) et [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.  
  
-   Entre le [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) et [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.  

### <a name="column_name_ex"></a> COLUMN_NAME_EX
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro accepte également le type de données, taille, précision, échelle, longueur de colonne et l’état de la colonne.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *wType*  
 [in] Le type de données.  
  
 *nLength*  
 [in] La taille des données en octets.  
  
 *nPrecision*  
 [in] La précision maximale à utiliser lors de l’obtention des données et *wType* est `DBTYPE_NUMERIC`. Sinon, ce paramètre est ignoré.  
  
 *nScale*  
 [in] La mise à l’échelle à utiliser lors de l’obtention des données et *wType* est `DBTYPE_NUMERIC` ou `DBTYPE_DECIMAL`.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [in] La variable doit être lié à la longueur de colonne.  
  
 *status*  
 [in] La variable doit être lié à l’état de la colonne.  
  
#### <a name="remarks"></a>Notes  
 Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour plus d’informations sur où les macros COLUMN_NAME_ * sont utilisées.  

### <a name="column_name_length"></a> COLUMN_NAME_LENGTH
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro accepte également la longueur de colonne.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_LENGTH(pszName, data, length)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [in] La variable doit être lié à la longueur de colonne.  
  
#### <a name="remarks"></a>Notes  
 Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour plus d’informations sur où les macros COLUMN_NAME_ * sont utilisées.  

### <a name="column_name_length_status"></a> COLUMN_NAME_LENGTH_STATUS
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro accepte également la longueur de colonne et l’état de la colonne.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [in] La variable doit être lié à la longueur de colonne.  
  
 *status*  
 [in] La variable doit être lié à l’état de la colonne.  
  
#### <a name="remarks"></a>Notes  
 Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour plus d’informations sur où les macros COLUMN_NAME_ * sont utilisées.  

### <a name="column_name_ps"></a> COLUMN_NAME_PS
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro accepte également la précision et l’échelle.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *nPrecision*  
 [in] La précision maximale de la colonne que vous souhaitez lier.  
  
 *nScale*  
 [in] La mise à l’échelle de la colonne que vous souhaitez lier.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
#### <a name="remarks"></a>Notes  
 Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour plus d’informations sur où les macros COLUMN_NAME_ * sont utilisées.  

### <a name="column_name_ps_length"></a> COLUMN_NAME_PS_LENGTH
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro accepte également la précision, échelle et colonne de longueur.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *nPrecision*  
 [in] La précision maximale de la colonne que vous souhaitez lier.  
  
 *nScale*  
 [in] La mise à l’échelle de la colonne que vous souhaitez lier.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [in] La variable doit être lié à la longueur de colonne.  
  
#### <a name="remarks"></a>Notes  
 Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour plus d’informations sur où les macros COLUMN_NAME_ * sont utilisées.  

### <a name="column_name_ps_length_status"></a> COLUMN_NAME_PS_LENGTH_STATUS
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro accepte également la précision, échelle, longueur de colonne et état de la colonne.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *nPrecision*  
 [in] La précision maximale de la colonne que vous souhaitez lier.  
  
 *nScale*  
 [in] La mise à l’échelle de la colonne que vous souhaitez lier.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *length*  
 [in] La variable doit être lié à la longueur de colonne.  
  
 *status*  
 [in] La variable doit être lié à l’état de la colonne.  
  
#### <a name="remarks"></a>Notes  
 Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour plus d’informations sur où les macros COLUMN_NAME_ * sont utilisées.  

### <a name="column_name_ps_status"></a> COLUMN_NAME_PS_STATUS
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également l’état de précision, échelle et de colonne.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *nPrecision*  
 [in] La précision maximale de la colonne que vous souhaitez lier.  
  
 *nScale*  
 [in] La mise à l’échelle de la colonne que vous souhaitez lier.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *status*  
 [in] La variable doit être lié à l’état de la colonne.  
  
#### <a name="remarks"></a>Notes  
 Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour plus d’informations sur où les macros COLUMN_NAME_ * sont utilisées.  

### <a name="column_name_status"></a> COLUMN_NAME_STATUS
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro accepte également l’état de la colonne.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_STATUS(pszName, data, status )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
 *status*  
 [in] La variable doit être lié à l’état de la colonne.  
  
#### <a name="remarks"></a>Notes  
 Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour plus d’informations sur où les macros COLUMN_NAME_ * sont utilisées.  

### <a name="column_name_type"></a> COLUMN_NAME_TYPE
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro prend également le type de données.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_TYPE(pszName, wType, data)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *wType*  
 [in] Le type de données.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
#### <a name="remarks"></a>Notes  
 Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour plus d’informations sur où les macros COLUMN_NAME_ * sont utilisées.  

### <a name="column_name_type_ps"></a> COLUMN_NAME_TYPE_PS
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro accepte également le type de données, la précision et l’échelle.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *wType*  
 [in] Le type de données.  
  
 *nPrecision*  
 [in] La précision maximale à utiliser lors de l’obtention des données et *wType* est `DBTYPE_NUMERIC`. Sinon, ce paramètre est ignoré.  
  
 *nScale*  
 [in] La mise à l’échelle à utiliser lors de l’obtention des données et *wType* est `DBTYPE_NUMERIC` ou `DBTYPE_DECIMAL`.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
#### <a name="remarks"></a>Notes  
 Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour plus d’informations sur où les macros COLUMN_NAME_ * sont utilisées.  

### <a name="column_name_type_size"></a> COLUMN_NAME_TYPE_SIZE
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro accepte également le type de données et la taille.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *wType*  
 [in] Le type de données.  
  
 *nLength*  
 [in] La taille des données en octets.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
#### <a name="remarks"></a>Notes  
 Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour plus d’informations sur où les macros COLUMN_NAME_ * sont utilisées.  

### <a name="column_name_type_status"></a> COLUMN_NAME_TYPE_STATUS
Représente une liaison sur l’ensemble de lignes à la colonne dans l’ensemble de lignes. Semblable à [COLUMN_NAME](../../data/oledb/column-name.md), sauf que cette macro accepte également l’état de type et à la colonne de données.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pszName*  
 [in] Pointeur vers le nom de colonne. Le nom doit être une chaîne Unicode. Vous pouvez accomplir cela en plaçant un « L » devant le nom, par exemple : `L"MyColumn"`.  
  
 *wType*  
 [in] Le type de données.  
  
 *status*  
 [in] La variable doit être lié à l’état de la colonne.  
  
 *data*  
 [in] Le membre de données correspondant dans l’enregistrement utilisateur.  
  
#### <a name="remarks"></a>Notes  
 Consultez [COLUMN_NAME](../../data/oledb/column-name.md) pour plus d’informations sur où les macros COLUMN_NAME_ * sont utilisées.  

### <a name="end_column_map"></a> END_COLUMN_MAP
Marque la fin des entrées de mappage de colonne.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
END_COLUMN_MAP()  
  
```  
  
#### <a name="remarks"></a>Notes  
 Il est utilisé avec un seul accesseur sur un ensemble de lignes. La macro BEGIN_COLUMN_MAP s’est terminée avec l’END_COLUMN_MAP (macro).  
  
#### <a name="example"></a>Exemple  
 Consultez [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).  

### <a name="define_command"></a> DEFINE_COMMAND
Spécifie la commande permettant de créer l’ensemble de lignes lorsque vous utilisez le [CCommand](../../data/oledb/ccommand-class.md) classe. Accepte uniquement les types de chaîne correspondant au type d’application spécifiée (ANSI ou Unicode).  
  
> [!NOTE]
>  Il est recommandé d’utiliser [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) au lieu de DEFINE_COMMAND.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
DEFINE_COMMAND(x, szCommand)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *x*  
 [in] Le nom de la classe d’enregistrement (commande) utilisateur.  
  
 *szCommand*  
 [in] La chaîne de commande permettant de créer l’ensemble de lignes lors de l’utilisation [CCommand](../../data/oledb/ccommand-class.md).  
  
#### <a name="remarks"></a>Notes  
 La chaîne de commande que vous spécifiez sera être utilisée en tant que la valeur par défaut si vous ne spécifiez pas de texte de la commande dans le [CCommand::Open](../../data/oledb/ccommand-open.md) (méthode).  
  
 Cette macro accepte ANSI si vous générez votre application comme étant ANSI, ou des chaînes Unicode si vous générez votre application au format Unicode. Il est recommandé d’utiliser [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) au lieu de DEFINE_COMMAND, étant donné que l’ancienne base de données accepte les chaînes Unicode, quel que soit le type d’application ANSI ou Unicode.  
  
#### <a name="example"></a>Exemple  
 Consultez [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).  

### <a name="define_command_ex"></a> DEFINE_COMMAND_EX
Spécifie la commande permettant de créer l’ensemble de lignes lorsque vous utilisez le [CCommand](../../data/oledb/ccommand-class.md) classe. Prend en charge les applications Unicode et ANSI.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
DEFINE_COMMAND_EX(x, wszCommand)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *x*  
 [in] Le nom de la classe d’enregistrement (commande) utilisateur.  
  
 *wszCommand*  
 [in] La chaîne de commande permettant de créer l’ensemble de lignes lors de l’utilisation [CCommand](../../data/oledb/ccommand-class.md).  
  
#### <a name="remarks"></a>Notes  
 La chaîne de commande que vous spécifiez sera être utilisée en tant que la valeur par défaut si vous ne spécifiez pas de texte de la commande dans le [CCommand::Open](../../data/oledb/ccommand-open.md) (méthode).  
  
 Cette macro accepte les chaînes Unicode, quel que soit le type d’application. Cette macro est préférée sur [DEFINE_COMMAND](../../data/oledb/define-command.md) , car il prend en charge Unicode, ainsi que les applications ANSI.  
  
#### <a name="example"></a>Exemple  
 Consultez [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).  

### <a name="begin_param_map"></a> BEGIN_PARAM_MAP
Marque le début des entrées de mappage de paramètre.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BEGIN_PARAM_MAP(x)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *x*  
 [in] Nom de la classe d’enregistrement utilisateur.  
  
#### <a name="remarks"></a>Notes  
 Paramètres sont utilisés par [commandes](https://msdn.microsoft.com/library/ms724608.aspx).  
  
#### <a name="example"></a>Exemple  
 Consultez l’exemple de la [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) macro.  

### <a name="end_param_map"></a> END_PARAM_MAP
Marque la fin des entrées de mappage de paramètre.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
END_PARAM_MAP()  
  
```  
  
#### <a name="example"></a>Exemple  
 Consultez l’exemple de la [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) macro.  
  
### <a name="set_param_type"></a> SET_PARAM_TYPE
Spécifie les macros COLUMN_ENTRY qui suivent l’entrée de la macro SET_PARAM_TYPE, sortie ou d’entrée/sortie.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
SET_PARAM_TYPE(type)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 *type*  
 [in] Type à définir pour le paramètre.  
  
#### <a name="remarks"></a>Notes  
 Les fournisseurs prennent en charge uniquement les types d’entrée/sortie de paramètres qui sont pris en charge par la source de données sous-jacente. Le type est une combinaison d’une ou plusieurs `DBPARAMIO` valeurs (voir [Structures DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) dans le *de référence du programmeur OLE DB*) :  
  
-   `DBPARAMIO_NOTPARAM` L’accesseur n’a aucun paramètre. En règle générale, vous définissez `eParamIO` à cette valeur dans les accesseurs de ligne pour rappeler à l’utilisateur que les paramètres sont ignorés.  
  
-   `DBPARAMIO_INPUT` Un paramètre d’entrée.  
  
-   `DBPARAMIO_OUTPUT` Un paramètre de sortie.  
  
-   `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT` Le paramètre est une entrée et un paramètre de sortie.  
  
#### <a name="example"></a>Exemple  
```cpp  
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
``` 

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et fonctions globales pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)    
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)    
