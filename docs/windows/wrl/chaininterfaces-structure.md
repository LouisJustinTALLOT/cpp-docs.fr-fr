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
ms.openlocfilehash: 9fd315f017d3dcc9823054ea99e845ec99bc4192
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336015"
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
(Obligatoire) ID d’interface 0.

*I1*<br/>
(Obligatoire) ID d’interface 1.

*I2*<br/>
(Facultatif) ID d’interface 2.

*I3*<br/>
(Facultatif) ID d’interface 3.

*I4*<br/>
(Facultatif) ID d’interface 4.

*I5*<br/>
(Facultatif) ID d’interface 5.

*I6*<br/>
(Facultatif) ID d’interface 6.

*I7*<br/>
(Facultatif) ID d’interface 7.

*I8*<br/>
(Facultatif) ID d’interface 8.

*I9*<br/>
(Facultatif) ID d’interface 9.

*DerivedType*<br/>
Un type dérivé.

*BaseType*<br/>
Le type de base d’un type dérivé.

*hasImplements*<br/>
Une valeur booléenne qu’if **true**, signifie que vous ne pouvez pas utiliser un [MixIn](mixin-structure.md) structure avec une classe qui ne dérive pas de la [implémente](implements-structure.md) structure.

## <a name="members"></a>Membres

### <a name="protected-methods"></a>Méthodes protégées

Nom                                                   | Description
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ChainInterfaces::CanCastTo](#cancastto)               | Indique si l’ID d’interface spécifié peut être casté à chacune des spécialisations définies par le `ChainInterface` paramètres de modèle.
[ChainInterfaces::CastToUnknown](#casttounknown)       | Convertit le pointeur d’interface du type défini par le *I0* paramètre de modèle à un pointeur vers `IUnknown`.
[ChainInterfaces::FillArrayWithIid](#fillarraywithiid) | Stocke l’ID d’interface définie par le *I0* paramètre de modèle dans un emplacement spécifié dans un tableau spécifié d’ID d’interface.
[ChainInterfaces::Verify](#verify)                     | Vérifie que chaque interface définie par les paramètres de modèle *I0* via *I9* hérite `IUnknown` et/ou `IInspectable`et qui *I0* hérite de *I1* via *I9*.

### <a name="protected-constants"></a>Constantes protégés

Name                                   | Description
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[ChainInterfaces::IidCount](#iidcount) | Le nombre total d’ID contenues dans les interfaces spécifiées par les paramètres de modèle d’interface *I0* via *I9*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`I0`

`ChainInterfaces`

## <a name="requirements"></a>Spécifications

**En-tête :** implements.h

**Espace de noms :** Microsoft::wrl

## <a name="cancastto"></a>ChainInterfaces::CanCastTo

Indique si l’ID d’interface spécifié peut être casté à chacune des spécialisations définies par les paramètres du modèle de celle par défaut.

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
Pointeur vers le dernier ID d’interface qui a été converti avec succès.

### <a name="return-value"></a>Valeur de retour

**true** si toutes les opérations de cast a réussi ; sinon, **false**.

## <a name="casttounknown"></a>ChainInterfaces::CastToUnknown

Convertit le pointeur d’interface du type défini par le *I0* paramètre de modèle à un pointeur vers `IUnknown`.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers `IUnknown`.

## <a name="fillarraywithiid"></a>ChainInterfaces::FillArrayWithIid

Stocke l’ID d’interface définie par le *I0* paramètre de modèle dans un emplacement spécifié dans un tableau spécifié d’ID d’interface.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Pointeur vers une valeur d’index dans le *IID* tableau.

*iids*<br/>
Tableau d’ID d’interface.

## <a name="iidcount"></a>ChainInterfaces::IidCount

Le nombre total d’ID contenues dans les interfaces spécifiées par les paramètres de modèle d’interface *I0* via *I9*.

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>Valeur de retour

Le nombre total de l’ID d’interface.

### <a name="remarks"></a>Notes

Paramètres de modèle *I0* et *I1* sont nécessaires et les paramètres *I2* via *I9* sont facultatifs. Le nombre de l’IID de chaque interface est généralement de 1.

## <a name="verify"></a>ChainInterfaces::Verify

Vérifie que chaque interface définie par les paramètres de modèle *I0* via *I9* hérite `IUnknown` et/ou `IInspectable`et qui *I0* hérite de *I1* via *I9*.

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>Notes

Si l’opération de vérification échoue, un `static_assert` émet un message d’erreur qui décrit l’échec.

Paramètres de modèle *I0* et *I1* sont nécessaires et les paramètres *I2* via *I9* sont facultatifs.
