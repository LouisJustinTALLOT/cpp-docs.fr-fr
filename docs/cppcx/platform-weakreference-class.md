---
title: Platform::WeakReference, classe | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- Platform::WeakReference
ms.assetid: 8cfe1977-a8c7-4b7b-b539-25c77ed4c5f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d411269794e3588f1273844d54f7d5d5f4dbdf88
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107066"
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
|[WeakReference::WeakReference](#ctor)|Initialise une nouvelle instance de la classe WeakReference.|

### <a name="methods"></a>Méthodes

|Membre|Description|
|------------|-----------------|
|[WeakReference::Resolve](#resolve)|Retourne un handle vers la classe ref sous-jacente, ou nullptr si l'objet n'existe plus.|

### <a name="operators"></a>Opérateurs

|Membre|Description|
|------------|-----------------|
|[WeakReference::operator=](#operator-assign)|Assigne une nouvelle valeur à l'objet WeakReference.|
|[WeakReference::operator BoolType](#booltype)|Implémente le modèle booléen sécurisé.|

### <a name="remarks"></a>Notes

La classe WeakReference elle-même n'est pas une classe ref et par conséquent elle n'hérite pas de Platform::Object^ et ne peut pas être utilisée dans la signature d'une méthode publique.

## <a name="operator-assign"></a> WeakReference::operator =

Assigne une valeur à un WeakReference.

### <a name="syntax"></a>Syntaxe

```cpp
WeakReference& operator=(decltype(__nullptr));
WeakReference& operator=(const WeakReference& otherArg);
WeakReference& operator=(WeakReference&& otherArg);
WeakReference& operator=(const volatile ::Platform::Object^ const otherArg);
```

### <a name="remarks"></a>Notes

La dernière surcharge de la liste ci-dessus vous permet d'assigner une classe ref à une variable WeakReference. Dans ce cas, la classe ref est castée en aval en [Platform::Object](../cppcx/platform-object-class.md)^. Vous restaurez ultérieurement le type d’origine en le spécifiant comme argument pour le paramètre de type dans le [WeakReference::Resolve\<T >](#resolve) fonction membre.

## <a name="booltype"></a> WeakReference::operator BoolType

Implémente le modèle booléen sécurisé pour la classe WeakReference. À ne pas appeler explicitement à partir de votre code.

### <a name="syntax"></a>Syntaxe

```cpp
BoolType BoolType();
```

## <a name="resolve"></a> WeakReference::Resolve, méthode (espace de noms Platform)

Retourne un handle vers la classe ref d'origine ou `nullptr` si l'objet n'existe plus.

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

## <a name="ctor"></a> WeakReference::WeakReference, constructeur

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