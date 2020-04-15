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
ms.openlocfilehash: 223f37d7cabbd0b8cd238582773c05d7b9eaabf6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371408"
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
L’ID d’interface zéro. (obligatoire)

*I1 (en)*<br/>
La première interface ID. (facultatif)

*I2 (en)*<br/>
La deuxième interface ID. (facultatif)

*I3 (en)*<br/>
La troisième interface ID. (facultatif)

*I4 (en)*<br/>
La quatrième interface ID. (facultatif)

*I5 (en)*<br/>
La cinquième interface ID. (facultatif)

*I6 (en)*<br/>
La sixième interface ID. (facultatif)

*I7 (en)*<br/>
La septième interface ID. (facultatif)

*I8 (en)*<br/>
La huitième interface ID. (facultatif)

*I9 (en)*<br/>
La neuvième interface ID. (facultatif)

*Drapeaux*<br/>
Drapeaux de configuration pour la classe. Un ou plusieurs recensements [RuntimeClassType](runtimeclasstype-enumeration.md) qui sont spécifiés dans une structure [RuntimeClassFlags.](runtimeclassflags-structure.md)

## <a name="remarks"></a>Notes

Dérive de la liste des interfaces spécifiées et `QueryInterface` `GetIid`implémente des modèles d’aide pour et .

Chaque *paramètre d’interface I0* `IUnknown`via `IInspectable` *I9* doit dériver de l’un ou l’autre, ou le modèle [ChainInterfaces.](chaininterfaces-structure.md) Le paramètre *des drapeaux* détermine `IUnknown` `IInspectable`si le support est généré pour ou .

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

| Nom        | Description                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| Synonyme de `RuntimeClassFlags<WinRt>`. |

### <a name="protected-methods"></a>Méthodes protégées

| Nom                                              | Description                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implémente::CanCastTo](#cancastto)               | Obtient un pointeur à l’interface spécifiée.                                                                    |
| [Outils::CastToUnknown](#casttounknown)       | Obtient un pointeur `IUnknown` à l’interface sous-jacente.                                                        |
| [Outils::FillArrayWithIid](#fillarraywithiid) | Insère l’id d’interface spécifié par le paramètre de modèle zéro actuel dans l’élément de tableau spécifié. |

### <a name="protected-constants"></a>Constants protégés

| Nom                              | Description                                    |
| --------------------------------- | ---------------------------------------------- |
| [Outils::IidCount](#iidcount) | Détient le nombre d’interfaces implémentées. |

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>Spécifications

**En-tête:** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="implementscancastto"></a><a name="cancastto"></a>Implémente::CanCastTo

Obtient un pointeur à l’interface spécifiée.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
Une référence à une interface ID.

*Ppv*<br/>
En cas de succès, un pointeur à l’interface spécifiée par *riid*.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; autrement, un HRESULT qui indique l’erreur, comme E_NOINTERFACE.

### <a name="remarks"></a>Notes

Il s’agit d’une fonction d’aide interne qui effectue une opération QueryInterface.

## <a name="implementscasttounknown"></a><a name="casttounknown"></a>Outils::CastToUnknown

Obtient un pointeur `IUnknown` à l’interface sous-jacente.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Valeur de retour

Cette opération réussit toujours `IUnknown` et renvoie le pointeur.

### <a name="remarks"></a>Notes

Fonction d’aide interne.

## <a name="implementsfillarraywithiid"></a><a name="fillarraywithiid"></a>Outils::FillArrayWithIid

Insère l’id d’interface spécifié par le paramètre de modèle zéro actuel dans l’élément de tableau spécifié.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Paramètres

*index*<br/>
Un index à base nulle qui indique l’élément de tableau de départ de cette opération. Lorsque cette opération se termine, *l’indice* est incrémenté par 1.

*iids*<br/>
Un tableau de type IID.

### <a name="remarks"></a>Notes

Fonction d’aide interne.

## <a name="implementsiidcount"></a><a name="iidcount"></a>Outils::IidCount

Détient le nombre d’interfaces implémentées.

```cpp
static const unsigned long IidCount;
```
