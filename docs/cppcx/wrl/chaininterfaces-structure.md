---
title: ChainInterfaces (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
- implements/Microsoft::WRL::ChainInterfaces::IidCount
- implements/Microsoft::WRL::ChainInterfaces::Verify
helpviewer_keywords:
- Microsoft::WRL::ChainInterfaces structure
- Microsoft::WRL::ChainInterfaces::CanCastTo method
- Microsoft::WRL::ChainInterfaces::CastToUnknown method
- Microsoft::WRL::ChainInterfaces::FillArrayWithIid method
- Microsoft::WRL::ChainInterfaces::IidCount constant
- Microsoft::WRL::ChainInterfaces::Verify method
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
ms.openlocfilehash: 48b663f2042ff0095466d83fe872ef6196112f76
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211539"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces (structure)

Spécifie les fonctions de vérification et d'initialisation pouvant être appliquées à un ensemble d'ID d'interface.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename I0,
    typename I1,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct ChainInterfaces : I0;

template <
    typename DerivedType,
    typename BaseType,
    bool hasImplements,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8,
    typename I9
>
struct ChainInterfaces<
    MixIn<
        DerivedType,
        BaseType,
        hasImplements
    >, I1, I2, I3, I4, I5, I6, I7, I8, I9
>;
```

### <a name="parameters"></a>Paramètres

*I0*<br/>
Souhaitée ID d’interface 0.

*I1*<br/>
Souhaitée ID d’interface 1.

*I2*<br/>
Facultatif ID d’interface 2.

*I3*<br/>
Facultatif ID d’interface 3.

*I4*<br/>
Facultatif ID d’interface 4.

*I5*<br/>
Facultatif ID d’interface 5.

*I6*<br/>
Facultatif ID d’interface 6.

*I7*<br/>
Facultatif ID d’interface 7.

*I8*<br/>
Facultatif ID d’interface 8.

*I9*<br/>
Facultatif ID d’interface 9.

*DerivedType*<br/>
Type dérivé.

*BaseType*<br/>
Type de base d’un type dérivé.

*hasImplements*<br/>
Valeur booléenne qui, si **`true`** , signifie que vous ne pouvez pas utiliser une structure [MixIn](mixin-structure.md) avec une classe qui ne dérive pas de la structure [Implements](implements-structure.md) .

## <a name="members"></a>Membres

### <a name="protected-methods"></a>Méthodes protégées

Nom                                                   | Description
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ChainInterfaces :: CanCastTo,](#cancastto)               | Indique si l’ID d’interface spécifié peut être casté en chacune des spécialisations définies par les `ChainInterface` paramètres du modèle.
[ChainInterfaces :: Casttounknown,](#casttounknown)       | Convertit le pointeur d’interface du type défini par le paramètre de modèle *I0* en pointeur vers `IUnknown` .
[ChainInterfaces :: Fillarraywithiid,](#fillarraywithiid) | Stocke l’ID d’interface défini par le paramètre de modèle *I0* dans un emplacement spécifié dans un tableau d’ID d’interface spécifié.
[ChainInterfaces :: Verify](#verify)                     | Vérifie que chaque interface définie par les paramètres de modèle *I0* via *i9* hérite de `IUnknown` et/ou `IInspectable` , et que *I0* hérite de *I1* à *i9*.

### <a name="protected-constants"></a>Constantes protégées

Nom                                   | Description
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[ChainInterfaces :: Iidcount,](#iidcount) | Nombre total d’ID d’interface contenus dans les interfaces spécifiées par les paramètres de modèle *I0* à *i9*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`I0`

`ChainInterfaces`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="chaininterfacescancastto"></a><a name="cancastto"></a>ChainInterfaces :: CanCastTo,

Indique si l’ID d’interface spécifié peut être casté en chacune des spécialisations définies par les paramètres de modèle non définis par défaut.

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
ID d’interface.

*ppv*<br/>
Pointeur vers le dernier ID d’interface qui a été correctement converti.

### <a name="return-value"></a>Valeur de retour

**`true`** Si toutes les opérations de conversion réussissent ; Sinon, **`false`** .

## <a name="chaininterfacescasttounknown"></a><a name="casttounknown"></a>ChainInterfaces :: Casttounknown,

Convertit le pointeur d’interface du type défini par le paramètre de modèle *I0* en pointeur vers `IUnknown` .

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers `IUnknown`.

## <a name="chaininterfacesfillarraywithiid"></a><a name="fillarraywithiid"></a>ChainInterfaces :: Fillarraywithiid,

Stocke l’ID d’interface défini par le paramètre de modèle *I0* dans un emplacement spécifié dans un tableau d’ID d’interface spécifié.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Pointeur vers une valeur d’index dans le tableau *IID* .

*IID*<br/>
Tableau d’ID d’interface.

## <a name="chaininterfacesiidcount"></a><a name="iidcount"></a>ChainInterfaces :: Iidcount,

Nombre total d’ID d’interface contenus dans les interfaces spécifiées par les paramètres de modèle *I0* à *i9*.

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>Valeur de retour

Nombre total d’ID d’interface.

### <a name="remarks"></a>Notes

Les paramètres de modèle *I0* et *I1* sont requis, et les paramètres *I2* à *i9* sont facultatifs. Le nombre d’IID de chaque interface est généralement 1.

## <a name="chaininterfacesverify"></a><a name="verify"></a>ChainInterfaces :: Verify

Vérifie que chaque interface définie par les paramètres de modèle *I0* via *i9* hérite de `IUnknown` et/ou `IInspectable` , et que *I0* hérite de *I1* à *i9*.

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>Notes

Si l’opération de vérification échoue, un **`static_assert`** émet un message d’erreur décrivant l’échec.

Les paramètres de modèle *I0* et *I1* sont requis, et les paramètres *I2* à *i9* sont facultatifs.
