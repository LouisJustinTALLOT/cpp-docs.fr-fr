---
title: CMyProviderSource (MyProviderDS.H) | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- myproviderds.h
- cmyprovidersource
- customds.h
- ccustomsource
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
- CCustomSource class in CustomDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 47a09aa9a368741dfd4c95bb86f22d09bc11e1b8
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808275"
---
# <a name="ccustomclasssource-customclassdsh"></a>CCustomClassSource (CustomClassDS.h)

Les classes de fournisseur utilisent l’héritage multiple. Le code suivant montre la chaîne d’héritage de l’objet de source de données :  
  
```cpp
/////////////////////////////////////////////////////////////////////////  
// CCustomSource  
class ATL_NO_VTABLE CCustomSource :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public CComCoClass<CCustomSource, &CLSID_Custom>,  
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,  
   public IDBInitializeImpl<CCustomSource>,  
   public IDBPropertiesImpl<CCustomSource>,  
   public IPersistImpl<CCustomSource>,  
   public IInternalConnectionImpl<CCustomSource>  
```  
  
Tous les composants COM dérivent `CComObjectRootEx` et `CComCoClass`. `CComObjectRootEx` fournit toute l’implémentation pour le `IUnknown` interface. Il peut gérer n’importe quel modèle de thread. `CComCoClass` gère toute prise en charge de l’erreur requise. Si vous souhaitez envoyer des informations d’erreur plus détaillées au client, vous pouvez utiliser certaines API d’erreurs dans `CComCoClass`.  
  
L’objet de source de données hérite également de plusieurs classes de 'Impl'. Chaque classe fournit l’implémentation pour une interface. La source de données objet implémente le `IPersist`, `IDBProperties`, `IDBInitialize`, et `IDBCreateSession` interfaces. Chaque interface est requise par OLE DB pour mettre en œuvre de l’objet de source de données. Vous pouvez choisir de prendre en charge ou la prend pas en charge des fonctionnalités particulières en héritant ou non à partir d’une de ces classes de 'Impl'. Si vous souhaitez prendre en charge la `IDBDataSourceAdmin` interface, vous héritez de la `IDBDataSourceAdminImpl` classe pour obtenir les fonctionnalités requises.  
  
## <a name="com-map"></a>Mappage COM  

Chaque fois que le client appelle `QueryInterface` pour une interface sur la source de données, qu’il traverse le mappage COM suivant :  
  
```cpp  
BEGIN_COM_MAP(CCustomSource)  
   COM_INTERFACE_ENTRY(IDBCreateSession)  
   COM_INTERFACE_ENTRY(IDBInitialize)  
   COM_INTERFACE_ENTRY(IDBProperties)  
   COM_INTERFACE_ENTRY(IPersist)  
   COM_INTERFACE_ENTRY(IInternalConnection)  
END_COM_MAP()  
```  
  
Les macros COM_INTERFACE_ENTRY sont issues d’ATL et indiquent à l’implémentation de `QueryInterface` dans `CComObjectRootEx` pour retourner les interfaces appropriées.  
  
## <a name="property-map"></a>Mappage des propriétés  

Le mappage des propriétés spécifie toutes les propriétés désignées par le fournisseur :  
  
```cpp  
BEGIN_PROPSET_MAP(CCustomSource)  
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)  
      PROPERTY_INFO_ENTRY(ACTIVESESSIONS)  
      PROPERTY_INFO_ENTRY(ASYNCTXNABORT)  
      PROPERTY_INFO_ENTRY(ASYNCTXNCOMMIT)  
      PROPERTY_INFO_ENTRY(BYREFACCESSORS)  
      PROPERTY_INFO_ENTRY_VALUE(CATALOGLOCATION, DBPROPVAL_CL_START)  
      PROPERTY_INFO_ENTRY(CATALOGTERM)  
      PROPERTY_INFO_ENTRY(CATALOGUSAGE)  
      PROPERTY_INFO_ENTRY(COLUMNDEFINITION)  
      PROPERTY_INFO_ENTRY(CONCATNULLBEHAVIOR)  
      PROPERTY_INFO_ENTRY(DATASOURCENAME)  
      PROPERTY_INFO_ENTRY(DATASOURCEREADONLY)  
      PROPERTY_INFO_ENTRY(DBMSNAME)  
      PROPERTY_INFO_ENTRY(DBMSVER)  
      PROPERTY_INFO_ENTRY_VALUE(DSOTHREADMODEL, DBPROPVAL_RT_FREETHREAD)  
      PROPERTY_INFO_ENTRY(GROUPBY)  
      PROPERTY_INFO_ENTRY(HETEROGENEOUSTABLES)  
      PROPERTY_INFO_ENTRY(IDENTIFIERCASE)  
      PROPERTY_INFO_ENTRY(MAXINDEXSIZE)  
      PROPERTY_INFO_ENTRY(MAXROWSIZE)  
      PROPERTY_INFO_ENTRY(MAXROWSIZEINCLUDESBLOB)  
      PROPERTY_INFO_ENTRY(MAXTABLESINSELECT)  
      PROPERTY_INFO_ENTRY(MULTIPLEPARAMSETS)  
      PROPERTY_INFO_ENTRY(MULTIPLERESULTS)  
      PROPERTY_INFO_ENTRY(MULTIPLESTORAGEOBJECTS)  
      PROPERTY_INFO_ENTRY(MULTITABLEUPDATE)  
      PROPERTY_INFO_ENTRY(NULLCOLLATION)  
      PROPERTY_INFO_ENTRY(OLEOBJECTS)  
      PROPERTY_INFO_ENTRY(ORDERBYCOLUMNSINSELECT)  
      PROPERTY_INFO_ENTRY(OUTPUTPARAMETERAVAILABILITY)  
      PROPERTY_INFO_ENTRY(PERSISTENTIDTYPE)  
      PROPERTY_INFO_ENTRY(PREPAREABORTBEHAVIOR)  
      PROPERTY_INFO_ENTRY(PREPARECOMMITBEHAVIOR)  
      PROPERTY_INFO_ENTRY(PROCEDURETERM)  
      PROPERTY_INFO_ENTRY(PROVIDERNAME)  
      PROPERTY_INFO_ENTRY(PROVIDEROLEDBVER)  
      PROPERTY_INFO_ENTRY(PROVIDERVER)  
      PROPERTY_INFO_ENTRY(QUOTEDIDENTIFIERCASE)  
      PROPERTY_INFO_ENTRY(ROWSETCONVERSIONSONCOMMAND)  
      PROPERTY_INFO_ENTRY(SCHEMATERM)  
      PROPERTY_INFO_ENTRY(SCHEMAUSAGE)  
      PROPERTY_INFO_ENTRY(STRUCTUREDSTORAGE)  
      PROPERTY_INFO_ENTRY(SUBQUERIES)  
      PROPERTY_INFO_ENTRY(TABLETERM)  
      PROPERTY_INFO_ENTRY(USERNAME)  
   END_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)  
   BEGIN_PROPERTY_SET(DBPROPSET_DBINIT)  
      PROPERTY_INFO_ENTRY(AUTH_PASSWORD)  
      PROPERTY_INFO_ENTRY(AUTH_PERSIST_SENSITIVE_AUTHINFO)  
      PROPERTY_INFO_ENTRY(AUTH_USERID)  
      PROPERTY_INFO_ENTRY(INIT_DATASOURCE)  
      PROPERTY_INFO_ENTRY(INIT_HWND)  
      PROPERTY_INFO_ENTRY(INIT_LCID)  
      PROPERTY_INFO_ENTRY(INIT_LOCATION)  
      PROPERTY_INFO_ENTRY(INIT_MODE)  
      PROPERTY_INFO_ENTRY(INIT_PROMPT)  
      PROPERTY_INFO_ENTRY(INIT_PROVIDERSTRING)  
      PROPERTY_INFO_ENTRY(INIT_TIMEOUT)  
   END_PROPERTY_SET(DBPROPSET_DBINIT)  
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCE)  
      PROPERTY_INFO_ENTRY(CURRENTCATALOG)  
   END_PROPERTY_SET(DBPROPSET_DATASOURCE)  
   CHAIN_PROPERTY_SET(CCustomSession)  
END_PROPSET_MAP()  
```  
  
Dans OLE DB, les propriétés sont groupées. L’objet de source de données possède deux groupes de propriétés : une pour le jeu DBPROPSET_DATASOURCEINFO définie et une pour le jeu DBPROPSET_DBINIT définie. Le jeu DBPROPSET_DATASOURCEINFO correspond aux propriétés sur le fournisseur et sa source de données. Le jeu DBPROPSET_DBINIT correspond aux propriétés utilisées lors de l’initialisation. Les modèles du fournisseur OLE DB gèrent ces jeux à l’aide des macros PROPERTY_SET. Les macros de créent un bloc qui contient un tableau de propriétés. Chaque fois que le client appelle le `IDBProperties` interface, le fournisseur utilise le mappage de propriété.  
  
Vous n’avez pas besoin d’implémenter chaque propriété dans la spécification. Toutefois, vous devez prendre en charge les propriétés requises ; consultez la spécification de la conformité de niveau 0 pour plus d’informations. Si vous ne souhaitez pas prendre en charge une propriété, vous pouvez le supprimer à partir de la carte. Si vous souhaitez prendre en charge une propriété, ajoutez-le dans le mappage à l’aide d’une macro PROPERTY_INFO_ENTRY. La macro correspond à la `UPROPINFO` structure comme indiqué dans le code suivant :  
  
```cpp  
struct UPROPINFO  
{  
   DBPROPID    dwPropId;  
   ULONG       ulIDS;  
   VARTYPE     VarType;  
   DBPROPFLAGS dwFlags;  
   union  
   {  
      DWORD dwVal;  
      LPOLESTR szVal;  
   };  
   DBPROPOPTIONS dwOption;  
};  
```  
  
Chaque élément dans la structure représente des informations pour gérer la propriété. Il contient un `DBPROPID` pour déterminer le GUID et l’ID de la propriété. Il contient également des entrées pour déterminer le type et la valeur de la propriété.  
  
Si vous souhaitez modifier la valeur par défaut d’une propriété (Notez qu’un consommateur peut modifier la valeur d’une propriété accessible en écriture à tout moment), vous pouvez utiliser le PROPERTY_INFO_ENTRY_VALUE ou PROPERTY_INFO_ENTRY_EX (macro). Ces macros permettent de spécifier une valeur pour une propriété correspondante. La macro PROPERTY_INFO_ENTRY_VALUE est une notation raccourcie qui vous permet de modifier la valeur. La macro PROPERTY_INFO_ENTRY_VALUE appelle la macro PROPERTY_INFO_ENTRY_EX. Cette macro vous permet d’ajouter ou modifier tous les attributs dans le `UPROPINFO` structure.  
  
Si vous souhaitez définir votre propre jeu de propriétés, vous pouvez ajouter un en créant une combinaison BEGIN_PROPSET_MAP/END_PROPSET_MAP supplémentaire. Vous devez définir un GUID pour le jeu de propriétés, puis définissez vos propres propriétés. Si vous avez des propriétés spécifiques au fournisseur, ajoutez-les à une nouvelle propriété au lieu d’utiliser un existant. Cela évite tout problème dans les versions ultérieures d’OLE DB.  
  
## <a name="user-defined-property-sets"></a>Jeux de propriétés définies par l’utilisateur  

Visual C++ prend en charge les jeux de propriétés définies par l’utilisateur. Vous n’êtes pas obligé de substituer `GetProperties` ou `GetPropertyInfo`. Au lieu de cela, les modèles de détectent tout jeu de propriétés défini par l’utilisateur et l’ajouter à l’objet approprié.  
  
Si vous avez un ensemble de propriétés défini par l’utilisateur qui doit être disponible au moment de l’initialisation (autrement dit, avant que le consommateur appelle `IDBInitialize::Initialize`), vous pouvez le spécifier à l’aide de l’indicateur UPROPSET_USERINIT conjointement avec la macro BEGIN_PROPERTY_SET_EX. Le jeu de propriétés doit être dans l’objet de source de données pour ce faire (comme la spécification OLE DB exige). Exemple :  
  
```cpp  
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)  
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)  
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)  
```  
  
## <a name="see-also"></a>Voir aussi  

[Fichiers générés par l’Assistant Fournisseur](../../data/oledb/provider-wizard-generated-files.md)