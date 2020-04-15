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
ms.openlocfilehash: d625d80df67a3c8207467ad629afd4c2bf88db18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318657"
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

Plate-forme::Array hérite de toutes ses méthodes de [la plate-forme::WriteOnlyArray Classe](../cppcx/platform-writeonlyarray-class.md) et implémente la `Value` propriété de la [plate-forme::IBoxArray Interface](../cppcx/platform-iboxarray-interface.md).

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeurs de tableaux](#ctor)|Initialise un tableau unidimensionnel et modifiable de types spécifiés par le paramètre du modèle de classe, *T*.|

### <a name="methods"></a>Méthodes

Voir [la plate-forme::WriteOnlyArray Class](../cppcx/platform-writeonlyarray-class.md).

### <a name="properties"></a>Propriétés

|||
|-|-|
|[Array::Valeur](#value)|Récupère un handle vers le tableau actuel.|

### <a name="remarks"></a>Notes

La classe Array est sealed et ne peut pas être héritée.

Le système de type Windows Runtime ne prend pas en charge le concept de tableaux déchiquetés\<et donc vous ne pouvez pas passer une plate-forme IVector<::Array T>> comme une valeur de retour ou un paramètre de méthode. Pour passer un tableau en escalier ou une séquence de séquences à travers l'ABI, utilisez `IVector<IVector<T>^>`.

Pour plus d’informations sur quand et comment utiliser la plate-forme::Array, voir [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

Cette classe est définie dans l'en-tête vccorlib.h, qui est inclus automatiquement par le compilateur. Il est visible dans IntelliSense mais pas dans Object Browser car il n’est pas un type public défini dans platform.winmd.

### <a name="requirements"></a>Spécifications

Option du compilateur : **/ZW**

## <a name="array-constructors"></a><a name="ctor"></a>Constructeurs de panneaux

Initialise un tableau unidimensionnel et modifiable de types spécifiés par le paramètre du modèle de classe, *T*.

## <a name="syntax"></a>Syntaxe

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Paramètre de modèle de classe.

*Taille*<br/>
Nombre d’éléments dans le tableau.

*data*<br/>
Pointeur vers un tableau de données de type `T` utilisé pour initialiser l'objet Array.

### <a name="remarks"></a>Notes

Pour plus d’informations sur la façon de créer des instances de la plate-forme::Array, voir [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="arrayget-method"></a><a name="get"></a>Array::obtenir la méthode

Extrait une référence à l'élément de tableau à la position d'index spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>Paramètres

*index*<br/>
Index de base zéro qui identifie un élément du tableau. L’indice minimum est de 0 et l’indice maximum est la valeur spécifiée par le `size` paramètre dans le constructeur [Array](#ctor).

### <a name="return-value"></a>Valeur de retour

Élément de tableau spécifié par le paramètre `index`.

## <a name="arrayvalue-property"></a><a name="value"></a>Array::Valeur Propriété

Récupère un handle vers le tableau actuel.

## <a name="syntax"></a>Syntaxe

```cpp
property Array^ Value;
```

### <a name="return-value"></a>Valeur de retour

Handle vers le tableau actuel.

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](../cppcx/platform-namespace-c-cx.md)<br/>
[Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
