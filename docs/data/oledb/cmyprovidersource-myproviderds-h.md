---
title: CMyProviderSource (MyProviderDS.H) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- myproviderds.h
- cmyprovidersource
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f141ad7565a78ff4e7a02b3847287879b81ccd6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098652"
---
# <a name="cmyprovidersource-myproviderdsh"></a>CMyProviderSource (MyProviderDS.H)
Les classes de fournisseur utilisent l’héritage multiple. Le code suivant montre la chaîne d’héritage de l’objet de source de données :  
  
```cpp
/////////////////////////////////////////////////////////////////////////  
// CMyProviderSource  
class ATL_NO_VTABLE CMyProviderSource :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public CComCoClass<CMyProviderSource, &CLSID_MyProvider>,  
   public IDBCreateSessionImpl<CMyProviderSource, CMyProviderSession>,  
   public IDBInitializeImpl<CMyProviderSource>,  
   public IDBPropertiesImpl<CMyProviderSource>,  
   public IPersistImpl<CMyProviderSource>,  
   public IInternalConnectionImpl<CMyProviderSource>  
```  
  
 Tous les composants COM dérivent `CComObjectRootEx` et `CComCoClass`. `CComObjectRootEx` fournit toute l’implémentation pour la **IUnknown** interface. Il peut gérer n’importe quel modèle de thread. `CComCoClass` gère toute prise en charge de l’erreur requise. Si vous souhaitez envoyer des informations plus détaillées sur l’erreur au client, vous pouvez utiliser certaines API d’erreurs dans `CComCoClass`.  
  
 L’objet de source de données hérite également de plusieurs classes de 'Impl'. Chaque classe fournit l’implémentation d’une interface. La source de données objet implémente le `IPersist`, `IDBProperties`, **IDBInitialize**, et **IDBCreateSession** interfaces. OLE DB exige que chaque interface implémente l’objet de source de données. Vous pouvez choisir de prendre en charge ou prennent pas en charge les fonctionnalités particulières en héritant ou non à partir d’une de ces classes 'Impl'. Si vous souhaitez prendre en charge la **IDBDataSourceAdmin** interface, vous héritez de la **IDBDataSourceAdminImpl** classe pour obtenir les fonctionnalités requises.  
  
## <a name="com-map"></a>Mappage COM  
 Chaque fois que le client appelle `QueryInterface` pour une interface sur la source de données, il parcourt le mappage COM suivant :  
  
```  
BEGIN_COM_MAP(CMyProviderSource)  
   COM_INTERFACE_ENTRY(IDBCreateSession)  
   COM_INTERFACE_ENTRY(IDBInitialize)  
   COM_INTERFACE_ENTRY(IDBProperties)  
   COM_INTERFACE_ENTRY(IPersist)  
   COM_INTERFACE_ENTRY(IInternalConnection)  
END_COM_MAP()  
```  
  
 Les macros COM_INTERFACE_ENTRY sont issues d’ATL et indiquent à l’implémentation de `QueryInterface` dans `CComObjectRootEx` pour retourner les interfaces appropriées.  
  
## <a name="property-map"></a>Mappages de propriété  
 Le mappage de propriété spécifie toutes les propriétés désignées par le fournisseur :  
  
```  
BEGIN_PROPSET_MAP(CMyProviderSource)  
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
   CHAIN_PROPERTY_SET(CMyProviderSession)  
END_PROPSET_MAP()  
```  
  
 Dans OLE DB, les propriétés sont groupées. L’objet de source de données possède deux groupes de propriétés : un pour le **DBPROPSET_DATASOURCEINFO** ensemble et l’autre pour le **DBPROPSET_DBINIT** définie. Le **DBPROPSET_DATASOURCEINFO** jeu correspond aux propriétés sur le fournisseur et sa source de données. Le **DBPROPSET_DBINIT** ensemble correspond aux propriétés utilisées lors de l’initialisation. Les modèles du fournisseur OLE DB gèrent ces jeux à l’aide des macros PROPERTY_SET. Les macros créent un bloc qui contient un tableau de propriétés. Chaque fois que le client appelle le `IDBProperties` interface, le fournisseur utilise le mappage de propriété.  
  
 Vous n’avez pas besoin d’implémenter chaque propriété dans la spécification. Toutefois, vous devez prendre en charge les propriétés requises ; consultez la spécification de mise en conformité de niveau 0 pour plus d’informations. Si vous ne souhaitez pas prendre en charge une propriété, vous pouvez le supprimer à partir de la carte. Si vous souhaitez prendre en charge une propriété, ajoutez-la dans la table à l’aide d’une macro PROPERTY_INFO_ENTRY. La macro correspond à la **UPROPINFO** structure comme indiqué dans le code suivant :  
  
```  
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
  
 Chaque élément de la structure représente des informations permettant de gérer la propriété. Il contient un **DBPROPID** pour déterminer le GUID et l’ID de la propriété. Il contient également des entrées pour déterminer le type et la valeur de la propriété.  
  
 Si vous souhaitez modifier la valeur par défaut d’une propriété (Notez qu’un consommateur peut modifier la valeur d’une propriété accessible en écriture à tout moment), vous pouvez utiliser soit la macro PROPERTY_INFO_ENTRY_VALUE ou PROPERTY_INFO_ENTRY_EX. Ces macros permettent de spécifier une valeur pour une propriété correspondante. La macro PROPERTY_INFO_ENTRY_VALUE est une notation abrégée qui vous permet de modifier la valeur. La macro PROPERTY_INFO_ENTRY_VALUE appelle la macro PROPERTY_INFO_ENTRY_EX. Cette macro permet d’ajouter ou modifier tous les attributs dans le **UPROPINFO** structure.  
  
 Si vous souhaitez définir votre propre jeu de propriétés, vous pouvez ajouter un en créant une combinaison BEGIN_PROPSET_MAP/END_PROPSET_MAP supplémentaire. Vous devez définir un GUID pour le jeu de propriétés, puis définissez vos propres propriétés. Si vous avez des propriétés spécifiques au fournisseur, les ajouter à une nouvelle propriété définie au lieu d’utiliser un existant. Cela évite les problèmes dans les versions ultérieures d’OLE DB.  
  
## <a name="user-defined-property-sets"></a>Jeux de propriétés défini par l’utilisateur  
 Visual C++ prend en charge les ensembles de propriétés défini par l’utilisateur. Vous n’êtes pas obligé de remplacer **GetProperties** ou `GetPropertyInfo`. Au lieu de cela, les modèles détectent tout jeu de propriétés défini par l’utilisateur et l’ajouter à l’objet approprié.  
  
 Si vous avez un jeu de propriétés défini par l’utilisateur qui doit être disponible au moment de l’initialisation (autrement dit, avant que le consommateur appelle **IDBInitialize::Initialize**), vous pouvez le spécifier à l’aide de la **UPROPSET_USERINIT** indicateur conjointement avec la macro BEGIN_PROPERTY_SET_EX. Le jeu de propriétés doit être dans l’objet de source de données pour que cela fonctionne (comme la spécification OLE DB exige). Par exemple :  
  
```  
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)  
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)  
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers générés par l’Assistant Fournisseur](../../data/oledb/provider-wizard-generated-files.md)