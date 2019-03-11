---
title: Platform::ArrayReference (classe)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: 923f60e90517e377b99d5e29f38c48b2633c3c46
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742978"
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
|[ArrayReference::ArrayReference](#ctor)|Initialise une nouvelle instance de la classe `ArrayReference`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[ArrayReference::operator(), opérateur](#operator-call)|Convertit cette `ArrayReference` en une `Platform::Array<T>^*`.|
|[ArrayReference::operator=, opérateur](#operator-assign)|Assigne le contenu d'une autre `ArrayReference` à cette instance.|

## <a name="exceptions"></a>Exceptions

### <a name="remarks"></a>Notes

En utilisant un `ArrayReference` pour remplir un tableau de style C, vous évitez l'opération de copie supplémentaire nécessaire en copiant d'abord vers une variable `Platform::Array` , puis dans le tableau de style C. Lorsque vous utilisez une `ArrayReference`, il n'existe qu'une seule opération de copie. Pour obtenir un exemple de code, consultez [Array et WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

### <a name="requirements"></a>Spécifications

**Prise en charge minimale du client :** Windows 8

**Serveur pris en charge minimale :** Windows Server 2012

**Espace de noms :** Plateforme

**En-tête :** vccorlib.h

## <a name="ctor"></a>  Ayreference::arrayreference, constructeur

Initialise une nouvelle instance de la [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) classe.

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

## <a name="operator-assign"></a>  ArrayReference::operator =, opérateur

Assigne l’objet spécifié à l’actuel [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) objet en utilisant la sémantique de déplacement.

### <a name="syntax"></a>Syntaxe

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>Paramètres

*otherArg*<br/>
Objet déplacé vers l'objet `ArrayReference` actif.

### <a name="return-value"></a>Valeur de retour

Référence à un objet de type `ArrayReference`.

### <a name="remarks"></a>Notes

`Platform::ArrayReference` est un modèle de classe C++ standard, et non une classe de référence.

## <a name="operator-call"></a>  Arrayreference::operator opérateur

Convertit en cours [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) de l’objet vers un [Platform::Array](../cppcx/platform-array-class.md) classe.

### <a name="syntax"></a>Syntaxe

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>Valeur de retour

Handle vers l'objet de type `Array<TArg>^`

### <a name="remarks"></a>Notes

[Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) et [Platform::Array](../cppcx/platform-array-class.md) sont des classes de modèles de classe C++ standards, pas ref.

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)
