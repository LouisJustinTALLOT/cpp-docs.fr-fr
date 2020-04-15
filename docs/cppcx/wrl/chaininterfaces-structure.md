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
ms.openlocfilehash: dd1af3fb5c1079a40d8248dc71ae4972537aa856
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372651"
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
(Requis) Interface ID 0.

*I1 (en)*<br/>
(Requis) Interface ID 1.

*I2 (en)*<br/>
(Facultatif) Interface ID 2.

*I3 (en)*<br/>
(Facultatif) Interface ID 3.

*I4 (en)*<br/>
(Facultatif) Interface ID 4.

*I5 (en)*<br/>
(Facultatif) Interface ID 5.

*I6 (en)*<br/>
(Facultatif) Interface ID 6.

*I7 (en)*<br/>
(Facultatif) Interface ID 7.

*I8 (en)*<br/>
(Facultatif) Interface ID 8.

*I9 (en)*<br/>
(Facultatif) Interface ID 9.

*DérivéType*<br/>
Un type dérivé.

*BaseType*<br/>
Le type de base d’un type dérivé.

*aImplements*<br/>
Une valeur Boolean qui, si elle est **vraie,** signifie que vous ne pouvez pas utiliser une structure [MixIn](mixin-structure.md) avec une classe qui ne dérive pas de la stucture [Implements.](implements-structure.md)

## <a name="members"></a>Membres

### <a name="protected-methods"></a>Méthodes protégées

Nom                                                   | Description
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ChainInterfaces::CanCastTo](#cancastto)               | Indique si l’ID d’interface spécifié peut être lancé `ChainInterface` à chacune des spécialisations définies par les paramètres du modèle.
[ChainInterfaces::CastToUnknown](#casttounknown)       | Lance le pointeur d’interface du type défini par `IUnknown`le paramètre du modèle *I0* à un pointeur à .
[ChainInterfaces::FillArrayWithIid](#fillarraywithiid) | Stocke l’interface ID définie par le paramètre du modèle *I0* dans un emplacement spécifié dans un tableau spécifié d’identifiants d’interface.
[ChainInterfaces::Vérifier](#verify)                     | Vérifie que chaque interface définie par les paramètres du `IUnknown` modèle *I0* à travers *I9* hérite de et / ou `IInspectable`, et que *I0* hérite de *I1* à *I9*.

### <a name="protected-constants"></a>Constants protégés

Nom                                   | Description
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[ChainInterfaces::IidCount](#iidcount) | Le nombre total d’interfaces id dans les interfaces spécifiées par les paramètres du modèle *I0* via *I9*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`I0`

`ChainInterfaces`

## <a name="requirements"></a>Spécifications

**En-tête:** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="chaininterfacescancastto"></a><a name="cancastto"></a>ChainInterfaces::CanCastTo

Indique si l’ID d’interface spécifié peut être lancé à chacune des spécialisations définies par les paramètres du modèle non par défaut.

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
ID d’interface.

*Ppv*<br/>
Un pointeur à la dernière interface ID qui a été jeté avec succès.

### <a name="return-value"></a>Valeur de retour

**vrai** si toutes les opérations de casting ont réussi; autrement, **faux**.

## <a name="chaininterfacescasttounknown"></a><a name="casttounknown"></a>ChainInterfaces::CastToUnknown

Lance le pointeur d’interface du type défini par `IUnknown`le paramètre du modèle *I0* à un pointeur à .

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers `IUnknown`.

## <a name="chaininterfacesfillarraywithiid"></a><a name="fillarraywithiid"></a>ChainInterfaces::FillArrayWithIid

Stocke l’interface ID définie par le paramètre du modèle *I0* dans un emplacement spécifié dans un tableau spécifié d’identifiants d’interface.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Pointeur vers une valeur d’index dans le tableau *iids.*

*iids*<br/>
Une gamme d’interfaces.

## <a name="chaininterfacesiidcount"></a><a name="iidcount"></a>ChainInterfaces::IidCount

Le nombre total d’interfaces id dans les interfaces spécifiées par les paramètres du modèle *I0* via *I9*.

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>Valeur de retour

Le nombre total d’interfaces iD.

### <a name="remarks"></a>Notes

Paramètres de modèle *I0* et *I1* sont nécessaires, et les paramètres *I2* à *I9* sont facultatifs. Le nombre d’IID de chaque interface est généralement 1.

## <a name="chaininterfacesverify"></a><a name="verify"></a>ChainInterfaces::Vérifier

Vérifie que chaque interface définie par les paramètres du `IUnknown` modèle *I0* à travers *I9* hérite de et / ou `IInspectable`, et que *I0* hérite de *I1* à *I9*.

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>Notes

Si l’opération de `static_assert` vérification échoue, un émetteur d’un message d’erreur décrivant l’échec.

Paramètres de modèle *I0* et *I1* sont nécessaires, et les paramètres *I2* à *I9* sont facultatifs.
