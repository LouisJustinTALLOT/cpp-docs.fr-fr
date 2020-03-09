---
title: Platform::Object, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Object::Object
- VCCORLIB/Platform::Object::Equals
- VCCORLIB/Platform::Object::GetHashCode
- VCCORLIB/Platform::Object::ReferenceEquals
- VCCORLIB/Platform::ToString
- VCCORLIB/Platform::GetType
helpviewer_keywords:
- Object class
ms.assetid: 709e84a8-0bff-471b-bc14-63e424080b5a
ms.openlocfilehash: 77313f8c4dcc87fa9de852afe2d60e614f8fc3a3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865741"
---
# <a name="platformobject-class"></a>Platform::Object, classe

Fournit un comportement commun pour les classes REF et les structs REF dans les applications Windows Runtime. Toute instance de classe ref ou de struct ref est implicitement convertible en objet Platform::Object^ et peut remplacer sa méthode ToString virtuelle.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class Object : Object
```

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[Object :: Object](#ctor)|Initialise une nouvelle instance de la classe Object.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[Object :: est égal à](#equals)|Détermine si l'objet spécifié est égal à l'objet actuel.|
|[Object :: GetHashCode](#gethashcode)|Retourne le code de hachage de cette instance.|
|[Objet :: ReferenceEquals](#referenceequals)|Détermine si les instances Object spécifiées sont identiques.|
|[ToString](#tostring)|Retourne une chaîne qui représente l'objet actif. Peut être substituée.|
|[GetType](#gettype)|Obtient un [Platform::Type](../cppcx/platform-type-class.md) qui décrit l'instance actuelle.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Object`

`Object`

### <a name="requirements"></a>Spécifications

**En-tête :** vccorlib.h

**Espace de noms :** Platform

## <a name="equals"></a>Object :: Equals, méthode

Détermine si l'objet spécifié est égal à l'objet actuel.

### <a name="syntax"></a>Syntaxe

```cpp
bool Equals(
    Object^ obj
)
```

### <a name="parameters"></a>Paramètres

*obj*<br/>
Objet à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si les objets sont égaux, sinon **false**.

## <a name="gethashcode"></a>Object :: GetHashCode, méthode

Retourne la valeur d'identité `IUnknown`* pour cette instance s'il s'agit d'un objet COM ou une valeur de hachage calculée s'il ne s'agit d'un objet COM.

### <a name="syntax"></a>Syntaxe

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Valeur de retour

Une valeur numérique qui identifie de façon unique cet objet.

### <a name="remarks"></a>Notes

Vous pouvez utiliser GetHashCode afin de créer des clés pour les objets des cartes. Vous pouvez comparer des codes de hachage à l’aide de [Object :: Equals](#equals). Si le chemin de code est extrêmement critique et `GetHashCode` et `Equals` ne sont pas suffisamment rapides, vous pouvez alors accéder à la couche COM sous-jacente et effectuer des comparaisons de pointeurs `IUnknown` natifs.

## <a name="gettype"></a>Object :: GetType, méthode

Retourne un objet [Platform :: type](../cppcx/platform-type-class.md) qui décrit le type au moment de l’exécution d’un objet.

### <a name="syntax"></a>Syntaxe

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Objet [Platform :: type](../cppcx/platform-type-class.md) qui décrit le type au moment de l’exécution de l’objet.

### <a name="remarks"></a>Notes

Le [type static :: GetTypeCode](../cppcx/platform-type-class.md#gettypecode) peut être utilisé pour obtenir une valeur d' [énumération Platform :: TypeCode](../cppcx/platform-typecode-enumeration.md) qui représente le type actuel. Ceci est particulièrement utile pour les types intégrés. Le code de type pour toute classe ref en dehors de [Platform :: String](../cppcx/platform-string-class.md) est Object (1).

La classe [Windows :: UI :: XAML :: Interop :: TypeName](/uwp/api/windows.ui.xaml.interop.typename) est utilisée dans les API Windows comme une méthode indépendante du langage pour passer des informations de type entre les composants et les applications Windows. La[classe T Platform :: type](../cppcx/platform-type-class.md) a des opérateurs pour la conversion entre `Type` et `TypeName`.

Utilisez l’opérateur [typeid](../extensions/typeid-cpp-component-extensions.md) pour retourner un objet `Platform::Type` pour un nom de classe, par exemple lors de la navigation entre les pages XAML :

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="ctor"></a>Object :: Object, constructeur

Initialise une nouvelle instance de la classe Object.

### <a name="syntax"></a>Syntaxe

```cpp
public:Object();
```

## <a name="referenceequals"></a>Object :: ReferenceEquals, méthode

Détermine si les instances Object spécifiées sont identiques.

### <a name="syntax"></a>Syntaxe

```cpp
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2);
```

### <a name="parameters"></a>Paramètres

*obj1*<br/>
Premier objet à comparer.

*obj2*<br/>
Deuxième objet à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si les deux objets sont identiques ; Sinon, **false**.

## <a name="tostring"></a>Object :: ToString, méthodeC++(/CX)

Retourne une chaîne qui représente l'objet actif.

### <a name="syntax"></a>Syntaxe

```cpp
public:
virtual String^ ToString();
```

### <a name="return-value"></a>Valeur de retour

Chaîne qui représente l’objet actif. Vous pouvez substituer cette méthode afin de fournir un message personnalisé dans votre classe ou struct ref :

```cpp
public ref class Tree sealed
{
public:
    Tree(){}
    virtual Platform::String^ ToString() override
    {
      return "I’m a Tree";
    };
};
```

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](platform-namespace-c-cx.md)<br/>
[Platform::Type, classe](platform-type-class.md)<br/>
[Système de type](type-system-c-cx.md)
