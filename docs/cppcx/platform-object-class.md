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
ms.openlocfilehash: 8300ec484bdb58919ce8e450b706dd07c275ceee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363685"
---
# <a name="platformobject-class"></a>Platform::Object, classe

Fournit un comportement courant pour les classes de ref et les structs de ref dans les applications Windows Runtime. Toute instance de classe ref ou de struct ref est implicitement convertible en objet Platform::Object^ et peut remplacer sa méthode ToString virtuelle.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class Object : Object
```

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Object::Object](#ctor)|Initialise une nouvelle instance de la classe Object.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Object::Equals](#equals)|Détermine si l'objet spécifié est égal à l'objet actuel.|
|[Object::GetHashCode](#gethashcode)|Retourne le code de hachage de cette instance.|
|[Object::ReferenceEquals](#referenceequals)|Détermine si les instances Object spécifiées sont identiques.|
|[ToString](#tostring)|Retourne une chaîne qui représente l'objet actif. Peut être substituée.|
|[GetType](#gettype)|Obtient un [Platform::Type](../cppcx/platform-type-class.md) qui décrit l'instance actuelle.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`Object`

`Object`

### <a name="requirements"></a>Spécifications

**En-tête** : vccorlib.h

**Espace de noms :** Platform

## <a name="objectequals-method"></a><a name="equals"></a>Objet::Méthode égale

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

**vrai** si les objets sont égaux, sinon **faux**.

## <a name="objectgethashcode-method"></a><a name="gethashcode"></a>Objet:GetHashCode Méthode

Retourne la valeur d'identité `IUnknown`* pour cette instance s'il s'agit d'un objet COM ou une valeur de hachage calculée s'il ne s'agit d'un objet COM.

### <a name="syntax"></a>Syntaxe

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Valeur de retour

Une valeur numérique qui identifie de façon unique cet objet.

### <a name="remarks"></a>Notes

Vous pouvez utiliser GetHashCode afin de créer des clés pour les objets des cartes. Vous pouvez comparer les codes de hachage en utilisant [Object::Equals](#equals). Si le chemin de code est extrêmement critique et `GetHashCode` et `Equals` ne sont pas suffisamment rapides, vous pouvez alors accéder à la couche COM sous-jacente et effectuer des comparaisons de pointeurs `IUnknown` natifs.

## <a name="objectgettype-method"></a><a name="gettype"></a>Objet::GetType Méthode

Retourne une [plate-forme::Type](../cppcx/platform-type-class.md) objet qui décrit le type de temps d’exécution d’un objet.

### <a name="syntax"></a>Syntaxe

```cpp
Object::GetType();
```

### <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Une [plate-forme::Type](../cppcx/platform-type-class.md) objet qui décrit le type de temps d’exécution de l’objet.

### <a name="remarks"></a>Notes

Le [type statique::GetTypeCode](../cppcx/platform-type-class.md#gettypecode) peut être utilisé pour obtenir une [plate-forme::TypeCode Valeur d’énumération](../cppcx/platform-typecode-enumeration.md) qui représente le type actuel. Ceci est particulièrement utile pour les types intégrés. Le code de type pour n’importe quelle classe d’arbitre en dehors [de la plate-forme : : La corde](../cppcx/platform-string-class.md) est objet (1).

Le [Windows::UI:Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename) classe est utilisé dans les API Windows comme une façon indépendante de la langue de passer des informations de type entre les composants Windows et les applications. La[plate-forme T::Type Class](../cppcx/platform-type-class.md) `Type` a `TypeName`des opérateurs pour la conversion entre et .

Utilisez [l’opérateur typeid](../extensions/typeid-cpp-component-extensions.md) pour retourner un `Platform::Type` objet pour un nom de classe, par exemple lors de la navigation entre les pages XAML:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

## <a name="objectobject-constructor"></a><a name="ctor"></a>Objet::Object Constructor

Initialise une nouvelle instance de la classe Object.

### <a name="syntax"></a>Syntaxe

```cpp
public:Object();
```

## <a name="objectreferenceequals-method"></a><a name="referenceequals"></a>Objet::ReferenceEquals Méthode

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

**vrai** si les deux objets sont les mêmes; autrement, **faux**.

## <a name="objecttostring-method-ccx"></a><a name="tostring"></a>Objet::Méthode ToString (C/CX)

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

[Espace nom de la plate-forme](platform-namespace-c-cx.md)<br/>
[Platform::Type, classe](platform-type-class.md)<br/>
[Système de types](type-system-c-cx.md)
