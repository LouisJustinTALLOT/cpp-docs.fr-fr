---
description: 'En savoir plus sur : classe Platform :: ArrayReference'
title: Platform::ArrayReference (classe)
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: 6d883dd369b4b439bd02a337017e8c13731999d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284081"
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference (classe)

`ArrayReference` est un type d'optimisation que vous pouvez remplacer par [Platform::Array^](../cppcx/platform-array-class.md) dans les paramètres d'entrée lorsque vous souhaitez remplir un tableau de style C avec les données d'entrée.

## <a name="syntax"></a>Syntaxe

```cpp
class ArrayReference
```

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[ArrayReference :: ArrayReference](#ctor)|Initialise une nouvelle instance de la classe `ArrayReference`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[ArrayReference :: Operator (), opérateur](#operator-call)|Convertit cette `ArrayReference` en une `Platform::Array<T>^*`.|
|[ArrayReference::operator=, opérateur](#operator-assign)|Assigne le contenu d'une autre `ArrayReference` à cette instance.|

## <a name="exceptions"></a>Exceptions

### <a name="remarks"></a>Remarques

En utilisant un `ArrayReference` pour remplir un tableau de style C, vous évitez l'opération de copie supplémentaire nécessaire en copiant d'abord vers une variable `Platform::Array` , puis dans le tableau de style C. Lorsque vous utilisez une `ArrayReference`, il n'existe qu'une seule opération de copie. Pour obtenir un exemple de code, consultez [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

### <a name="requirements"></a>Spécifications

**Client minimal pris en charge :** Windows 8

**Serveur minimal pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**En-tête** : vccorlib.h

## <a name="arrayreferencearrayreference-constructor"></a><a name="ctor"></a> ArrayReference :: ArrayReference, constructeur

Initialise une nouvelle instance de la classe [Platform :: ArrayReference](../cppcx/platform-arrayreference-class.md) .

### <a name="syntax"></a>Syntaxe

```cpp
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);
ArrayReference(ArrayReference&& otherArg)
```

### <a name="parameters"></a>Paramètres

*dataArg*<br/>
Pointeur vers les données de tableau.

*sizeArg*<br/>
Nombre d'éléments du tableau source.

*otherArg*<br/>
Objet `ArrayReference` dont les données sont déplacées pour initialiser la nouvelle instance.

### <a name="remarks"></a>Notes

## <a name="arrayreferenceoperator-operator"></a><a name="operator-assign"></a> ArrayReference :: Operator =, opérateur

Assigne l’objet spécifié à l’objet [Platform :: ArrayReference](../cppcx/platform-arrayreference-class.md) en cours à l’aide de la sémantique de déplacement.

### <a name="syntax"></a>Syntaxe

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>Paramètres

*otherArg*<br/>
Objet déplacé vers l'objet `ArrayReference` actif.

### <a name="return-value"></a>Valeur renvoyée

Référence à un objet de type `ArrayReference`.

### <a name="remarks"></a>Notes

`Platform::ArrayReference` est un modèle de classe C++ standard, et non une classe de référence.

## <a name="arrayreferenceoperator-operator"></a><a name="operator-call"></a> ArrayReference :: Operator (), opérateur

Convertit l’objet [Platform :: ArrayReference](../cppcx/platform-arrayreference-class.md) actuel en classe [Platform :: Array](../cppcx/platform-array-class.md) .

### <a name="syntax"></a>Syntaxe

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>Valeur de retour

Handle vers l'objet de type `Array<TArg>^`

### <a name="remarks"></a>Notes

[Platform :: ArrayReference](../cppcx/platform-arrayreference-class.md) est un modèle de classe C++ standard, et [Platform :: Array](../cppcx/platform-array-class.md) est une classe ref.

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](../cppcx/platform-namespace-c-cx.md)
