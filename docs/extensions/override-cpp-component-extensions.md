---
description: 'En savoir plus sur : override (C++/CLI et C++/CX)'
title: remplacement (C++/CLI et C++/CX)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
ms.openlocfilehash: 1be49ac9b9e2d0f2eb3342855a42e9707f883078
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335938"
---
# <a name="override--ccli-and-ccx"></a>remplacement (C++/CLI et C++/CX)

Le mot clé contextuel **override** indique qu’un membre d’un type substitue un membre de la classe de base ou de l’interface de base.

## <a name="remarks"></a>Notes

Le mot clé **override** est valide lors de la compilation de cibles natives (option du compilateur par défaut), de cibles Windows Runtime (option du compilateur `/ZW`), ou de cibles common language runtime (option du compilateur `/clr`).

Pour plus d’informations sur les spécificateurs de substitution, consultez [Spécificateur de substitution](../cpp/override-specifier.md) et [Spécificateurs de substitution et compilations natives](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Pour plus d’informations sur les mots clés contextuels, consultez [Mots clés contextuels](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="examples"></a>Exemples

L’exemple de code suivant montre que **override** peut également être utilisé dans les compilations natives.

```cpp
// override_keyword_1.cpp
// compile with: /c
struct I1 {
   virtual void f();
};

struct X : public I1 {
   virtual void f() override {}
};
```

### <a name="example"></a>Exemple

L’exemple de code suivant montre que **override** peut être utilisé dans les compilations Windows Runtime.

```cpp
// override_keyword_2.cpp
// compile with: /ZW /c
ref struct I1 {
   virtual void f();
};

ref struct X : public I1 {
   virtual void f() override {}
};
```

#### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

### <a name="example"></a>Exemple

L’exemple de code suivant montre que **override** peut être utilisé dans les compilations de common language runtime.

```cpp
// override_keyword_3.cpp
// compile with: /clr /c
ref struct I1 {
   virtual void f();
};

ref struct X : public I1 {
   virtual void f() override {}
};
```

#### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

## <a name="see-also"></a>Voir aussi

[Spécificateur de substitution](../cpp/override-specifier.md)<br/>
[Spécificateurs de substitution](override-specifiers-cpp-component-extensions.md)
