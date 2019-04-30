---
title: Implements (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
- implements/Microsoft::WRL::Implements::CanCastTo
- implements/Microsoft::WRL::Implements::CastToUnknown
- implements/Microsoft::WRL::Implements::FillArrayWithIid
- implements/Microsoft::WRL::Implements::IidCount
helpviewer_keywords:
- Microsoft::WRL::Implements structure
- Microsoft::WRL::Implements::CanCastTo method
- Microsoft::WRL::Implements::CastToUnknown method
- Microsoft::WRL::Implements::FillArrayWithIid method
- Microsoft::WRL::Implements::IidCount method
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
ms.openlocfilehash: 63cac6931428644cc5ddec7d87e49007e95e039d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398248"
---
# <a name="implements-structure"></a>Implements (structure)

Implémente `QueryInterface` et `GetIid` pour les interfaces spécifiées.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename I0,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct __declspec(novtable) Implements :
    Details::ImplementsHelper<
        RuntimeClassFlags<WinRt>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8, I9
        >::TypeT
    >,
    Details::ImplementsBase;

template <
    int flags,
    typename I0,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8
>
struct __declspec(novtable) Implements<
        RuntimeClassFlags<flags>,
        I0, I1, I2, I3, I4, I5, I6, I7, I8> :
    Details::ImplementsHelper<
        RuntimeClassFlags<flags>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8
        >::TypeT
    >,
    Details::ImplementsBase;
```

### <a name="parameters"></a>Paramètres

*I0*<br/>
L’ID d’interface de zéro. (Obligatoire)

*I1*<br/>
Le premier ID d’interface. (facultatif)

*I2*<br/>
Le deuxième ID d’interface. (facultatif)

*I3*<br/>
Le troisième ID d’interface. (facultatif)

*I4*<br/>
La quatrième ID d’interface. (facultatif)

*I5*<br/>
Le cinquième ID d’interface. (facultatif)

*I6*<br/>
Le sixième ID d’interface. (facultatif)

*I7*<br/>
Le septième ID d’interface. (facultatif)

*I8*<br/>
L’ID d’interface huitième. (facultatif)

*I9*<br/>
Le neuvième ID d’interface. (facultatif)

*flags*<br/>
Indicateurs de configuration pour la classe. Un ou plusieurs [RuntimeClassType](runtimeclasstype-enumeration.md) énumérations qui sont spécifiées dans un [RuntimeClassFlags](runtimeclassflags-structure.md) structure.

## <a name="remarks"></a>Notes

Dérive de la liste des interfaces spécifiées et implémente des modèles d’assistance pour `QueryInterface` et `GetIid`.

Chaque *I0* via *I9* paramètre d’interface doit être dérivé `IUnknown`, `IInspectable`, ou le [ChainInterfaces](chaininterfaces-structure.md) modèle. Le *indicateurs* paramètre détermine si la prise en charge est généré pour `IUnknown` ou `IInspectable`.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

| Nom        | Description                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| Synonyme de `RuntimeClassFlags<WinRt>`. |

### <a name="protected-methods"></a>Méthodes protégées

| Nom                                              | Description                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implements::CanCastTo](#cancastto)               | Obtient un pointeur vers l’interface spécifiée.                                                                    |
| [Implements::CastToUnknown](#casttounknown)       | Obtient un pointeur vers sous-jacent `IUnknown` interface.                                                        |
| [Implements::FillArrayWithIid](#fillarraywithiid) | Insère l’ID d’interface spécifié par le paramètre de modèle actuel placée dans l’élément de tableau spécifié. |

### <a name="protected-constants"></a>Constantes protégés

| Nom                              | Description                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implements::IidCount](#iidcount) | Contient le nombre d’ID d’interface implémentée. |

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::wrl

## <a name="cancastto"></a>Implements::CanCastTo

Obtient un pointeur vers l’interface spécifiée.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
Une référence à un ID d’interface.

*ppv*<br/>
Si réussie, un pointeur vers l’interface spécifiée par *riid*.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, un HRESULT qui indique l’erreur, telles que E_NOINTERFACE.

### <a name="remarks"></a>Notes

Il s’agit d’une fonction d’assistance interne qui exécute une opération de QueryInterface.

## <a name="casttounknown"></a>Implements::CastToUnknown

Obtient un pointeur vers sous-jacent `IUnknown` interface.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valeur de retour

Cette opération réussit et retourne toujours le `IUnknown` pointeur.

### <a name="remarks"></a>Notes

Fonction d’assistance interne.

## <a name="fillarraywithiid"></a>Implements::FillArrayWithIid

Insère l’ID d’interface spécifié par le paramètre de modèle actuel placée dans l’élément de tableau spécifié.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Index de base zéro qui indique l’élément de tableau de départ pour cette opération. Lorsque cette opération se termine, *index* est incrémentée de 1.

*iids*<br/>
Tableau de type IID.

### <a name="remarks"></a>Notes

Fonction d’assistance interne.

## <a name="iidcount"></a>Implements::IidCount

Contient le nombre d’ID d’interface implémentée.

```cpp
static const unsigned long IidCount;
```
