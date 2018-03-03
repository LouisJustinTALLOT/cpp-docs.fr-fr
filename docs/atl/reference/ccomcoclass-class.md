---
title: Classe de CComCoClass | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
dev_langs:
- C++
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 969370294ed3d5d2ca2fdff5f4a106b72ed77a17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcoclass-class"></a>CComCoClass (classe)
Cette classe fournit des méthodes pour créer des instances d’une classe et l’obtention de ses propriétés.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, const CLSID* pclsid = &CLSID_NULL>  
class CComCoClass
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `CComCoClass`.  
  
 *pclsid*  
 Pointeur vers le CLSID de l’objet.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComCoClass::CreateInstance](#createinstance)|(Statique) Crée une instance de la classe et les requêtes pour une interface.|  
|[CComCoClass::Error](#error)|(Statique) Retourne des informations d’erreur complètes au client.|  
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|(Statique) Retourne l’identificateur de classe de l’objet.|  
|[CComCoClass::GetObjectDescription](#getobjectdescription)|(Statique) Substituez pour retourner la description de l’objet.|  
  
## <a name="remarks"></a>Notes  
 `CComCoClass`Fournit des méthodes pour la récupération CLSID d’un objet, la définition des informations d’erreur et la création d’instances de la classe. N’importe quelle classe inscrite dans le [de mappage des objets](http://msdn.microsoft.com/en-us/b57619cc-534f-4b8f-bfd4-0c12f937202f) doit être dérivé `CComCoClass`.  
  
 `CComCoClass`définit également la classe modèle par défaut en usine et d’agrégation pour votre objet. `CComCoClass`utilise les deux macros suivantes :  
  
- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) déclare la fabrique de classe [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).  
  
- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) déclare que votre objet peut être agrégée.  
  
 Vous pouvez remplacer ces valeurs par défaut en spécifiant une autre macro dans votre définition de classe. Par exemple, pour utiliser [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) au lieu de `CComClassFactory`, spécifiez la [macro DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) macro :  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlcom.h  
  
##  <a name="createinstance"></a>CComCoClass::CreateInstance  
 Utilisez ces `CreateInstance` fonctions pour créer une instance de COM de l’objet et récupérer un pointeur d’interface sans l’aide de l’API COM.  
  
```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```  
  
### <a name="parameters"></a>Paramètres  
 `Q`  
 L’interface COM qui doit être retournée via `pp`.  
  
 *punkOuter*  
 [in] Inconnu externe ou inconnu de contrôle de l’agrégat.  
  
 `pp`  
 [out] L’adresse d’une variable pointeur qui reçoit le pointeur d’interface demandé si la création réussit.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard. Consultez [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615) dans le SDK Windows pour obtenir une description des valeurs de retournés possibles.  
  
### <a name="remarks"></a>Notes  
 Utilisez la première surcharge de cette fonction pour la création de l’objet « Typical » ; Utilisez la deuxième surcharge lorsque vous avez besoin agréger l’objet en cours de création.  
  
 La classe ATL qui implémente l’objet COM requis (autrement dit, la classe utilisée comme premier paramètre de modèle à [CComCoClass](../../atl/reference/ccomcoclass-class.md)) doit être dans le même projet que le code appelant. La création de l’objet COM est effectuée par la fabrique de classe enregistrée pour cette classe ATL.  
  
 Ces fonctions sont utiles pour la création d’objets que vous n’a pas pu être créé en externe à l’aide de la [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto) (macro). Ils sont également utiles dans les situations où vous souhaitez éviter l’API COM pour des raisons d’efficacité.  
  
 Notez que l’interface `Q` doit avoir un IID associé qui peut être récupéré à l’aide de la [__uuidof](../../cpp/uuidof-operator.md) opérateur.  
  
### <a name="example"></a>Exemple  
 Dans l’exemple suivant, `CDocument` est une classe ATL générées par l’Assistant dérivée `CComCoClass` qui implémente le **IDocument** interface. La classe est inscrite dans la table des objets avec le `OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO` afin que les clients ne peut pas créer des instances de document à l’aide de macro [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615). `CApplication`est une coclasse qui fournit une méthode sur l’un de ses propres interfaces COM pour créer des instances de la classe de document. Le code ci-dessous montre comment facilement lui permet de créer des instances de la classe de document à l’aide de la `CreateInstance` membre hérité à partir de la `CComCoClass` classe de base.  
  
 [!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]  
  
##  <a name="error"></a>CComCoClass::Error  
 Cette fonction statique configure le `IErrorInfo` interface afin de fournir des informations d’erreur au client.  
  
```
static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance ());

static HRESULT Error(
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszDesc`  
 [in] Chaîne décrivant l’erreur. La version Unicode de `Error` Spécifie que `lpszDesc` est de type **LPCOLESTR**; la version ANSI spécifie un type de `LPCSTR`.  
  
 `iid`  
 [in] IID de l’interface qui définit l’erreur ou `GUID_NULL` (la valeur par défaut) si l’erreur est définie par le système d’exploitation.  
  
 `hRes`  
 [in] Le `HRESULT` à renvoyer à l’appelant. La valeur par défaut est 0. Pour plus d’informations sur `hRes`, consultez la section Notes.  
  
 `nID`  
 [in] L’identificateur de ressource où se trouve la chaîne de description d’erreur. Cette valeur doit être comprise entre 0 x 0200 et 0xFFFF, inclus. Dans les versions debug, un **ASSERT** se produira si `nID` n’indexe pas une chaîne valide. Dans les versions release, la chaîne de description d’erreur sera définie sur « Erreur inconnue ».  
  
 `dwHelpID`  
 [in] L’identificateur de contexte d’aide pour l’erreur.  
  
 `lpszHelpFile`  
 [in] Le chemin d’accès et le nom du fichier d’aide décrivant l’erreur.  
  
 `hInst`  
 [in] Le handle de la ressource. Par défaut, ce paramètre est **_AtlModule::GetResourceInstance**, où **_AtlModule** est l’instance globale de [CAtlModule](../../atl/reference/catlmodule-class.md).  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard. Pour plus d'informations, consultez Notes.  
  
### <a name="remarks"></a>Notes  
 Pour appeler `Error`, votre objet doit implémenter le `ISupportErrorInfo Interface` interface.  
  
 Si le `hRes` paramètre est différent de zéro, puis `Error` retourne la valeur de `hRes`. Si `hRes` est zéro, les quatre premières versions de `Error` retourner `DISP_E_EXCEPTION`. Les deux dernières versions retournent le résultat de la macro **MAKE_HRESULT (1, FACILITY_ITF,** `nID` **)**.  
  
##  <a name="getobjectclsid"></a>CComCoClass::GetObjectCLSID  
 Fournit un moyen cohérent de la récupération de CLSID de l’objet.  
  
```
static const CLSID& WINAPI GetObjectCLSID();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Identificateur de classe de l’objet.  
  
##  <a name="getobjectdescription"></a>CComCoClass::GetObjectDescription  
 Cette fonction statique récupère la description textuelle de l’objet de classe.  
  
```
static LPCTSTR WINAPI GetObjectDescription();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Description de l’objet de la classe.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut retourne **NULL**. Vous pouvez substituer cette méthode avec le [DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description) (macro). Exemple :  
  
 [!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]  
  
 `GetObjectDescription`est appelée par **IComponentRegistrar::GetComponents**. **IComponentRegistrar** est une interface d’automatisation qui vous permet d’enregistrer et annuler l’inscription des composants individuels dans une DLL. Lorsque vous créez un objet de l’inscription de composants avec l’Assistant Projet ATL, l’Assistant appliquent automatiquement la **IComponentRegistrar** interface. **IComponentRegistrar** est généralement utilisée par Microsoft Transaction Server.  
  
 Pour plus d’informations sur l’Assistant Projet ATL, consultez l’article [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
