---
title: Type^, opérateur
ms.date: 12/30/2016
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
ms.openlocfilehash: 180efcac76b7f51291a47ee68508e7444a6c069c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161808"
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

Projet de programmes .NET framework `TypeName` en tant que <xref:System.Type>

### <a name="requirements"></a>Configuration requise

## <a name="see-also"></a>Voir aussi

[Windows::UI::Xaml::Interop::TypeName, opérateur](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform::Type, classe](../cppcx/platform-type-class.md)
