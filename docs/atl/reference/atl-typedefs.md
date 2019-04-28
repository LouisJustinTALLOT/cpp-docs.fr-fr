---
title: Typedefs ATL
ms.date: 11/04/2016
f1_keywords:
- atlcore/ATL::_ATL_BASE_MODULE
- atlbase/ATL::_ATL_COM_MODULE
- atlbase/ATL::_ATL_MODULE
- atlbase/ATL::_ATL_WIN_MODULE
- atlutil/ATL::ATL_URL_PORT
- atlbase/ATL::CComDispatchDriver
- atlbase/ATL::CComGlobalsThreadModel
- atlbase/ATL::CComObjectThreadModel
- atlwin/ATL::CContainedWindow
- atlpath/ATL::CPath
- atlpath/ATL::CPathA
- atlpath/ATL::CPathW
- " atlsimpcoll/ATL::CSimpleValArray"
- " atlutil/ATL::LPCURL"
- atlbase/ATL::DefaultThreadTraits
- atlutil/ATL::LPURL
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
ms.openlocfilehash: f3db32e85ea9cba1e946db6259c00c621650e969
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260855"
---
# <a name="atl-typedefs"></a>Typedefs ATL

Active Template Library inclut les typedefs suivants.

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|Défini comme un typedef selon [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|
|[_ATL_COM_MODULE](#_atl_com_module)|Défini comme un typedef selon [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|
|[_ATL_MODULE](#_atl_module)|Défini comme un typedef selon [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|
|[_ATL_WIN_MODULE](#_atl_win_module)|Défini comme un typedef selon [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|Le type utilisé par [CUrl](../../atl/reference/curl-class.md) pour spécifier un numéro de port.|
|[CComDispatchDriver](#ccomdispatchdriver)|Cette classe gère les pointeurs d’interface COM.|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|Appelle des méthodes de modèle, quel que soit le modèle de thread utilisé le thread approprié.|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|Appelle des méthodes de modèle, quel que soit le modèle de thread utilisé le thread approprié.|
|[CContainedWindow](#ccontainedwindow)|Cette classe est une spécialisation de `CContainedWindowT`.|
|[CPath](#cpath)|Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide de `CString`.|
|[CPathA](#cpatha)|Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide de `CStringA`.|
|[CPathW](#cpathw)|Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide de `CStringW`.|
|[CSimpleValArray](#csimplevalarray)|Représente un tableau pour le stockage des types simples.|
|[DefaultThreadTraits](#defaultthreadtraits)|La classe de traits de thread par défaut.|
|[LPCURL](#lpcurl)|Un pointeur vers une constante [CUrl](../../atl/reference/curl-class.md) objet.|
|[LPURL](#lpurl)|Un pointeur vers un [CUrl](../../atl/reference/curl-class.md) objet.|

##  <a name="_atl_base_module"></a>  _ATL_BASE_MODULE

Défini comme typedef selon _ATL_BASE_MODULE70.

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Notes

Utilisé dans chaque projet ATL. Selon [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).

Les classes qui font partie des Classes ATL 7.0 Module dérivent de la structure _ATL_BASE_MODULE.  Pour plus d’informations sur les Classes du Module ATL, consultez [Classes de Modules COM](../../atl/com-modules-classes.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcore.h

##  <a name="_atl_com_module"></a>  _ATL_COM_MODULE

Défini comme typedef selon _ATL_COM_MODULE70.

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Notes

Utilisé par les projets ATL qui utilisent les fonctionnalités COM. Selon [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="_atl_module"></a>  _ATL_MODULE

Défini comme typedef selon _ATL_MODULE70.

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>Configuration requise

**En-tête :**

### <a name="remarks"></a>Notes

Selon [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).

##  <a name="_atl_win_module"></a>  _ATL_WIN_MODULE

Défini comme typedef selon _ATL_WIN_MODULE70.

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Notes

Utilisé par tous les projets ATL qui utilisent les fonctionnalités de fenêtrage. Selon [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="atl_url_port"></a>  ATL_URL_PORT

Le type utilisé par [CUrl](curl-class.md) pour spécifier un numéro de port.

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atlutil.h

##  <a name="ccomdispatchdriver"></a>  CComDispatchDriver

Cette classe gère les pointeurs d’interface COM.

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="ccomglobalsthreadmodel"></a>  CComGlobalsThreadModel

Appelle des méthodes de modèle, quel que soit le modèle de thread utilisé le thread approprié.

```
#if defined(_ATL_SINGLE_THREADED)
typedef CComSingleThreadModel CComGlobalsThreadModel;
#elif defined(_ATL_APARTMENT_THREADED)
typedef CComMultiThreadModel CComGlobalsThreadModel;
#elif defined(_ATL_FREE_THREADED)
typedef CComMultiThreadModel CComGlobalsThreadModel;
#else
#pragma message ("No global threading model defined")
#endif
```

### <a name="remarks"></a>Notes

Selon le modèle de thread utilisé par votre application, le **typedef** nom `CComGlobalsThreadModel` fait référence à [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) ou [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Ces classes fournissent supplémentaires `typedef` noms pour référencer une classe de la section critique.

> [!NOTE]
> `CComGlobalsThreadModel` ne référence pas de classe [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

À l’aide de `CComGlobalsThreadModel` vous libère de la spécification d’une classe de modèle de thread particulier. Quel que soit le modèle de thread utilisé, les méthodes appropriées seront appelées.

En plus de `CComGlobalsThreadModel`, ATL fournit le **typedef** nom [CComObjectThreadModel](#ccomobjectthreadmodel). La classe référencée par chaque `typedef` varie selon le modèle de thread utilisé, comme indiqué dans le tableau suivant :

|typedef|Thread unique|Thread cloisonné|Modèle de thread libre|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`; M= `CComMultiThreadModel`

Utilisez `CComObjectThreadModel` au sein d’une classe d’objet unique. Utilisez `CComGlobalsThreadModel` dans un objet qui est globalement disponible pour votre programme, ou lorsque vous souhaitez protéger des ressources du module entre plusieurs threads.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="ccomobjectthreadmodel"></a>  CComObjectThreadModel

Appelle des méthodes de modèle, quel que soit le modèle de thread utilisé le thread approprié.

```
#if defined(_ATL_SINGLE_THREADED)
typedef CComSingleThreadModel CComObjectThreadModel;
#elif defined(_ATL_APARTMENT_THREADED)
typedef CComSingleThreadModel CComObjectThreadModel;
#elif defined(_ATL_FREE_THREADED)
typedef CComMultiThreadModel CComObjectThreadModel;
#else
#pragma message ("No global threading model defined")
#endif
```

### <a name="remarks"></a>Notes

Selon le modèle de thread utilisé par votre application, le `typedef` nom `CComObjectThreadModel` fait référence à [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) ou [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Ces classes fournissent supplémentaires `typedef` noms pour référencer une classe de la section critique.

> [!NOTE]
> `CComObjectThreadModel` ne référence pas de classe [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

À l’aide de `CComObjectThreadModel` vous libère de la spécification d’une classe de modèle de thread particulier. Quel que soit le modèle de thread utilisé, les méthodes appropriées seront appelées.

En plus de `CComObjectThreadModel`, ATL fournit le **typedef** nom [CComGlobalsThreadModel](#ccomglobalsthreadmodel). La classe référencée par chaque **typedef** varie selon le modèle de thread utilisé, comme indiqué dans le tableau suivant :

|typedef|Thread unique|Thread cloisonné|Modèle de thread libre|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`; M= `CComMultiThreadModel`

Utilisez `CComObjectThreadModel` au sein d’une classe d’objet unique. Utilisez `CComGlobalsThreadModel` dans un objet qui est globalement disponible pour votre programme, ou lorsque vous souhaitez protéger des ressources du module entre plusieurs threads.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="ccontainedwindow"></a>  CContainedWindow

Cette classe est une spécialisation de `CContainedWindowT`.

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atlwin.h

### <a name="remarks"></a>Notes

`CContainedWindow` est une spécialisation de [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Si vous souhaitez modifier la classe de base ou les caractéristiques, utilisez `CContainedWindowT` directement.

##  <a name="cpath"></a>  CPath

Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide de `CString`.

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atlpath.h

##  <a name="cpatha"></a>  CPathA

Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide de `CStringA`.

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atlpath.h

##  <a name="cpathw"></a>  CPathW

Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide de `CStringW`.

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atlpath.h

##  <a name="csimplevalarray"></a>  CSimpleValArray

Représente un tableau pour le stockage des types simples.

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Notes

`CSimpleValArray` est fourni pour créer et gérer des tableaux contenant des types de données simples. Il est un simple #define de [CSimpleArray](../../atl/reference/csimplearray-class.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsimpcoll.h

##  <a name="lpcurl"></a>  LPCURL

Un pointeur vers une constante [CUrl](../../atl/reference/curl-class.md) objet.

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atlutil.h

##  <a name="defaultthreadtraits"></a>  DefaultThreadTraits

La classe de traits de thread par défaut.

### <a name="syntax"></a>Syntaxe

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Notes

Si le projet actif utilise la bibliothèque CRT multithread, DefaultThreadTraits est défini comme CRTThreadTraits. Sinon, Win32ThreadTraits est utilisée.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="lpurl"></a>  LPURL

Un pointeur vers un [CUrl](../../atl/reference/curl-class.md) objet.

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>Configuration requise

**En-tête :** atlutil.h

## <a name="see-also"></a>Voir aussi

[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)<br/>
[Fonctions](../../atl/reference/atl-functions.md)<br/>
[Variables globales](../../atl/reference/atl-global-variables.md)<br/>
[Les classes et structs](../../atl/reference/atl-classes.md)<br/>
[Macros](../../atl/reference/atl-macros.md)
