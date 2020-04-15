---
title: InterfaceTraits (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
- implements/Microsoft::WRL::Details::InterfaceTraits::IidCount
- implements/Microsoft::WRL::Details::InterfaceTraits::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::InterfaceTraits structure
- Microsoft::WRL::Details::InterfaceTraits::CanCastTo method
- Microsoft::WRL::Details::InterfaceTraits::CastToBase method
- Microsoft::WRL::Details::InterfaceTraits::CastToUnknown method
- Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid method
- Microsoft::WRL::Details::InterfaceTraits::IidCount constant
- Microsoft::WRL::Details::InterfaceTraits::Verify method
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
ms.openlocfilehash: 17f743a38af3ddc600a55e38905d19868d076a22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371372"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename I0>
struct __declspec(novtable) InterfaceTraits;

template<typename CloakedType>
struct __declspec(novtable) InterfaceTraits<
    CloakedIid<CloakedType>
>;

template<>
struct __declspec(novtable) InterfaceTraits<Nil>;
```

### <a name="parameters"></a>Paramètres

*I0*<br/>
Le nom d’une interface.

*CloakedType*<br/>
Pour `RuntimeClass` `Implements` , `ChainInterfaces`et , une interface qui ne sera pas dans la liste des interfaces prises en charge.

## <a name="remarks"></a>Notes

Implémente les caractéristiques communes d’une interface.

Le deuxième modèle est une spécialisation pour les interfaces masquées. Le troisième modèle est une spécialisation des paramètres Nil.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a><a name="public-typedefs"></a>Typesdefs publics

Nom   | Description
------ | ------------------------------------------
`Base` | Un synonyme du paramètre du modèle *I0.*

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                   | Description
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[InterfaceTraits::CanCastTo](#cancastto)               | Indique si le pointeur spécifié peut `Base`être jeté à un pointeur à .
[InterfaceTraits::CastToBase](#casttobase)             | Lance le pointeur spécifié `Base`à un pointeur à .
[InterfaceTraits::CastToUnknown](#casttounknown)       | Lance le pointeur spécifié `IUnknown`à un pointeur à .
[InterfaceTraits::FillArrayWithIid](#fillarraywithiid) | Assigne l’interface `Base` ID de l’élément de tableau spécifié par l’argument de l’index.
[InterfaceTraits::Vérifier](#verify)                     | Vérifie qui `Base` est correctement dérivé.

### <a name="public-constants"></a>Constantes publiques

Nom                                   | Description
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits::IidCount](#iidcount) | Détient le nombre d’interfaces d’interface associées à l’objet actuel. `InterfaceTraits`

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`InterfaceTraits`

## <a name="requirements"></a>Spécifications

**En-tête:** implements.h

**Espace nom:** Microsoft::WRL::Details

## <a name="interfacetraitscancastto"></a><a name="cancastto"></a>InterfaceTraits::CanCastTo

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Paramètres

*Ptr*<br/>
Le nom d’un pointeur à un type.

*riid*<br/>
L’interface `Base`ID de .

*Ppv*<br/>
Si cette opération est réussie, *ppv* `Base`pointe vers l’interface spécifiée par . Sinon, *ppv* est `nullptr`réglé à .

### <a name="return-value"></a>Valeur de retour

**vrai** si cette opération est réussie et *ptr* est jeté à un pointeur à `Base`; autrement, **faux**.

### <a name="remarks"></a>Notes

Indique si le pointeur spécifié peut `Base`être jeté à un pointeur à .

Pour plus `Base`d’informations sur , voir la section [Dudefs publics.](#public-typedefs)

## <a name="interfacetraitscasttobase"></a><a name="casttobase"></a>InterfaceTraits::CastToBase

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de paramètre *ptr*.

*Ptr*<br/>
Pointeur à un type *T*.

### <a name="return-value"></a>Valeur de retour

Pointeur vers `Base`.

### <a name="remarks"></a>Notes

Lance le pointeur spécifié `Base`à un pointeur à .

Pour plus `Base`d’informations sur , voir la section [Dudefs publics.](#public-typedefs)

## <a name="interfacetraitscasttounknown"></a><a name="casttounknown"></a>InterfaceTraits::CastToUnknown

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de paramètre *ptr*.

*Ptr*<br/>
Pointeur pour taper *T*.

### <a name="return-value"></a>Valeur de retour

Pointeur à l’IUnknown à partir de laquelle `Base` est dérivé.

### <a name="remarks"></a>Notes

Lance le pointeur spécifié `IUnknown`à un pointeur à .

Pour plus `Base`d’informations sur , voir la section [Dudefs publics.](#public-typedefs)

## <a name="interfacetraitsfillarraywithiid"></a><a name="fillarraywithiid"></a>InterfaceTraits::FillArrayWithIid

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Pointeur vers un champ qui contient une valeur d’index à base de zéro.

*iids*<br/>
Une gamme d’interfaces.

### <a name="remarks"></a>Notes

Assigne l’interface `Base` ID de l’élément de tableau spécifié par l’argument de l’index.

Contrairement au nom de cette API, un seul élément de tableau est modifié; pas tout le tableau.

Pour plus `Base`d’informations sur , voir la section [Dudefs publics.](#public-typedefs)

## <a name="interfacetraitsiidcount"></a><a name="iidcount"></a>InterfaceTraits::IidCount

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>Notes

Détient le nombre d’interfaces d’interface associées à l’objet actuel. `InterfaceTraits`

## <a name="interfacetraitsverify"></a><a name="verify"></a>InterfaceTraits::Vérifier

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>Notes

Vérifie qui `Base` est correctement dérivé.

Pour plus `Base`d’informations sur , voir la section [Dudefs publics.](#public-typedefs)
