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
ms.openlocfilehash: 456dbff652c8f1b800308ff757930b425616a83f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781742"
---
# <a name="platformtype-class"></a>Platform::Type (classe)

Contient des informations d'exécution sur un type, en particulier un nom de chaîne et un code de type. Obtenu en appelant [Object::GetType](../cppcx/platform-object-class.md#gettype) sur n’importe quel objet ou à l’aide de la [typeid](../extensions/typeid-cpp-component-extensions.md) opérateur sur un nom de classe ou un struct.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>Notes

La classe `Type` est utile dans les applications qui doivent effectuer un traitement en utilisant une instruction `if` ou `switch` qui crée une branche en fonction du type d'exécution d'un objet. Le code de type qui décrit la catégorie d’un type est récupéré à l’aide de la [Type::GetTypeCode](#gettypecode) fonction membre.

## <a name="public-methods"></a>Méthodes publiques

|||
|-|-|
|[Type::GetTypeCode Method](#gettypecode)|Retourne une valeur [Platform::TypeCode Enumeration](../cppcx/platform-typecode-enumeration.md) pour l'objet.|
|[Type::ToString (méthode)](#tostring)|Retourne le nom du type tel que spécifié dans ses métadonnées.|

## <a name="public-properties"></a>Propriétés publiques

|||
|-|-|
|[Type::FullName](#fullname)|Retourne une [classe Platform::String](../cppcx/platform-string-class.md)^ qui représente le nom complet du type et utilise . (point) comme séparateur, pas :: (double deux-points), par exemple, `MyNamespace.MyClass`.|

## <a name="conversion-operators"></a>Opérateurs de conversion

|||
|-|-|
|[Type^, opérateur](../cppcx/operator-type-hat.md)|Permet de convertir `Windows::UI::Xaml::Interop::TypeName` en `Platform::Type`.|
|[Windows::UI::Xaml::Interop::TypeName, opérateur](../cppcx/operator-windows-ui-xaml-interop-typename.md)|Permet de convertir `Platform::Type` en `Windows::UI::Xaml::Interop::TypeName`.|

### <a name="requirements"></a>Configuration requise

**Prise en charge minimale du client :** Windows 8

**Serveur pris en charge minimale :** Windows Server 2012

**Espace de noms :** Plateforme

**Métadonnées :** platform.winmd

## <a name="fullname"></a> Type::FullName, propriété

Récupère le nom qualifié complet du type actuel sous la forme `Namespace.Type`.

### <a name="syntax"></a>Syntaxe

```cpp
String^ FullName();
```

### <a name="return-value"></a>Valeur de retour

Nom du type.
### <a name="example"></a>Exemple

```

//  namespace is TestApp
MainPage::MainPage()
{
    InitializeComponent();
    Type^ t = this->GetType();
    auto s = t->FullName; // returns "TestApp.MainPage"
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"
}
```

## <a name="gettypecode"></a> Type::GetTypeCode Method

Récupère une catégorie de type numérique de types intégrés.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>Valeur de retour

L’un des valeurs énumérées Platform::TypeCode.

### <a name="remarks"></a>Notes

L’équivalent de la méthode membre GetTypeCode() est la propriété `typeid`.

## <a name="tostring"></a> Type::ToString (méthode)

Récupère un le nom du type.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>Valeur de retour

Un nom de type tel que spécifié dans ses métadonnées.

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)
