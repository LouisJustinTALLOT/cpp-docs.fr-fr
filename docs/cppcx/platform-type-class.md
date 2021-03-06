---
description: 'En savoir plus sur : classe Platform :: type'
title: Platform::Type (classe)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
ms.openlocfilehash: c11e85180dfb3eeeeb6eea88c3bd47b40fa7289b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307897"
---
# <a name="platformtype-class"></a>Platform::Type (classe)

Contient des informations d'exécution sur un type, en particulier un nom de chaîne et un code de type. Obtenu en appelant [Object :: GetType](../cppcx/platform-object-class.md#gettype) sur tout objet ou à l’aide de l’opérateur [typeid](../extensions/typeid-cpp-component-extensions.md) sur un nom de classe ou de struct.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>Notes

La `Type` classe est utile dans les applications qui doivent diriger le traitement à l’aide d’une **`if`** **`switch`** instruction ou qui fait l’objet d’une branche en fonction du type au moment de l’exécution d’un objet. Le code de type qui décrit la catégorie d’un type est récupéré à l’aide de la fonction membre [type :: GetTypeCode](#gettypecode) .

## <a name="public-methods"></a>Méthodes publiques

| Nom | Description |
|--|--|
| [Type::GetTypeCode Method](#gettypecode) | Retourne une valeur [Platform::TypeCode Enumeration](../cppcx/platform-typecode-enumeration.md) pour l'objet. |
| [Type :: ToString, méthode](#tostring) | Retourne le nom du type tel que spécifié dans ses métadonnées. |

## <a name="public-properties"></a>Propriétés publiques

| Nom | Description |
|--|--|
| [Type :: FullName](#fullname) | Retourne une [classe Platform::String](../cppcx/platform-string-class.md)^ qui représente le nom complet du type et utilise . (point) en tant que séparateur, et non :: (double deux-points), par exemple `MyNamespace.MyClass` . |

## <a name="conversion-operators"></a>Opérateurs de conversion

| Nom | Description |
|--|--|
| [Type d’opérateur ^](../cppcx/operator-type-hat.md) | Permet de convertir `Windows::UI::Xaml::Interop::TypeName` en `Platform::Type`. |
| [Windows::UI::Xaml::Interop::TypeName, opérateur](../cppcx/operator-windows-ui-xaml-interop-typename.md) | Permet de convertir `Platform::Type` en `Windows::UI::Xaml::Interop::TypeName`. |

### <a name="requirements"></a>Spécifications

**Client minimal pris en charge :** Windows 8

**Serveur minimal pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** Platform. winmd

## <a name="typefullname-property"></a><a name="fullname"></a> Type :: FullName, propriété

Récupère le nom qualifié complet du type actuel dans le formulaire `Namespace.Type` .

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

## <a name="typegettypecode-method"></a><a name="gettypecode"></a> Type :: GetTypeCode, méthode

Récupère une catégorie de type numérique de types intégrés.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>Valeur de retour

L’un des valeurs énumérées Platform::TypeCode.

### <a name="remarks"></a>Notes

L’équivalent de la méthode membre GetTypeCode () est la **`typeid`** propriété.

## <a name="typetostring-method"></a><a name="tostring"></a> Type :: ToString, méthode

Récupère le nom du type.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>Valeur de retour

Nom du type tel que spécifié dans ses métadonnées.

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)
