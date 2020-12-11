---
description: 'En savoir plus sur : ATL typedefs'
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
ms.openlocfilehash: cb243ef3d16689a1a0ddeb81d3de0bb4ec234a9c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158645"
---
# <a name="atl-typedefs"></a>Typedefs ATL

Le Active Template Library comprend les typedefs suivants.

|Typedef|Description|
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|Défini comme un typedef basé sur [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|
|[_ATL_COM_MODULE](#_atl_com_module)|Défini comme un typedef basé sur [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|
|[_ATL_MODULE](#_atl_module)|Défini comme un typedef basé sur [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|
|[_ATL_WIN_MODULE](#_atl_win_module)|Défini comme un typedef basé sur [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|Type utilisé par la [boucle](../../atl/reference/curl-class.md) pour spécifier un numéro de port.|
|[CComDispatchDriver](#ccomdispatchdriver)|Cette classe gère les pointeurs d’interface COM.|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|Appelle les méthodes de modèle de thread appropriées, quel que soit le modèle de thread utilisé.|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|Appelle les méthodes de modèle de thread appropriées, quel que soit le modèle de thread utilisé.|
|[CContainedWindow](#ccontainedwindow)|Cette classe est une spécialisation de `CContainedWindowT` .|
|[CPath](#cpath)|Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide de `CString` .|
|[CPathA](#cpatha)|Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide de `CStringA` .|
|[CPathW](#cpathw)|Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide de `CStringW` .|
|[CSimpleValArray](#csimplevalarray)|Représente un tableau pour le stockage des types simples.|
|[DefaultThreadTraits](#defaultthreadtraits)|Classe de caractéristiques de thread par défaut.|
|[LPCURL](#lpcurl)|Pointeur vers un objet de [boucle](../../atl/reference/curl-class.md) constante.|
|[LPURL](#lpurl)|Pointeur vers un objet de la [boucle](../../atl/reference/curl-class.md) .|

## <a name="_atl_base_module"></a><a name="_atl_base_module"></a> _ATL_BASE_MODULE

Défini comme un typedef basé sur _ATL_BASE_MODULE70.

```cpp
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Notes

Utilisé dans chaque projet ATL. Basé sur [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).

Les classes qui font partie des classes de module ATL 7,0 dérivent de la structure _ATL_BASE_MODULE.  Pour plus d’informations sur les classes de module ATL, consultez [classes de modules com](../../atl/com-modules-classes.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlcore. h

## <a name="_atl_com_module"></a><a name="_atl_com_module"></a> _ATL_COM_MODULE

Défini comme un typedef basé sur _ATL_COM_MODULE70.

```cpp
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Notes

Utilisé par les projets ATL qui utilisent les fonctionnalités COM. Basé sur [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="_atl_module"></a><a name="_atl_module"></a> _ATL_MODULE

Défini comme un typedef basé sur _ATL_MODULE70.

```cpp
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

### <a name="requirements"></a>Spécifications

**Titre**

### <a name="remarks"></a>Notes

Basé sur [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).

## <a name="_atl_win_module"></a><a name="_atl_win_module"></a> _ATL_WIN_MODULE

Défini comme un typedef basé sur _ATL_WIN_MODULE70.

```cpp
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Notes

Utilisé par tous les projets ATL qui utilisent des fonctionnalités de fenêtrage. Basé sur [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="atl_url_port"></a><a name="atl_url_port"></a> ATL_URL_PORT

Type utilisé par la [boucle](curl-class.md) pour spécifier un numéro de port.

```cpp
typedef WORD ATL_URL_PORT;
```

### <a name="requirements"></a>Spécifications

**En-tête :** atlutil. h

## <a name="ccomdispatchdriver"></a><a name="ccomdispatchdriver"></a> CComDispatchDriver

Cette classe gère les pointeurs d’interface COM.

```cpp
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

### <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="ccomglobalsthreadmodel"></a><a name="ccomglobalsthreadmodel"></a> CComGlobalsThreadModel

Appelle les méthodes de modèle de thread appropriées, quel que soit le modèle de thread utilisé.

```cpp
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

Selon le modèle de thread utilisé par votre application, le **`typedef`** nom `CComGlobalsThreadModel` fait référence à [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) ou [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Ces classes fournissent des **`typedef`** noms supplémentaires pour référencer une classe de section critique.

> [!NOTE]
> `CComGlobalsThreadModel` ne fait pas référence à la classe [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

L’utilisation `CComGlobalsThreadModel` de vous libère de la spécification d’une classe de modèle de thread particulière. Quel que soit le modèle de thread utilisé, les méthodes appropriées sont appelées.

En plus de `CComGlobalsThreadModel` , ATL fournit le **`typedef`** nom [CComObjectThreadModel](#ccomobjectthreadmodel). La classe référencée par chacune **`typedef`** dépend du modèle de thread utilisé, comme indiqué dans le tableau suivant :

|typedef|Thread unique|Thread cloisonné|Thread libre|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel` ; M = `CComMultiThreadModel`

Utilisez `CComObjectThreadModel` dans une classe d’objet unique. Utilisez `CComGlobalsThreadModel` dans un objet qui est globalement disponible pour votre programme, ou lorsque vous souhaitez protéger des ressources de module sur plusieurs threads.

### <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="ccomobjectthreadmodel"></a><a name="ccomobjectthreadmodel"></a> CComObjectThreadModel

Appelle les méthodes de modèle de thread appropriées, quel que soit le modèle de thread utilisé.

```cpp
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

Selon le modèle de thread utilisé par votre application, le **`typedef`** nom `CComObjectThreadModel` fait référence à [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) ou [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Ces classes fournissent des **`typedef`** noms supplémentaires pour référencer une classe de section critique.

> [!NOTE]
> `CComObjectThreadModel` ne fait pas référence à la classe [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

L’utilisation `CComObjectThreadModel` de vous libère de la spécification d’une classe de modèle de thread particulière. Quel que soit le modèle de thread utilisé, les méthodes appropriées sont appelées.

En plus de `CComObjectThreadModel` , ATL fournit le **`typedef`** nom [CComGlobalsThreadModel](#ccomglobalsthreadmodel). La classe référencée par chacune **`typedef`** dépend du modèle de thread utilisé, comme indiqué dans le tableau suivant :

|typedef|Thread unique|Thread cloisonné|Thread libre|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel` ; M = `CComMultiThreadModel`

Utilisez `CComObjectThreadModel` dans une classe d’objet unique. Utilisez `CComGlobalsThreadModel` dans un objet qui est accessible globalement à votre programme, ou lorsque vous souhaitez protéger des ressources de module sur plusieurs threads.

### <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="ccontainedwindow"></a><a name="ccontainedwindow"></a> CContainedWindow

Cette classe est une spécialisation de `CContainedWindowT` .

```cpp
typedef CContainedWindowT<CWindow> CContainedWindow;
```

### <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

### <a name="remarks"></a>Notes

`CContainedWindow` est une spécialisation de [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Si vous souhaitez modifier la classe de base ou les traits, utilisez `CContainedWindowT` directement.

## <a name="cpath"></a><a name="cpath"></a> CPath

Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide de `CString` .

```cpp
typedef CPathT<CString> CPath;
```

### <a name="requirements"></a>Spécifications

**En-tête :** atlpath. h

## <a name="cpatha"></a><a name="cpatha"></a> CPathA

Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide de `CStringA` .

```cpp
typedef CPathT<CStringA> CPathA;
```

### <a name="requirements"></a>Spécifications

**En-tête :** atlpath. h

## <a name="cpathw"></a><a name="cpathw"></a> CPathW

Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide de `CStringW` .

```cpp
typedef ATL::CPathT<CStringW> CPathW;
```

### <a name="requirements"></a>Spécifications

**En-tête :** atlpath. h

## <a name="csimplevalarray"></a><a name="csimplevalarray"></a> CSimpleValArray

Représente un tableau pour le stockage des types simples.

```cpp
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Notes

`CSimpleValArray` est fourni pour créer et gérer des tableaux contenant des types de données simples. C’est un #define simple de [CSimpleArray](../../atl/reference/csimplearray-class.md).

### <a name="requirements"></a>Spécifications

**En-tête :** atlsimpcoll. h

## <a name="lpcurl"></a><a name="lpcurl"></a> LPCURL

Pointeur vers un objet de [boucle](../../atl/reference/curl-class.md) constante.

```cpp
typedef const CUrl* LPCURL;
```

### <a name="requirements"></a>Spécifications

**En-tête :** atlutil. h

## <a name="defaultthreadtraits"></a><a name="defaultthreadtraits"></a> DefaultThreadTraits

Classe de caractéristiques de thread par défaut.

### <a name="syntax"></a>Syntaxe

```cpp
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Notes

Si le projet en cours utilise le CRT multithread, DefaultThreadTraits est défini en tant que CRTThreadTraits. Dans le cas contraire, Win32ThreadTraits est utilisé.

### <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="lpurl"></a><a name="lpurl"></a> LPURL

Pointeur vers un objet de la [boucle](../../atl/reference/curl-class.md) .

```cpp
typedef CUrl* LPURL;
```

### <a name="requirements"></a>Spécifications

**En-tête :** atlutil. h

## <a name="see-also"></a>Voir aussi

[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)<br/>
[Fonctions](../../atl/reference/atl-functions.md)<br/>
[Variables globales](../../atl/reference/atl-global-variables.md)<br/>
[Classes et structs](../../atl/reference/atl-classes.md)<br/>
[Macros](../../atl/reference/atl-macros.md)
