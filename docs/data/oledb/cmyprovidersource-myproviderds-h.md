---
description: 'En savoir plus sur : CCustomSource (CustomDS. h)'
title: CCustomSource (CustomDS.H)
ms.date: 10/22/2018
f1_keywords:
- myproviderds.h
- cmyprovidersource
- customds.h
- ccustomsource
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
- CCustomSource class in CustomDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
ms.openlocfilehash: 6fbb9fe0676521b01caa3bba5f5bb2be03d0fe6f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170436"
---
# <a name="ccustomsource-customdsh"></a>CCustomSource (CustomDS. h)

Les classes de fournisseur utilisent l’héritage multiple. Le code suivant montre la chaîne d’héritage pour l’objet source de données :

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

Tous les composants COM dérivent de `CComObjectRootEx` et `CComCoClass` . `CComObjectRootEx` fournit toute l’implémentation pour l' `IUnknown` interface. Il peut gérer n’importe quel modèle de thread. `CComCoClass` gère toute prise en charge des erreurs requise. Si vous souhaitez envoyer des informations plus détaillées sur l’erreur au client, vous pouvez utiliser certaines API d’erreur dans `CComCoClass` .

L’objet source de données hérite également de plusieurs classes’impl'. Chaque classe fournit l’implémentation d’une interface. L’objet de source de données implémente les `IPersist` interfaces,, `IDBProperties` `IDBInitialize` et `IDBCreateSession` . Chaque interface est requise par OLE DB pour implémenter l’objet source de données. Vous pouvez choisir de prendre en charge ou de ne pas prendre en charge des fonctionnalités particulières en héritant ou non de l’une de ces classes’impl'. Si vous souhaitez prendre en charge l' `IDBDataSourceAdmin` interface, vous héritez de la `IDBDataSourceAdminImpl` classe pour obtenir les fonctionnalités requises.

## <a name="com-map"></a>Mappage COM

Chaque fois que le client appelle `QueryInterface` pour une interface sur la source de données, il passe par le mappage com suivant :

```cpp
BEGIN_COM_MAP(CCustomSource)
   COM_INTERFACE_ENTRY(IDBCreateSession)
   COM_INTERFACE_ENTRY(IDBInitialize)
   COM_INTERFACE_ENTRY(IDBProperties)
   COM_INTERFACE_ENTRY(IPersist)
   COM_INTERFACE_ENTRY(IInternalConnection)
END_COM_MAP()
```

Les macros COM_INTERFACE_ENTRY proviennent d’ATL et indiquent à l’implémentation de `QueryInterface` dans de `CComObjectRootEx` retourner les interfaces appropriées.

## <a name="property-map"></a>Mappage de propriété

Le mappage de propriété spécifie toutes les propriétés assignées par le fournisseur :

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

Les propriétés des OLE DB sont regroupées. L’objet de source de données possède deux groupes de propriétés : une pour le jeu de DBPROPSET_DATASOURCEINFO et une pour le jeu de DBPROPSET_DBINIT. Le jeu de DBPROPSET_DATASOURCEINFO correspond aux propriétés relatives au fournisseur et à sa source de données. Le jeu de DBPROPSET_DBINIT correspond aux propriétés utilisées lors de l’initialisation. Les modèles du fournisseur OLE DB gèrent ces jeux avec les macros PROPERTY_SET. Les macros créent un bloc qui contient un tableau de propriétés. Chaque fois que le client appelle l' `IDBProperties` interface, le fournisseur utilise le mappage de propriété.

Vous n’avez pas besoin d’implémenter toutes les propriétés dans la spécification. Toutefois, vous devez prendre en charge les propriétés requises ; Pour plus d’informations, consultez la spécification de conformité de niveau 0. Si vous ne souhaitez pas prendre en charge une propriété, vous pouvez la supprimer de la carte. Si vous souhaitez prendre en charge une propriété, ajoutez-la dans la classe Map à l’aide d’une macro PROPERTY_INFO_ENTRY. La macro correspond à la `UPROPINFO` structure comme indiqué dans le code suivant :

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

Chaque élément de la structure représente des informations pour gérer la propriété. Elle contient un `DBPROPID` pour déterminer le GUID et l’ID de la propriété. Elle contient également des entrées pour déterminer le type et la valeur de la propriété.

Si vous souhaitez modifier la valeur par défaut d’une propriété (Notez qu’un consommateur peut modifier la valeur d’une propriété accessible en écriture à tout moment), vous pouvez utiliser la macro PROPERTY_INFO_ENTRY_VALUE ou PROPERTY_INFO_ENTRY_EX. Ces macros vous permettent de spécifier une valeur pour une propriété correspondante. La macro PROPERTY_INFO_ENTRY_VALUE est une notation abrégée qui vous permet de modifier la valeur. La macro PROPERTY_INFO_ENTRY_VALUE appelle la macro PROPERTY_INFO_ENTRY_EX. Cette macro vous permet d’ajouter ou de modifier tous les attributs de la `UPROPINFO` structure.

Si vous souhaitez définir votre propre jeu de propriétés, vous pouvez en ajouter un en effectuant une combinaison BEGIN_PROPSET_MAP/END_PROPSET_MAP supplémentaire. Définissez un GUID pour le jeu de propriétés, puis définissez vos propres propriétés. Si vous avez des propriétés spécifiques au fournisseur, ajoutez-les à un nouveau jeu de propriétés au lieu d’en utiliser un existant. Cela évite les problèmes dans les versions ultérieures de OLE DB.

## <a name="user-defined-property-sets"></a>Jeux de propriétés User-Defined

Visual C++ prend en charge les jeux de propriétés définis par l’utilisateur. Vous n’êtes pas obligé de remplacer `GetProperties` ou `GetPropertyInfo` . Au lieu de cela, les modèles détectent tout jeu de propriétés défini par l’utilisateur et l’ajoutent à l’objet approprié.

Si vous avez un jeu de propriétés défini par l’utilisateur qui doit être disponible au moment de l’initialisation (autrement dit, avant que le consommateur n’appelle `IDBInitialize::Initialize` ), vous pouvez le spécifier à l’aide de l’indicateur UPROPSET_USERINIT, ainsi que de la macro BEGIN_PROPERTY_SET_EX. Le jeu de propriétés doit être dans l’objet de source de données pour que ce fonctionne (comme le requiert la spécification OLE DB). Par exemple :

```cpp
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)
```

## <a name="see-also"></a>Voir aussi

[Fichiers de Wizard-Generated du fournisseur](../../data/oledb/provider-wizard-generated-files.md)<br/>
