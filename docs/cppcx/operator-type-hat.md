---
title: Type^, opérateur
ms.date: 12/30/2016
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
ms.openlocfilehash: fca53abb9dc17588695591d496b7db2a76e319f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553658"
---
# <a name="operator-type"></a>Type^, opérateur

Permet la conversion de [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) en `Platform::Type`.

## <a name="syntax"></a>Syntaxe

```cpp
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName);
```

### <a name="return-value"></a>Valeur de retour

Retourne `Platform::Type` quand un [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx)est fourni.

### <a name="remarks"></a>Notes

`TypeName` est la structure Windows Runtime indépendante du langage pour représenter les informations de type. [Platform::Type](../cppcx/platform-type-class.md) est spécifique à C++ et ne peut pas être passé à travers l'interface binaire d'application (ABI). Voici une utilisation de `TypeName`dans la fonction [Navigate](https://msdn.microsoft.com/library/windows/apps/hh702394.aspx) :

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