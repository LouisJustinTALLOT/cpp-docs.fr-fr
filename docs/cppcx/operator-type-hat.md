---
description: 'En savoir plus sur : type d’opérateur ^'
title: Type^, opérateur
ms.date: 12/30/2016
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
ms.openlocfilehash: 6258da5f276313d28f56fe470849c929cc057a47
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276801"
---
# <a name="operator-type"></a>Type^, opérateur

Permet la conversion de [Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename) en `Platform::Type`.

## <a name="syntax"></a>Syntaxe

```cpp
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName);
```

### <a name="return-value"></a>Valeur de retour

Retourne `Platform::Type` quand un [Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename)est fourni.

### <a name="remarks"></a>Notes

`TypeName` est la structure Windows Runtime indépendante du langage pour représenter les informations de type. [Platform::Type](../cppcx/platform-type-class.md) est spécifique à C++ et ne peut pas être passé à travers l'interface binaire d'application (ABI). Voici une utilisation de `TypeName`dans la fonction [Navigate](/uwp/api/windows.ui.xaml.controls.frame.navigate) :

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>Exemple

L'exemple suivant montre comment convertir un `TypeName` en `Type`.

```

// Convert from Type to TypeName
TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>Équivalent .NET Framework

.NET Framework le projet `TypeName` de programmes en tant que <xref:System.Type>

### <a name="requirements"></a>Spécifications

## <a name="see-also"></a>Voir aussi

[Windows::UI::Xaml::Interop::TypeName, opérateur](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Classe Platform :: type](../cppcx/platform-type-class.md)
