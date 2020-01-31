---
title: Implements, structure
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
ms.openlocfilehash: 0ce6e9193107cbd0d033d99b257e41004b4343a8
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821855"
---
# <a name="implements-structure"></a>Implements, structure

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

### <a name="parameters"></a>Parameters

*I0*<br/>
ID d’interface avant toute chose. Requise

*I1*<br/>
Premier ID d’interface. (facultatif)

*I2*<br/>
Deuxième ID d’interface. (facultatif)

*I3*<br/>
Troisième ID d’interface. (facultatif)

*I4*<br/>
Quatrième ID d’interface. (facultatif)

*I5*<br/>
Cinquième ID d’interface. (facultatif)

*I6*<br/>
Sixième ID d’interface. (facultatif)

*I7*<br/>
Septième ID d’interface. (facultatif)

*I8*<br/>
Huitième ID d’interface. (facultatif)

*I9*<br/>
Neuvième ID d’interface. (facultatif)

*flags*<br/>
Indicateurs de configuration pour la classe. Une ou plusieurs énumérations [RuntimeClassType](runtimeclasstype-enumeration.md) spécifiées dans une structure [RuntimeClassFlags](runtimeclassflags-structure.md) .

## <a name="remarks"></a>Notes

Dérive de la liste d’interfaces spécifiées et implémente des modèles d’assistance pour `QueryInterface` et `GetIid`.

Chaque *I0* via un paramètre d’interface *i9* doit dériver de `IUnknown`, `IInspectable`ou du modèle [ChainInterfaces](chaininterfaces-structure.md) . Le paramètre *Flags* détermine si la prise en charge est générée pour `IUnknown` ou `IInspectable`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs publics

| Name        | Description                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| Synonyme de `RuntimeClassFlags<WinRt>`. |

### <a name="protected-methods"></a>Méthodes protégées

| Name                                              | Description                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implémente :: CanCastTo,](#cancastto)               | Obtient un pointeur vers l’interface spécifiée.                                                                    |
| [Implémente :: Casttounknown,](#casttounknown)       | Obtient un pointeur vers l’interface de `IUnknown` sous-jacente.                                                        |
| [Implements::FillArrayWithIid](#fillarraywithiid) | Insère l’ID d’interface spécifié par le paramètre de modèle avant toute chose actuel dans l’élément de tableau spécifié. |

### <a name="protected-constants"></a>Constantes protégées

| Name                              | Description                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implements::IidCount](#iidcount) | Contient le nombre d’ID d’interface implémentés. |

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>Configuration requise pour

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="cancastto"></a>Implémente :: CanCastTo,

Obtient un pointeur vers l’interface spécifiée.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parameters

*riid*<br/>
Référence à un ID d’interface.

*ppv*<br/>
En cas de réussite, pointeur vers l’interface spécifiée par *riid*.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, HRESULT qui indique l’erreur, par exemple E_NOINTERFACE.

### <a name="remarks"></a>Notes

Il s’agit d’une fonction d’assistance interne qui effectue une opération QueryInterface.

## <a name="casttounknown"></a>Implémente :: Casttounknown,

Obtient un pointeur vers l’interface de `IUnknown` sous-jacente.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valeur de retour

Cette opération est toujours réussie et retourne le pointeur `IUnknown`.

### <a name="remarks"></a>Notes

Fonction d’assistance interne.

## <a name="fillarraywithiid"></a>Implements::FillArrayWithIid

Insère l’ID d’interface spécifié par le paramètre de modèle avant toute chose actuel dans l’élément de tableau spécifié.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parameters

*index*<br/>
Index de base zéro qui indique l’élément de départ du tableau pour cette opération. Lorsque cette opération est terminée, l' *index* est incrémenté de 1.

*iids*<br/>
Tableau de type IID.

### <a name="remarks"></a>Notes

Fonction d’assistance interne.

## <a name="iidcount"></a>Implements::IidCount

Contient le nombre d’ID d’interface implémentés.

```cpp
static const unsigned long IidCount;
```
