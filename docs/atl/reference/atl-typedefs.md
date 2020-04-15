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
ms.openlocfilehash: 5548bee36ac52dbd6add31241714b0404289be45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319198"
---
# <a name="atl-typedefs"></a>Typedefs ATL

La bibliothèque Active Template comprend les types suivants.

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|Défini comme un typedef basé sur [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|
|[_ATL_COM_MODULE](#_atl_com_module)|Défini comme un typedef basé sur [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|
|[_ATL_MODULE](#_atl_module)|Défini comme un typedef basé sur [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|
|[_ATL_WIN_MODULE](#_atl_win_module)|Défini comme un dactylographe basé sur [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|Le type utilisé par [CUrl](../../atl/reference/curl-class.md) pour spécifier un numéro de port.|
|[CComDispatchDriver](#ccomdispatchdriver)|Cette classe gère les pointeurs d’interface COM.|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|Appelle les méthodes appropriées de modèle de fil, indépendamment du modèle de threading utilisé.|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|Appelle les méthodes appropriées de modèle de fil, indépendamment du modèle de threading utilisé.|
|[CContainedWindow](#ccontainedwindow)|Cette classe est une `CContainedWindowT`spécialisation de .|
|[CPath (en)](#cpath)|Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide `CString`de .|
|[CPathA (en)](#cpatha)|Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide `CStringA`de .|
|[CPathW (en)](#cpathw)|Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide `CStringW`de .|
|[CSimpleValArray](#csimplevalarray)|Représente un tableau pour stocker des types simples.|
|[DéfautThreadTraits](#defaultthreadtraits)|La classe des traits de thread par défaut.|
|[LPCURL](#lpcurl)|Un pointeur vers un objet [CUrl](../../atl/reference/curl-class.md) constant.|
|[LPURL (LPURL)](#lpurl)|Un pointeur sur un objet [CUrl.](../../atl/reference/curl-class.md)|

## <a name="_atl_base_module"></a><a name="_atl_base_module"></a>_ATL_BASE_MODULE

Défini comme un dactylographe basé sur _ATL_BASE_MODULE70.

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Notes

Utilisé dans chaque projet ATL. Basé sur [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).

Les classes qui font partie des classes de module ATL 7.0 proviennent de la structure _ATL_BASE_MODULE.  Pour plus d’informations sur les classes de modules ATL, consultez [les classes de modules COM](../../atl/com-modules-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlcore.h

## <a name="_atl_com_module"></a><a name="_atl_com_module"></a>_ATL_COM_MODULE

Défini comme un dactylographe basé sur _ATL_COM_MODULE70.

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Notes

Utilisé par les projets ATL qui utilisent les fonctionnalités COM. Basé sur [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="_atl_module"></a><a name="_atl_module"></a>_ATL_MODULE

Défini comme un dactylographe basé sur _ATL_MODULE70.

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>Spécifications

**En-tête:**

### <a name="remarks"></a>Notes

Basé sur [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).

## <a name="_atl_win_module"></a><a name="_atl_win_module"></a>_ATL_WIN_MODULE

Défini comme un dactylographe basé sur _ATL_WIN_MODULE70.

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Notes

Utilisé par tous les projets ATL qui utilisent des fonctionnalités de fenêtre. Basé sur [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="atl_url_port"></a><a name="atl_url_port"></a>ATL_URL_PORT

Le type utilisé par [CUrl](curl-class.md) pour spécifier un numéro de port.

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>Spécifications

**En-tête:** atlutil.h

## <a name="ccomdispatchdriver"></a><a name="ccomdispatchdriver"></a>CComDispatchDriver

Cette classe gère les pointeurs d’interface COM.

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccomglobalsthreadmodel"></a><a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel

Appelle les méthodes appropriées de modèle de fil, indépendamment du modèle de threading utilisé.

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

Selon le modèle de threading utilisé par votre `CComGlobalsThreadModel` application, le nom **dactylographe** fait référence soit [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) ou [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Ces classes `typedef` fournissent des noms supplémentaires pour faire référence à une classe de section critique.

> [!NOTE]
> `CComGlobalsThreadModel`ne fait pas référence à la classe [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

À `CComGlobalsThreadModel` l’aide de vous libère de spécifier une classe de modèle de threading particulier. Quel que soit le modèle de threading utilisé, les méthodes appropriées seront appelées.

En plus `CComGlobalsThreadModel`de , ATL fournit le nom **de dactylographe** [CComObjectThreadModel](#ccomobjectthreadmodel). La classe référencée par chacun `typedef` dépend du modèle de threading utilisé, comme indiqué dans le tableau suivant :

|typedef|Filet unique|Threading appartement|Threading gratuit|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S `CComSingleThreadModel`' ; M`CComMultiThreadModel`

Utiliser `CComObjectThreadModel` dans une seule classe d’objets. Utilisez-le `CComGlobalsThreadModel` dans un objet disponible à l’échelle mondiale pour votre programme, ou lorsque vous souhaitez protéger les ressources du module sur plusieurs threads.

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccomobjectthreadmodel"></a><a name="ccomobjectthreadmodel"></a>CComObjectThreadModel

Appelle les méthodes appropriées de modèle de fil, indépendamment du modèle de threading utilisé.

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

Selon le modèle de threading utilisé `typedef` `CComObjectThreadModel` par votre application, le nom fait référence soit [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) ou [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Ces classes `typedef` fournissent des noms supplémentaires pour faire référence à une classe de section critique.

> [!NOTE]
> `CComObjectThreadModel`ne fait pas référence à la classe [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

À `CComObjectThreadModel` l’aide de vous libère de spécifier une classe de modèle de threading particulier. Quel que soit le modèle de threading utilisé, les méthodes appropriées seront appelées.

En plus `CComObjectThreadModel`de , ATL fournit le nom **dactylographié** [CComGlobalsThreadModel](#ccomglobalsthreadmodel). La classe référencée par chaque **type** dépend du modèle de threading utilisé, comme indiqué dans le tableau suivant :

|typedef|Filet unique|Threading appartement|Threading gratuit|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S `CComSingleThreadModel`' ; M`CComMultiThreadModel`

Utiliser `CComObjectThreadModel` dans une seule classe d’objets. Utilisez-le `CComGlobalsThreadModel` dans un objet disponible soit globalement pour votre programme, soit lorsque vous souhaitez protéger les ressources du module sur plusieurs threads.

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccontainedwindow"></a><a name="ccontainedwindow"></a>CContainedWindow

Cette classe est une `CContainedWindowT`spécialisation de .

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

### <a name="remarks"></a>Notes

`CContainedWindow`est une spécialisation de [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Si vous voulez changer la classe de `CContainedWindowT` base ou les traits, utilisez directement.

## <a name="cpath"></a><a name="cpath"></a>CPath (en)

Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide `CString`de .

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>Spécifications

**En-tête:** atlpath.h

## <a name="cpatha"></a><a name="cpatha"></a>CPathA (en)

Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide `CStringA`de .

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>Spécifications

**En-tête:** atlpath.h

## <a name="cpathw"></a><a name="cpathw"></a>CPathW (en)

Une spécialisation de [CPathT](../../atl/reference/cpatht-class.md) à l’aide `CStringW`de .

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>Spécifications

**En-tête:** atlpath.h

## <a name="csimplevalarray"></a><a name="csimplevalarray"></a>CSimpleValArray

Représente un tableau pour stocker des types simples.

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Notes

`CSimpleValArray`est prévu pour la création et la gestion de tableaux contenant des types de données simples. Il s’agit d’une simple #define de [CSimpleArray](../../atl/reference/csimplearray-class.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlsimpcoll.h

## <a name="lpcurl"></a><a name="lpcurl"></a>LPCURL

Un pointeur vers un objet [CUrl](../../atl/reference/curl-class.md) constant.

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>Spécifications

**En-tête:** atlutil.h

## <a name="defaultthreadtraits"></a><a name="defaultthreadtraits"></a>DéfautThreadTraits

La classe des traits de thread par défaut.

### <a name="syntax"></a>Syntaxe

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Notes

Si le projet actuel utilise le CRT multithreaded, DefaultThreadTraits est défini comme CRTThreadTraits. Sinon, Win32ThreadTraits est utilisé.

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="lpurl"></a><a name="lpurl"></a>LPURL (LPURL)

Un pointeur sur un objet [CUrl.](../../atl/reference/curl-class.md)

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>Spécifications

**En-tête:** atlutil.h

## <a name="see-also"></a>Voir aussi

[Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)<br/>
[Fonctions](../../atl/reference/atl-functions.md)<br/>
[Variables globales](../../atl/reference/atl-global-variables.md)<br/>
[Classes et structs](../../atl/reference/atl-classes.md)<br/>
[Macros](../../atl/reference/atl-macros.md)
