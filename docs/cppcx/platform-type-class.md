---
title: Platform::Type (classe)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
ms.openlocfilehash: 7463a2518e6ec5cc84f59db05cfaf60e43eb9fde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322092"
---
# <a name="platformtype-class"></a>Platform::Type (classe)

Contient des informations d'exécution sur un type, en particulier un nom de chaîne et un code de type. Obtenu en appelant [l’objet : : GetType](../cppcx/platform-object-class.md#gettype) sur n’importe quel objet ou en utilisant [l’opérateur typeid](../extensions/typeid-cpp-component-extensions.md) sur une classe ou un nom struct.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>Notes

La classe `Type` est utile dans les applications qui doivent effectuer un traitement en utilisant une instruction `if` ou `switch` qui crée une branche en fonction du type d'exécution d'un objet. Le code de type qui décrit la catégorie d’un type est récupéré en utilisant la fonction de membre [Type::GetTypeCode.](#gettypecode)

## <a name="public-methods"></a>Méthodes publiques

|||
|-|-|
|[Type::GetTypeCode Method](#gettypecode)|Retourne une valeur [Platform::TypeCode Enumeration](../cppcx/platform-typecode-enumeration.md) pour l'objet.|
|[Type::Méthode ToString](#tostring)|Retourne le nom du type tel que spécifié dans ses métadonnées.|

## <a name="public-properties"></a>Propriétés publiques

|||
|-|-|
|[Type::FullName](#fullname)|Retourne une [classe Platform::String](../cppcx/platform-string-class.md)^ qui représente le nom complet du type et utilise . (point) comme séparateur, pas :: (double `MyNamespace.MyClass`colon)—par exemple, .|

## <a name="conversion-operators"></a>Opérateurs de conversion

|||
|-|-|
|[type d’opérateur](../cppcx/operator-type-hat.md)|Permet de convertir `Windows::UI::Xaml::Interop::TypeName` en `Platform::Type`.|
|[Windows::UI::Xaml::Interop::TypeName, opérateur](../cppcx/operator-windows-ui-xaml-interop-typename.md)|Permet de convertir `Platform::Type` en `Windows::UI::Xaml::Interop::TypeName`.|

### <a name="requirements"></a>Spécifications

**Client pris en charge au minimum :** Windows 8

**Serveur pris en charge minimum :** Serveur Windows 2012

**Espace de noms :** Platform

**Métadonnées:** platform.winmd

## <a name="typefullname-property"></a><a name="fullname"></a>Type::FullName Propriété

Récupère le nom entièrement qualifié du type `Namespace.Type`actuel sous la forme .

### <a name="syntax"></a>Syntaxe

```cpp
String^ FullName();
```

### <a name="return-value"></a>Valeur de retour

Nom du type.

### <a name="example"></a>Exemple

```cpp
//  namespace is TestApp
MainPage::MainPage()
{
    InitializeComponent();
    Type^ t = this->GetType();
    auto s = t->FullName; // returns "TestApp.MainPage"
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"
}
```

## <a name="typegettypecode-method"></a><a name="gettypecode"></a>Type::GetTypeCode Méthode

Récupère une catégorie de type numérique de types intégrés.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>Valeur de retour

L’un des valeurs énumérées Platform::TypeCode.

### <a name="remarks"></a>Notes

L’équivalent de la méthode membre GetTypeCode() est la propriété `typeid`.

## <a name="typetostring-method"></a><a name="tostring"></a>Type::Méthode ToString

Récupère un nom du type.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>Valeur de retour

Un nom du type tel que spécifié dans ses métadonnées.

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](../cppcx/platform-namespace-c-cx.md)
