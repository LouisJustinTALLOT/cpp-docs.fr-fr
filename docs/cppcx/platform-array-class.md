---
title: Classe Platform::Array
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Array
- VCCORLIB/Platform::Array::Value
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
ms.openlocfilehash: 4903c18f981c87c418a6ab08595816ce22a7413c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742942"
---
# <a name="platformarray-class"></a>Classe Platform::Array

Représente un tableau unidimensionnel et modifiable qui peut être reçu et passé via l'interface binaire d'application (ABI).

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
private ref class Array<TArg, 1> :
    public WriteOnlyArray<TArg, 1>,
    public IBoxArray<TArg>
```

### <a name="members"></a>Membres

Platform :: Array hérite de toutes ses méthodes de la [classe Platform :: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) et implémente la `Value` propriété de l' [interface Platform :: IBoxArray](../cppcx/platform-iboxarray-interface.md).

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeurs de tableaux](#ctor)|Initialise un tableau unidimensionnel et modifiable de types spécifiés par le paramètre de modèle de classe, *T*.|

### <a name="methods"></a>Méthodes

Consultez la [classe Platform :: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md).

### <a name="properties"></a>Propriétés

| Nom | Description |
|--|--|
| [Array :: value](#value) | Récupère un handle vers le tableau actuel. |

### <a name="remarks"></a>Notes

La classe Array est sealed et ne peut pas être héritée.

Le système de type Windows Runtime ne prend pas en charge le concept de tableaux en escalier et vous ne pouvez donc pas passer un `IVector<Platform::Array<T>>` en tant que valeur de retour ou paramètre de méthode. Pour passer un tableau en escalier ou une séquence de séquences à travers l'ABI, utilisez `IVector<IVector<T>^>`.

Pour plus d’informations sur le moment et la façon d’utiliser Platform :: Array, consultez [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

Cette classe est définie dans l'en-tête vccorlib.h, qui est inclus automatiquement par le compilateur. Elle est visible dans IntelliSense, mais pas dans l’Explorateur d’objets, car il ne s’agit pas d’un type public défini dans Platform. winmd.

### <a name="requirements"></a>Spécifications

Option du compilateur : **/ZW**

## <a name="array-constructors"></a><a name="ctor"></a> Constructeurs de tableau

Initialise un tableau unidimensionnel et modifiable de types spécifiés par le paramètre de modèle de classe, *T*.

### <a name="syntax"></a>Syntaxe

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Paramètre de modèle de classe.

*size*<br/>
Nombre d’éléments dans le tableau.

*data*<br/>
Pointeur vers un tableau de données de type `T` utilisé pour initialiser l'objet Array.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la création d’instances de Platform :: Array, consultez [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="arrayget-method"></a><a name="get"></a> Array :: obten, méthode

Extrait une référence à l'élément de tableau à la position d'index spécifiée.

### <a name="syntax"></a>Syntaxe

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>Paramètres

*index*<br/>
Index de base zéro qui identifie un élément du tableau. L’index minimal est 0 et l’index maximal est la valeur spécifiée par le `size` paramètre dans le [constructeur de tableau](#ctor).

### <a name="return-value"></a>Valeur de retour

Élément de tableau spécifié par le paramètre `index`.

## <a name="arrayvalue-property"></a><a name="value"></a> Array :: value, propriété

Récupère un handle vers le tableau actuel.

### <a name="syntax"></a>Syntaxe

```cpp
property Array^ Value;
```

### <a name="return-value"></a>Valeur de retour

Handle vers le tableau actuel.

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)<br/>
[Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
