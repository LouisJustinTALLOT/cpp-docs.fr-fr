---
title: CDataSource::Open | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: a6d28bd1-799a-48ed-8993-5f82d1705b77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3196aa89426e895dd6b73b28ce197e8f271a0262
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097066"
---
# <a name="cdatasourceopen"></a>CDataSource::Open
Ouvre une connexion à une source de données à l’aide un **CLSID**, **ProgID**, ou `CEnumerator` moniker ou invite l’utilisateur avec une boîte de dialogue de recherche.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Open(const CLSID& clsid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();  


HRESULT Open(const CLSID& clsid,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();HRESULT Open(LPCTSTR szProgID,  
  DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();HRESULT Open(LPCTSTR szProgID,  
   LPCTSTR pName,  LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();  

HRESULT Open(const CEnumerator& enumerator,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();  

HRESULT Open(const CEnumerator& enumerator,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();  

HRESULT Open(HWND hWnd = GetActiveWindow(),  
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET) throw();

HRESULT Open(LPCWSTR szProgID,   
  DBPROPSET* pPropSet = NULL,   
   ULONG nPropertySets = 1) throw();

HRESULT Open(LPCSTR szProgID,   
   LPCTSTR pName,LPCTSTR pUserName = NULL,   
   LPCTSTR pPassword = NULL,   
   long nInitMode = 0) throw();  
```  
  
#### <a name="parameters"></a>Paramètres  
 `clsid`  
 [in] Le **CLSID** du fournisseur de données.  
  
 *pPropSet*  
 [in] Un pointeur vers un tableau de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) les structures contenant des propriétés et valeurs à définir. Consultez [jeux de propriétés et des groupes de propriétés](https://msdn.microsoft.com/en-us/library/ms713696.aspx) dans les *de référence du programmeur OLE DB* dans le Kit de développement logiciel Windows.  
  
 *nPropertySets*  
 [in] Le nombre de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) structures passées dans le *pPropSet* argument.  
  
 *pName*  
 [in] Nom de la base de données à laquelle se connecter.  
  
 *pUserName*  
 [in] Nom de l'utilisateur.  
  
 *pPassword*  
 [in] Mot de passe de l'utilisateur.  
  
 `nInitMode`  
 [in] Mode d'initialisation de la base de données. Consultez [propriétés d’initialisation](https://msdn.microsoft.com/en-us/library/ms723127.aspx)dans les *de référence du programmeur OLE DB* dans le SDK Windows pour obtenir la liste des modes d’initialisation valides. Si `nInitMode` est égal à zéro, aucun mode d'initialisation n'est inclus dans le jeu de propriétés utilisé pour ouvrir la connexion.  
  
 `szProgID`  
 [in] Identificateur de programme.  
  
 `enumerator`  
 [in] A [CEnumerator](../../data/oledb/cenumerator-class.md) objet utilisé pour obtenir un moniker pour ouvrir la connexion lorsque l’appelant ne spécifie pas un **CLSID**.  
  
 `hWnd`  
 [in] Handle de fenêtre devant être le parent de la boîte de dialogue. L'utilisation de la surcharge de fonction avec le paramètre `hWnd` a pour effet d'appeler automatiquement les composants de service ; consultez les Notes pour plus d'informations.  
  
 `dwPromptOptions`  
 [in] Détermine le style de la boîte de dialogue de recherche à afficher. Consultez Msdasc.h pour connaître les valeurs possibles.  
  
## <a name="return-value"></a>Valeur de retour  
 `HRESULT` standard.  
  
## <a name="remarks"></a>Notes  
 La surcharge de méthode qui utilise le paramètre `hWnd` ouvre un objet source de données à l'aide des composants de service d'oledb32.dll ; cette DLL contient l'implémentation des fonctionnalités Composants de service telles que la mise en pool de ressources, l'inscription de transaction automatique, etc. Pour plus d’informations, consultez « Services OLE DB » dans la référence du programmeur OLE DB à l’adresse [ http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
 Les surcharges de méthode qui n'utilisent pas le paramètre `hWnd` ouvrent un objet source de données sans utiliser les composants de service dans oledb32.dll. A [CDataSource](../../data/oledb/cdatasource-class.md) objet ouvert avec ces surcharges de fonction ne pourra pas utiliser aucune des fonctionnalités de composants de Service.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment ouvrir une source de données Jet 4.0 avec les modèles OLE DB. Même si vous traitez la source de données Jet comme une source de données OLE DB, Toutefois, votre appel à **ouvrir** a besoin de deux jeux de propriétés : un pour **DBPROPSET_DBINIT** et l’autre pour **DBPROPSET_JETOLEDB_DBINIT**, afin que vous puissiez définir  **DBPROP_JETOLEDB_DATABASEPASSWORD**.  
  
 [!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [CDataSource, classe](../../data/oledb/cdatasource-class.md)
