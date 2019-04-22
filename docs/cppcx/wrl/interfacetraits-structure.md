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
ms.openlocfilehash: e8222ccaca9572331412b90e696829568eedcf8e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784607"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

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
Pour `RuntimeClass`, `Implements` et `ChainInterfaces`, une interface qui ne sera pas dans la liste de prise en charge les ID d’interface.

## <a name="remarks"></a>Notes

Caractéristiques communes d’implémente d’une interface.

Le deuxième modèle est une spécialisation pour les interfaces masqués. Le troisième modèle est une spécialisation pour les paramètres Nil.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom   | Description
------ | ------------------------------------------
`Base` | Un synonyme pour le *I0* paramètre de modèle.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                   | Description
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[InterfaceTraits::CanCastTo](#cancastto)               | Indique si le pointeur spécifié peut être casté en un pointeur vers `Base`.
[InterfaceTraits::CastToBase](#casttobase)             | Effectue un cast du pointeur spécifié vers un pointeur vers `Base`.
[InterfaceTraits::CastToUnknown](#casttounknown)       | Effectue un cast du pointeur spécifié vers un pointeur vers `IUnknown`.
[InterfaceTraits::FillArrayWithIid](#fillarraywithiid) | Attribue l’ID de l’interface de `Base` à l’élément de tableau spécifié par l’argument d’index.
[InterfaceTraits::Verify](#verify)                     | Vérifie que `Base` est dérivé correctement.

### <a name="public-constants"></a>Constantes publiques

Nom                                   | Description
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits::IidCount](#iidcount) | Contient le nombre d’ID associés en cours d’interface `InterfaceTraits` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`InterfaceTraits`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="cancastto"></a>InterfaceTraits::CanCastTo

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

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
Le nom d’un pointeur vers un type.

*riid*<br/>
L’ID d’interface de `Base`.

*ppv*<br/>
Si cette opération est réussie, *ppv* pointe vers l’interface spécifiée par `Base`. Sinon, *ppv* est défini sur `nullptr`.

### <a name="return-value"></a>Valeur de retour

**true** si cette opération réussit et *ptr* est casté en un pointeur vers `Base`; sinon, **false**.

### <a name="remarks"></a>Notes

Indique si le pointeur spécifié peut être casté en un pointeur vers `Base`.

Pour plus d’informations sur `Base`, consultez le [Typedefs publics](#public-typedefs) section.

## <a name="casttobase"></a>InterfaceTraits::CastToBase

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de paramètre *ptr*.

*ptr*<br/>
Pointeur vers un type *T*.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers `Base`.

### <a name="remarks"></a>Notes

Effectue un cast du pointeur spécifié vers un pointeur vers `Base`.

Pour plus d’informations sur `Base`, consultez le [Typedefs publics](#public-typedefs) section.

## <a name="casttounknown"></a>InterfaceTraits::CastToUnknown

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de paramètre *ptr*.

*ptr*<br/>
Pointeur vers le type *T*.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’interface IUnknown à partir de laquelle `Base` est dérivée.

### <a name="remarks"></a>Notes

Effectue un cast du pointeur spécifié vers un pointeur vers `IUnknown`.

Pour plus d’informations sur `Base`, consultez le [Typedefs publics](#public-typedefs) section.

## <a name="fillarraywithiid"></a>InterfaceTraits::FillArrayWithIid

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Pointeur vers un champ qui contient une valeur d’index de base zéro.

*iids*<br/>
Tableau d’ID d’interface.

### <a name="remarks"></a>Notes

Attribue l’ID de l’interface de `Base` à l’élément de tableau spécifié par l’argument d’index.

Contrairement au nom de cette API, élément de tableau qu’une seule est modifiée ; pas l’intégralité du tableau.

Pour plus d’informations sur `Base`, consultez le [Typedefs publics](#public-typedefs) section.

## <a name="iidcount"></a>InterfaceTraits::IidCount

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>Notes

Contient le nombre d’ID associés en cours d’interface `InterfaceTraits` objet.

## <a name="verify"></a>InterfaceTraits::Verify

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>Notes

Vérifie que `Base` est dérivé correctement.

Pour plus d’informations sur `Base`, consultez le [Typedefs publics](#public-typedefs) section.
