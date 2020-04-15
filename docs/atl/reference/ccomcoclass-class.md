---
title: Classe CComCoClass
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
ms.openlocfilehash: 11e724a982f3a2f404473dbdd34d848842cc8e14
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320817"
---
# <a name="ccomcoclass-class"></a>Classe CComCoClass

Cette classe fournit des méthodes pour créer des instances d’une classe, et l’obtention de ses propriétés.

## <a name="syntax"></a>Syntaxe

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `CComCoClass`dérivée de .

*pclsid (pclsid)*<br/>
Un pointeur pour le CLSID de l’objet.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComCoClass::CréerInstance](#createinstance)|(Statique) Crée un exemple de la classe et des requêtes pour une interface.|
|[CComCoClass::Erreur](#error)|(Statique) Renvoie de riches informations d’erreur au client.|
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|(Statique) Retourne l’identifiant de classe de l’objet.|
|[CComCoClass:GetObjectDescription](#getobjectdescription)|(Statique) Remplacer pour retourner la description de l’objet.|

## <a name="remarks"></a>Notes

`CComCoClass`fournit des méthodes pour récupérer le CLSID d’un objet, régler des informations d’erreur et créer des instances de la classe. Toute classe enregistrée sur la carte `CComCoClass`de l’objet doit être dérivée .

`CComCoClass`définit également l’usine de classe par défaut et le modèle d’agrégation pour votre objet. `CComCoClass`utilise les deux macros suivantes :

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) Déclare l’usine de classe pour être [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) Déclare que votre objet peut être agrégé.

Vous pouvez remplacer l’un ou l’autre de ces défauts en spécifiant une autre macro dans votre définition de classe. Par exemple, pour utiliser [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) au lieu de `CComClassFactory`, spécifier le [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) macro:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomcoclasscreateinstance"></a><a name="createinstance"></a>CComCoClass::CréerInstance

Utilisez `CreateInstance` ces fonctions pour créer une instance d’un objet COM et récupérer un pointeur d’interface sans utiliser l’API COM.

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>Paramètres

*Q*<br/>
L’interface COM qui doit être retournée via *pp*.

*punkOuter (punkOuter)*<br/>
[dans] L’inconnu extérieur ou le contrôle inconnu de l’agrégat.

*Pp*<br/>
[out] L’adresse d’une variable de pointeur qui reçoit le pointeur d’interface demandé si la création réussit.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard. Voir [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) dans le SDK Windows pour une description des valeurs de retour possibles.

### <a name="remarks"></a>Notes

Utilisez la première surcharge de cette fonction pour la création d’objets typiques; utiliser la deuxième surcharge lorsque vous avez besoin d’agréger l’objet en cours de création.

La classe ATL implémentant l’objet COM requis (c’est-à-dire la classe utilisée comme premier paramètre de modèle pour [CComCoClass](../../atl/reference/ccomcoclass-class.md)) doit être dans le même projet que le code d’appel. La création de l’objet COM est réalisée par l’usine de classe enregistrée pour cette classe ATL.

Ces fonctions sont utiles pour créer des objets que vous avez empêchés d’être créatables à l’extérieur en utilisant la [macro OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO.](object-map-macros.md#object_entry_non_createable_ex_auto) Ils sont également utiles dans les situations où vous voulez éviter l’API COM pour des raisons d’efficacité.

Notez que l’interface *Q* doit avoir un IID associé à elle qui peut être récupéré à l’aide [de l’opérateur __uuidof.](../../cpp/uuidof-operator.md)

### <a name="example"></a>Exemple

Dans l’exemple `CDocument` suivant, est une classe `CComCoClass` ATL générée `IDocument` par les sorciers dérivé de qui implémente l’interface. La classe est enregistrée dans la carte des objets avec la OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO macro afin que les clients ne peuvent pas créer des instances du document à l’aide de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance). `CApplication`est une CoClass qui fournit une méthode sur l’une de ses propres interfaces COM pour créer des instances de la classe de documents. Le code ci-dessous montre à quel point `CreateInstance` il est `CComCoClass` facile de créer des instances de la classe de documents en utilisant le membre hérité de la classe de base.

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

## <a name="ccomcoclasserror"></a><a name="error"></a>CComCoClass::Erreur

Cette fonction statique `IErrorInfo` définit l’interface pour fournir des informations d’erreur au client.

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

*lpszDesc (en)*<br/>
[dans] La chaîne décrivant l’erreur. La version Unicode de `Error` spécifie que *lpszDesc* est de type LPCOLESTR; la version ANSI spécifie un type de LPCSTR.

*Iid*<br/>
[dans] L’IID de l’interface définissant l’erreur ou GUID_NULL (la valeur par défaut) si l’erreur est définie par le système d’exploitation.

*hRes*<br/>
[dans] Le HRESULT que vous souhaitez retourner à l’appelant. La valeur par défaut est 0. Pour plus de détails sur *hRes*, voir Remarques.

*nID*<br/>
[dans] L’identifiant de ressource où la chaîne de description d’erreur est stockée. Cette valeur devrait se situer entre 0x0200 et 0xFFFF, inclusivement. Dans les constructions de débogé, un **ASSERT** se traduira si *nID* n’indexe pas une chaîne valide. Dans les versions, la chaîne de description d’erreur sera définie à "Erreur inconnue."

*dwHelpID*<br/>
[dans] L’identifiant de contexte d’aide pour l’erreur.

*lpszHelpFile*<br/>
[dans] Le chemin et le nom du fichier d’aide décrivant l’erreur.

*hInst*<br/>
[dans] Le manche de la ressource. Par défaut, ce `_AtlModule::GetResourceInstance`paramètre est , où `_AtlModule` est l’exemple global de [CAtlModule](../../atl/reference/catlmodule-class.md).

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard. Pour plus d'informations, consultez Notes.

### <a name="remarks"></a>Notes

Pour `Error`appeler, votre objet `ISupportErrorInfo Interface` doit implémenter l’interface.

Si le *paramètre hRes* est `Error` nonzero, puis retourne la valeur de *hRes*. Si *hRes* est zéro, alors les `Error` quatre premières versions de retour DISP_E_EXCEPTION. Les deux dernières versions renvoient le résultat de la macro **MAKE_HRESULT( 1, FACILITY_ITF,** *nID* **)**.

## <a name="ccomcoclassgetobjectclsid"></a><a name="getobjectclsid"></a>CComCoClass::GetObjectCLSID

Fournit un moyen cohérent de récupérer le CLSID de l’objet.

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>Valeur de retour

L’identifiant de classe de l’objet.

## <a name="ccomcoclassgetobjectdescription"></a><a name="getobjectdescription"></a>CComCoClass:GetObjectDescription

Cette fonction statique récupère la description de texte pour votre objet de classe.

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>Valeur de retour

La description de l’objet de classe.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut renvoie NULL. Vous pouvez remplacer cette méthode avec la [macro DECLARE_OBJECT_DESCRIPTION.](object-map-macros.md#declare_object_description) Par exemple :

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription`est appelé `IComponentRegistrar::GetComponents`par . `IComponentRegistrar`est une interface Automation qui vous permet d’enregistrer et de dépoister des composants individuels dans un DLL. Lorsque vous créez un objet registraire de composant avec l’assistant de projet ATL, l’assistant implémente automatiquement l’interface. `IComponentRegistrar` `IComponentRegistrar`est généralement utilisé par Microsoft Transaction Server.

Pour plus d’informations sur le assistant de projet ATL, voir l’article [Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
