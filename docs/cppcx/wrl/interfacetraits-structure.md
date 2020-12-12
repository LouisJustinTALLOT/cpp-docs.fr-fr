---
description: 'En savoir plus sur : structure InterfaceTraits'
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
ms.openlocfilehash: 8dfa540119b0a120ea7b8d9365a0e8b8203939b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124525"
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
Nom d’une interface.

*CloakedType*<br/>
Pour `RuntimeClass` , `Implements` et `ChainInterfaces` , il s’agit d’une interface qui ne figurera pas dans la liste des ID d’interface pris en charge.

## <a name="remarks"></a>Notes

Implémente les caractéristiques communes d’une interface.

Le deuxième modèle est une spécialisation pour les interfaces masquées. Le troisième modèle est une spécialisation pour les paramètres Nil.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a><a name="public-typedefs"></a> Typedefs publics

Nom   | Description
------ | ------------------------------------------
`Base` | Synonyme du paramètre de modèle *I0* .

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                   | Description
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[InterfaceTraits :: CanCastTo,](#cancastto)               | Indique si le pointeur spécifié peut être casté en pointeur vers `Base` .
[InterfaceTraits :: Casttobase,](#casttobase)             | Effectue un cast du pointeur spécifié vers un pointeur vers `Base` .
[InterfaceTraits :: Casttounknown,](#casttounknown)       | Effectue un cast du pointeur spécifié vers un pointeur vers `IUnknown` .
[InterfaceTraits :: Fillarraywithiid,](#fillarraywithiid) | Affecte l’ID d’interface de `Base` à l’élément de tableau spécifié par l’argument d’index.
[InterfaceTraits :: Verify](#verify)                     | Vérifie que `Base` est correctement dérivé.

### <a name="public-constants"></a>Constantes publiques

Nom                                   | Description
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits :: Iidcount,](#iidcount) | Contient le nombre d’ID d’interface associés à l' `InterfaceTraits` objet actuel.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`InterfaceTraits`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="interfacetraitscancastto"></a><a name="cancastto"></a> InterfaceTraits :: CanCastTo,

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

*ptr*<br/>
Nom d’un pointeur vers un type.

*riid*<br/>
ID d’interface de `Base` .

*ppv*<br/>
Si cette opération réussit, *PPV* pointe vers l’interface spécifiée par `Base` . Sinon, *PPV* a la valeur **`nullptr`** .

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si cette opération réussit et que *ptr* est casté en pointeur vers `Base` ; sinon, **`false`** .

### <a name="remarks"></a>Notes

Indique si le pointeur spécifié peut être casté en pointeur vers `Base` .

Pour plus d’informations sur `Base` , consultez la section [typedefs publics](#public-typedefs) .

## <a name="interfacetraitscasttobase"></a><a name="casttobase"></a> InterfaceTraits :: Casttobase,

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de *ptr* du paramètre.

*ptr*<br/>
Pointeur vers un type *T*.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers `Base`.

### <a name="remarks"></a>Notes

Effectue un cast du pointeur spécifié vers un pointeur vers `Base` .

Pour plus d’informations sur `Base` , consultez la section [typedefs publics](#public-typedefs) .

## <a name="interfacetraitscasttounknown"></a><a name="casttounknown"></a> InterfaceTraits :: Casttounknown,

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type de *ptr* du paramètre.

*ptr*<br/>
Pointeur vers le type *T*.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers IUnknown à partir duquel `Base` est dérivé.

### <a name="remarks"></a>Notes

Effectue un cast du pointeur spécifié vers un pointeur vers `IUnknown` .

Pour plus d’informations sur `Base` , consultez la section [typedefs publics](#public-typedefs) .

## <a name="interfacetraitsfillarraywithiid"></a><a name="fillarraywithiid"></a> InterfaceTraits :: Fillarraywithiid,

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Pointeur vers un champ qui contient une valeur d’index de base zéro.

*IID*<br/>
Tableau d’ID d’interface.

### <a name="remarks"></a>Notes

Affecte l’ID d’interface de `Base` à l’élément de tableau spécifié par l’argument d’index.

Contrairement au nom de cette API, un seul élément de tableau est modifié ; ce n’est pas le tableau entier.

Pour plus d’informations sur `Base` , consultez la section [typedefs publics](#public-typedefs) .

## <a name="interfacetraitsiidcount"></a><a name="iidcount"></a> InterfaceTraits :: Iidcount,

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>Notes

Contient le nombre d’ID d’interface associés à l' `InterfaceTraits` objet actuel.

## <a name="interfacetraitsverify"></a><a name="verify"></a> InterfaceTraits :: Verify

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>Notes

Vérifie que `Base` est correctement dérivé.

Pour plus d’informations sur `Base` , consultez la section [typedefs publics](#public-typedefs) .
