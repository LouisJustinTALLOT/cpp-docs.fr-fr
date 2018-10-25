---
title: Remplacer (C++ / c++ / CLI et c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1d97558dc50adc0bac8758d0821badff14707c04
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056137"
---
# <a name="override--ccli-and-ccx"></a>Remplacer (C++ / c++ / CLI et c++ / CX)

Le **remplacer** mot clé contextuel indique qu’un membre d’un type substitue une classe de base ou d’un membre d’interface de base.

## <a name="remarks"></a>Notes

Le **remplacer** mot clé est valide lors de la compilation pour les cibles natives (option de compilateur par défaut), les cibles Windows Runtime (`/ZW` option du compilateur), ou les cibles de runtime de langage courantes (`/clr` option du compilateur).

Pour plus d’informations sur les spécificateurs de substitution, consultez [spécificateur de substitution](../cpp/override-specifier.md) et [des spécificateurs de substitution et Compilations natives](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Pour plus d’informations sur les mots clés contextuels, consultez [mots clés contextuels](../windows/context-sensitive-keywords-cpp-component-extensions.md).

## <a name="examples"></a>Exemples

L’exemple de code suivant montre que **remplacer** peut également être utilisé dans les compilations natives.

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

L’exemple de code suivant montre que **remplacer** peut être utilisé dans les compilations de Windows Runtime.

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

#### <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

### <a name="example"></a>Exemple

L’exemple de code suivant montre que **remplacer** peut être utilisé dans les compilations de runtime de langage commun.

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

#### <a name="requirements"></a>Configuration requise

Option du compilateur : `/clr`

## <a name="see-also"></a>Voir aussi

[override, spécificateur](../cpp/override-specifier.md)<br/>
[Spécificateurs de substitution](../windows/override-specifiers-cpp-component-extensions.md)