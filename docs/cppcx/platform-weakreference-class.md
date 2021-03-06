---
description: 'En savoir plus sur : Platform :: WeakReference, classe'
title: Platform::WeakReference, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- Platform::WeakReference
ms.assetid: 8cfe1977-a8c7-4b7b-b539-25c77ed4c5f1
ms.openlocfilehash: edf3220d8916ff4bdb1462f3dd04149a4e9a9709
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307793"
---
# <a name="platformweakreference-class"></a>Platform::WeakReference, classe

Représente une référence faible à une instance d'une classe ref.

## <a name="syntax"></a>Syntaxe

```cpp
class WeakReference
```

#### <a name="parameters"></a>Paramètres

### <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Membre|Description|
|------------|-----------------|
|[WeakReference :: WeakReference](#ctor)|Initialise une nouvelle instance de la classe WeakReference.|

### <a name="methods"></a>Méthodes

|Membre|Description|
|------------|-----------------|
|[WeakReference :: Resolve](#resolve)|Retourne un handle vers la classe ref sous-jacente, ou nullptr si l'objet n'existe plus.|

### <a name="operators"></a>Opérateurs

|Membre|Description|
|------------|-----------------|
|[WeakReference::operator=](#operator-assign)|Assigne une nouvelle valeur à l'objet WeakReference.|
|[WeakReference::operator BoolType](#booltype)|Implémente le modèle de valeur booléenne sécurisé.|

### <a name="remarks"></a>Notes

La classe WeakReference elle-même n'est pas une classe ref et par conséquent elle n'hérite pas de Platform::Object^ et ne peut pas être utilisée dans la signature d'une méthode publique.

## <a name="weakreferenceoperator"></a><a name="operator-assign"></a> WeakReference :: Operator =

Assigne une valeur à un WeakReference.

### <a name="syntax"></a>Syntaxe

```cpp
WeakReference& operator=(decltype(__nullptr));
WeakReference& operator=(const WeakReference& otherArg);
WeakReference& operator=(WeakReference&& otherArg);
WeakReference& operator=(const volatile ::Platform::Object^ const otherArg);
```

### <a name="remarks"></a>Notes

La dernière surcharge de la liste ci-dessus vous permet d'assigner une classe ref à une variable WeakReference. Dans ce cas, la classe ref est castée vers [Platform :: Object](../cppcx/platform-object-class.md)^. Vous restaurez le type d’origine ultérieurement en le spécifiant comme argument pour le paramètre de type dans la fonction membre [WeakReference :: Resolve \<T> ](#resolve) .

## <a name="weakreferenceoperator-booltype"></a><a name="booltype"></a> WeakReference :: Operator Booltype,

Implémente le modèle booléen sécurisé pour la classe WeakReference. À ne pas appeler explicitement à partir de votre code.

### <a name="syntax"></a>Syntaxe

```cpp
BoolType BoolType();
```

## <a name="weakreferenceresolve-method-platform-namespace"></a><a name="resolve"></a> WeakReference :: Resolve, méthode (espace de noms Platform)

Retourne un handle vers la classe ref d’origine, ou **`nullptr`** si l’objet n’existe plus.

### <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
T^ Resolve() const;
```

### <a name="parameters"></a>Paramètres

### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Handle vers la classe ref à laquelle l'objet WeakReference était associé précédemment ou nullptr.

### <a name="example"></a>Exemple

```cpp
Bar^ bar = ref new Bar();
//use bar...

if (bar != nullptr)
{
    WeakReference wr(bar);
    Bar^ newReference = wr.Resolve<Bar>();
}
```

Notez que le paramètre de type est T au lieu de T^.

## <a name="weakreferenceweakreference-constructor"></a><a name="ctor"></a> WeakReference :: WeakReference, constructeur

Fournit différentes façons de construire un WeakReference.

### <a name="syntax"></a>Syntaxe

```cpp
WeakReference();
WeakReference(decltype(__nullptr));
WeakReference(const WeakReference& otherArg);
WeakReference(WeakReference&& otherArg);
explicit WeakReference(const volatile ::Platform::Object^ const otherArg);
```

### <a name="example"></a>Exemple

```cpp
MyClass^ mc = ref new MyClass();
WeakReference wr(mc);
MyClass^ copy2 = wr.Resolve<MyClass>();
```

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)
