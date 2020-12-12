---
description: 'En savoir plus sur : CComCoClass, classe'
title: CComCoClass, classe
ms.date: 11/04/2016
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
ms.openlocfilehash: 31895afa9100159e8ac1a9ef370f6548e2b2e3f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152254"
---
# <a name="ccomcoclass-class"></a>CComCoClass, classe

Cette classe fournit des méthodes pour la création d’instances d’une classe et l’obtention de ses propriétés.

## <a name="syntax"></a>Syntaxe

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `CComCoClass` .

*pclsid*<br/>
Pointeur vers le CLSID de l’objet.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComCoClass :: CreateInstance](#createinstance)|Statique Crée une instance de la classe et des requêtes pour une interface.|
|[CComCoClass :: Error](#error)|Statique Retourne des informations complètes sur l’erreur au client.|
|[CComCoClass :: GetObjectCLSID](#getobjectclsid)|Statique Retourne l’identificateur de classe de l’objet.|
|[CComCoClass :: GetObjectDescription](#getobjectdescription)|Statique Substituez pour retourner la description de l’objet.|

## <a name="remarks"></a>Notes

`CComCoClass` fournit des méthodes pour récupérer le CLSID d’un objet, définir des informations d’erreur et créer des instances de la classe. Toute classe inscrite dans le mappage d’objets doit être dérivée de `CComCoClass` .

`CComCoClass` définit également la fabrique de classe et le modèle d’agrégation par défaut pour votre objet. `CComCoClass` utilise les deux macros suivantes :

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) Déclare que la fabrique de classe est [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) Déclare que votre objet peut être agrégé.

Vous pouvez remplacer l’une de ces valeurs par défaut en spécifiant une autre macro dans votre définition de classe. Par exemple, pour utiliser [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) au lieu de `CComClassFactory` , spécifiez la macro [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) :

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ccomcoclasscreateinstance"></a><a name="createinstance"></a> CComCoClass :: CreateInstance

Utilisez ces `CreateInstance` fonctions pour créer une instance d’un objet com et récupérer un pointeur d’interface sans utiliser l’API com.

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>Paramètres

*Question*<br/>
Interface COM qui doit être retournée via *pp*.

*punkOuter*<br/>
dans Inconnu externe ou contrôle inconnu de l’agrégat.

*p*<br/>
à Adresse d’une variable pointeur qui reçoit le pointeur d’interface demandé en cas de création réussie.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard. Consultez [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) dans le SDK Windows pour obtenir une description des valeurs de retour possibles.

### <a name="remarks"></a>Notes

Utilisez la première surcharge de cette fonction pour la création d’objets classiques ; Utilisez la deuxième surcharge lorsque vous avez besoin d’agréger l’objet en cours de création.

La classe ATL qui implémente l’objet COM requis (autrement dit, la classe utilisée comme premier paramètre de modèle de [CComCoClass](../../atl/reference/ccomcoclass-class.md)) doit se trouver dans le même projet que le code appelant. La création de l’objet COM est effectuée par la fabrique de classe inscrite pour cette classe ATL.

Ces fonctions sont utiles pour créer des objets que vous ne pouvez pas créer de manière externe à l’aide de la macro [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto) . Elles sont également utiles dans les situations où vous souhaitez éviter l’API COM pour des raisons d’efficacité.

Notez que l’interface *Q* doit avoir un IID associé qui peut être récupéré à l’aide de l’opérateur [__uuidof](../../cpp/uuidof-operator.md) .

### <a name="example"></a>Exemple

Dans l’exemple suivant, `CDocument` est une classe ATL générée par l’Assistant dérivée de `CComCoClass` qui implémente l' `IDocument` interface. La classe est inscrite dans la table d’objets avec la macro OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO afin que les clients ne puissent pas créer d’instances du document à l’aide de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance). `CApplication` est une coclasse qui fournit une méthode sur l’une de ses propres interfaces COM pour créer des instances de la classe de document. Le code ci-dessous montre combien il est facile de créer des instances de la classe de document à l’aide du `CreateInstance` membre hérité de la `CComCoClass` classe de base.

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

## <a name="ccomcoclasserror"></a><a name="error"></a> CComCoClass :: Error

Cette fonction statique configure l' `IErrorInfo` interface pour fournir des informations d’erreur au client.

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

*lpszDesc*<br/>
dans Chaîne décrivant l’erreur. La version Unicode de `Error` spécifie que *lpszDesc* est de type LPCOLESTR ; la version ANSI spécifie un type de LPCSTR.

*vaut*<br/>
dans IID de l’interface définissant l’erreur ou la GUID_NULL (valeur par défaut) si l’erreur est définie par le système d’exploitation.

*hRes*<br/>
dans HRESULT que vous souhaitez retourner à l’appelant. La valeur par défaut est 0. Pour plus d’informations sur *hres*, consultez la section Notes.

*nID*<br/>
dans Identificateur de ressource dans lequel la chaîne de description de l’erreur est stockée. Cette valeur doit être comprise entre 0x0200 et 0xFFFF, inclus. Dans les versions Debug, une **assertion** se produit si *nid* n’indexe pas une chaîne valide. Dans les versions release, la chaîne de description d’erreur est définie sur « erreur inconnue ».

*dwHelpID*<br/>
dans Identificateur du contexte d’aide pour l’erreur.

*lpszHelpFile*<br/>
dans Chemin d’accès et nom du fichier d’aide décrivant l’erreur.

*hInst*<br/>
dans Handle de la ressource. Par défaut, ce paramètre est `_AtlModule::GetResourceInstance` , où `_AtlModule` est l’instance globale de [CAtlModule](../../atl/reference/catlmodule-class.md).

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Pour appeler `Error` , votre objet doit implémenter l' `ISupportErrorInfo Interface` interface.

Si le paramètre *hres* est différent de zéro, `Error` retourne la valeur de *hres*. Si *hres* est égal à zéro, les quatre premières versions de `Error` retournent DISP_E_EXCEPTION. Les deux dernières versions renvoient le résultat de la macro **MAKE_HRESULT (1, FACILITY_ITF,** *nid* **)**.

## <a name="ccomcoclassgetobjectclsid"></a><a name="getobjectclsid"></a> CComCoClass :: GetObjectCLSID

Fournit un moyen cohérent de récupérer le CLSID de l’objet.

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>Valeur renvoyée

Identificateur de classe de l’objet.

## <a name="ccomcoclassgetobjectdescription"></a><a name="getobjectdescription"></a> CComCoClass :: GetObjectDescription

Cette fonction statique récupère la description textuelle de votre objet de classe.

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>Valeur renvoyée

Description de l’objet de classe.

### <a name="remarks"></a>Notes

L’implémentation par défaut retourne la valeur NULL. Vous pouvez remplacer cette méthode par la macro [DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description) . Par exemple :

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription` est appelé par `IComponentRegistrar::GetComponents` . `IComponentRegistrar` est une interface Automation qui vous permet d’inscrire et d’annuler l’enregistrement de composants individuels dans une DLL. Lorsque vous créez un objet d’inscription de composants à l’aide de l’Assistant Projet ATL, l’Assistant implémente automatiquement l' `IComponentRegistrar` interface. `IComponentRegistrar` est généralement utilisé par Microsoft Transaction Server.

Pour plus d’informations sur l’Assistant Projet ATL, consultez l’article [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
